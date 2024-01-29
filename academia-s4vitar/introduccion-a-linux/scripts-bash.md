# Scripts Bash

1. Script bash con menu con opciones programadas

```
#!/bin/bash

#Colours
greenColour="\e[0;32m\033[1m"
endColour="\033[0m\e[0m"
redColour="\e[0;31m\033[1m"
blueColour="\e[0;34m\033[1m"
yellowColour="\e[0;33m\033[1m"
purpleColour="\e[0;35m\033[1m"
turquoiseColour="\e[0;36m\033[1m"
grayColour="\e[0;37m\033[1m"

function Ctrl_c(){
        echo -e "\n\n${redColour}[!] Saliendo...${endColour}\n"
        tput cnorm && exit 1
}
# Ctrl+C
trap Ctrl_c INT

# Variables globales
main_url="https://htbmachines.github.io/bundle.js"


function helpPanel(){
        echo -e "\n[+] Uso:"
        echo -e "\t${purpleColour}u)${endColour}${grayColour}Descargar o acutaliza archivos necesarios${endColour}"
        echo -e "\t${purpleColour}m)${endColour}${grayColour}Buscar por un nombre de maquina${endColour}"
        echo -e "\t${purpleColour}i)${endColour}${grayColour}Buscar por direccion IP${endColour}"
        echo -e "\t${purpleColour}h)${endColour}${grayColour}Mostar un panel de ayuda${endColour}\n"

}

function searchMachine(){
        machineName="$1"
        echo -e "\n [+] Listando las propiedades de la maquina $machineName \n"
        cat bundle.js | awk "/name: \"$machineName\"/,/resuelta:/" | grep -vE "id:|sku:|resuelta" | tr -d '"' | tr -d ',' | sed 's/^ *//'
}

function searchIP(){
        ipAddress="$1"
        cat bundle.js | grep 'ip: \"$ipAddress\"' -B 3 | grep "name: " | awk 'NF{print $NF}' | tr -d ',' | tr -d '"'
        machineName="$(cat bundle.js | grep "ip: \"$ipAddress\"" -B 3 | grep "name: " | awk 'NF{print $NF}' | tr -d ',' | tr -d '"')"
        echo -e "\n [+] La maquina correspondiente a la IP $ipAddress es $machineName \n"
}

function updateFiles(){

        if [ ! -f bundle.js ]; then
                tput civis
                echo -e "\n${yellowColour}[+]${endColour}${grayColour} Descargando archivos necesarios...${endColour}"
                curl -s $main_url > bundle.js
                js-beautify bundle.js | sponge bundle.js
                echo -e "\n${yellowColor}[+]${endColour}${grayColour} Todos los archivos han sido descargados.${endColour}"
                tput cnorm
        else
                tput civis
                echo -e "\n${yellowColour}[+]${endColour}${grayColour} COmprobando si hay actualizaciones pendientes...${endColour}"
                curl -s $main_url > bundle_temp.js
                js-beautify bundle_temp.js | sponge bundle_temp.js
                md5_temp_value=$(md5sum bundle_temp.js | awk '{print $1}')
                md5_original_value=$(md5sum bundle.js | awk '{print $1}')

                if [ "$md5_temp_value" == "$md5_original_value" ]; then
                        echo -e "\n${yellowColour}[+]${endColour}${grayColour} No se han detectado actualizaciones.${endColour}"
                        rm bundle_temp.js
                else
                        echo -e "\n${yellowColour}[+]${endColour}${grayColour} Se han encontrado actualizaciones disponibles.${endColour}"
                        rm bundle.js && mv bundle_temp.js bundle.js
                        echo -e "\n${yellowColour}[+]${endColour}${grayColour} Los archivos han sido actualizados correctamente.${endColour}"
                fi

                tput cnorm
        fi
}

function skills(){
        skillMachines="$1"
        echo -e "La maquina/s de la skill selecionada [$skillMachines] :\n"
        cat bundle.js | grep "skills: " -B 6 | grep "$skillMachines" -i -B 6 | grep "name: " | awk NF{'print $NF'} | tr -d '"' | tr -d "," | tr -d "(" | column
}

# Indicadores
declare -i parameter_counter=0

while getopts "m:ui:s:h" arg; do
        case $arg in
                m) machineName=$OPTARG; let parameter_counter+=1;;
                u) let parameter_counter+=2;;
                i) ipAddress=$OPTARG; let parameter_counter+=3;;
                s) skillMachines=$OPTARG; let parameter_counter+=4;;
                h) ;;
        esac
done

if [ $parameter_counter -eq 1 ]; then
        searchMachine $machineName
elif [ $parameter_counter -eq 2 ]; then
        updateFiles
elif [ $parameter_counter -eq 3 ]; then
        searchIP $ipAddress
elif [ $parameter_counter -eq 4 ]; then 
        skills "$skillMachines"
else
        helpPanel
fi
```

2. Script Ruleta con opcion a jugar con la tecnica Martingala y InverseLabroucher

```
#!/bin/bash

#Colours
greenColour="\e[0;32m\033[1m"
endColour="\033[0m\e[0m"
redColour="\e[0;31m\033[1m"
blueColour="\e[0;34m\033[1m"
yellowColour="\e[0;33m\033[1m"
purpleColour="\e[0;35m\033[1m"
turquoiseColour="\e[0;36m\033[1m"
grayColour="\e[0;37m\033[1m"

function ctrl_c(){
	echo -e "\n\n [!] Saliendo...\n"
       	exit 1
}
#Ctrl+C
trap ctrl_c INT

function helpPanel(){
	echo -e "\n ${yellowColour}[!]${endColour} Uso: \n"
	echo -e "\t-m) Dinero con el que se desea jugar"
	echo -e "\t-t) Tecnica con la que se desea jugar {martingala | inverseLabrouchete}"
	exit 1
}

function martingala(){
	echo -e "\n Dinero actual: $money€\n"
	echo -n "[+] ¿Cuanto dinero tienes pensado apostar? -> " && read initial_bet
	echo -n "[+] ¿A que deseas apostar continuamente (par/impar)? -> " && read par_impar

	# echo -e "\nVamos a jugar con una cantidad de ${yellowColour}$initial_bet${endColour} al ${greenColour}$par_impar${endColour}"

	backup_bet=$initial_bet
	play_counter=1
	jugadas_malas=""
	let DineroX=0
	while true; do
		money=$(($money-$initial_bet))
		# echo -e "\nAcabas de apostar ${yellowColour}$initial_bet€${endColour} y tienes ${yellowColour}$money€${endColour}\n"
		random_number="$(($RANDOM % 37))"		
		# sleep 1
		if [ ! "$money" -lt 0 ]; then
			if [ "$par_impar" == "par" ]; then
				# Cuando queremos par
				if [ "$(($random_number % 2))" -eq 0 ]; then
					if [ "$random_number" -eq 0 ]; then 
						# echo -e "${redColour}Pierdes! Numero: 0${endColour}"
						initial_bet=$(($initial_bet*2))
						# echo -e "Ahora mismo tienes $money€"
						jugadas_malas+="$random_number "
					
					else
						# echo -e "[+] ${greenColour}Ganas! Numero PAR: ${endColour} $random_number"
						reward=$(($initial_bet*2))
						# echo -e "[+] Ganas un total de ${yellowColour}$reward€ ${endColour}"
						money=$(($money+$reward))
						# echo -e "[+] Tienes un saldo de ${yellowColour}$money€${endColour}\n"
						DineroX=$money
						initial_bet=$backup_bet
						jugadas_malas=""
					fi
				else 				
					# echo -e "[+] ${redColour}Pierdes !Numero impar: ${endColour} $random_number "
					initial_bet=$(($initial_bet*2))
					# echo -e "pierdes un total de $initial_bet"
					# echo -e "Ahora mismo tienes $money€"
					jugadas_malas+="$random_number "
				fi
				# sleep 2
			else 
				# Cuando queremos impar
				if [ "$(($random_number % 2))" -eq 1 ]; then			
					# echo -e "[+] ${greenColour}Ganas! Numero PAR: ${endColour} $random_number"
					reward=$(($initial_bet*2))
					# echo -e "[+] Ganas un total de ${yellowColour}$reward€ ${endColour}"
					money=$(($money+$reward))
					# echo -e "[+] Tienes un saldo de ${yellowColour}$money€${endColour}\n"
					DineroX=$money
					initial_bet=$backup_bet
					jugadas_malas=""
				else
					initial_bet=$(($initial_bet*2))
					jugadas_malas+="$random_number "
				fi
				# sleep 2
			fi
		else
			echo -e "\n${redColour}[!] Te has quedado sin dinero guapet@n${endColour}\n---------------------"
			echo -e "${yellowColour}[+] ${endColour}Han habido un total de ${yellowColour}$((play_counter-1)) ${endColour}jugadas"
			echo -e "${yellowColour}[+]${endColour} Tu mayor ganancia ha sido ${yellowColour}$DineroX€${endColour}"
			echo -e "${yellowColour}[+]${endColour} A continuación se van a representar las malas jugadas consecutivas que han salido:\n"
			echo -e "${blueColour}[ $jugadas_malas]${endColour}"
			exit 0
		fi
		let play_counter+=1
	done
	tput cnorm #recuperamos cursor
}

function inverseLabrouchere (){
	echo -e "\n[+] Dinero actual: $money€"
	echo -ne "[+] ¿A que deseas apostar continuamente (par/impar)? -> " && read par_impar

	declare -a my_sequence=(1 2 3 4)

	echo -e "\n${yellowColour}[+]${endColour} Comenzamos con la secuencia ${greenColour}${endColour}"
	
	bet=$((${my_sequence[0]} + ${my_sequence[-1]}))	

	jugadas_totales=0
	bet_to_renew=$(($money+50)) #Dinero el caul una vez alcanzado hará que renovemos nuestra sequencia a (1 2 3 4)
	echo -e "${yellowColour}[+]${endColour} El tope para renovar la secuencia está establecido por encima de los $bet_to_renew€"
	sleep 5
	tput civis
	while true; do
		let jugadas_totales+=1
		random_number=$((RANDOM % 37))
		money=$(($money - $bet))	
		if [ ! "$money" -lt 0 ]; then
			echo -e "${yellowColour}[+]${endColour} Invertimos $bet"
			echo -e "${yellowColour}[+]${endColour} Tenemos ${yellowColour}$money€${endColour}"
			echo -e "\n${yellowColour}[+]${endColour} Ha salido el numero ${blueColour}$random_number${endColour}"

			if [ "$par_impar" == "par" ]; then
				if [ "$(($random_number % 2))" -eq 0 ] && [ "$random_number" -ne 0 ]; then
					echo -e "${greenColour}[+] Es par, ¡GANAS!${endColour}"
					reward=$(($bet*2))
					let money+=$reward
					echo -e "${yellowColour}[+]${endColour} Tienes ${yellowColour}$money€${endColour}"
					
					if [ $money -gt $bet_to_renew ]; then
						echo "${yellowColour}[+]${endColour} Se ha superado el tope establecido de $bet_to_renew€ para restablecer nuestra sequencia"
						bet_to_renew=$(($bet_to_renew + 50))
						echo -e "[+] El tope se ha establecido en $bet_to_renew€"
						my_sequence=(1 2 3 4)
						bet=$((${my_sequence[0]} + ${my_sequence[-1]}))

						echo -e "Nuestra nueva sequencia es [${my_sequence[@]}]"
					elif [ $money -lt $(($bet_to_renew - 100)) ]; then
						echo -e "[+] El dinero ha alcanzado el minimo, reajustamos tope"
						bet_to_renew=$(($bet_to_renew - 50))
						echo -e "[+] El tope a sido renovado a $bet_to_renew€"
						my_sequence+=($bet)
						my_sequence=(${my_sequence[@]})
						if [ "${#my_sequence[@]}" -ne 1 ] && [ "${#my_sequence[@]}" -ne 0 ]; then
							bet=$((${my_sequence[0]} + ${my_sequence[-1]}))
						elif [ "${#my_sequence[@]}" -eq 1 ]; then
							bet=${my_sequence[0]}
						fi
					else
						my_sequence+=($bet)
						my_sequence=(${my_sequence[@]})
						if [ "${#my_sequence[@]}" -ne 1 ] && [ "${#my_sequence[@]}" -ne 0 ]; then
							bet=$((${my_sequence[0]} + ${my_sequence[-1]}))
						elif [ "${#my_sequence[@]}" -eq 1 ]; then
							bet=${my_sequence[0]}
					
						fi
					fi
					
				elif [ "$((random_number % 2))" -eq 1 ] || [ "$random_number" -eq 0 ]; then
					if [ "$((random_number % 2))" -eq 1 ]; then
						echo -e "${redColour}[!] El numero es impar, ¡PIERDES!${endColour}"
					else
						echo -e "${redColour}[!] El numero es 0, ¡PIERDES!${endColour}"
					fi
					
					unset my_sequence[0]
					unset my_sequence[-1] 2>/dev/null
					
					my_sequence=(${my_sequence[@]})
					
					echo -e "${yellowColour}[+]${endColour} La sequencia se nos queda de la siguiente forma: [${my_sequence[@]}]\n"				
					if [ "${#my_sequence[@]}" -ne 1 ] && [ "${#my_sequence[@]}" -ne 0 ]; then
						bet=$((${my_sequence[0]} + ${my_sequence[-1]}))
					elif [ "${#my_sequence[@]}" -eq 1 ]; then
						bet=${my_sequence[0]}
					else
						echo -e "${redColour}[!] Nuestra sequencia ha terminado${endColour}"
						my_sequence=(1 2 3 4)
						echo -e "${yellowColour}[+]${endColour} Restablecemos la sequencia a [${my_sequence[@]}]\n"
						bet=$((${my_sequence[0]} + ${my_sequence[-1]}))
					fi
				fi
			fi
		else			
			echo -e "\n${redColour}[!] Te has quedado sin dinero guapet@n${endColour}\n---------------------"		
			echo -e "${yellowColour}[+]${endColour} Jugadas totales: ${yellowColour}$jugadas_totales${endColour}"
			exit 0
		fi
	done
	tput cnorm
}

while getopts "m:t:h" arg; do
	case $arg in
		m) money=$OPTARG;;
		t) technique=$OPTARG;;
		h) helpPanel;;
	esac
done

if [ $money ] && [ $technique ]; then
	if [ "$technique" == "martingala" ]; then
		martingala
	elif [ "$technique" == "inverseLabrouchere" ]; then
		inverseLabrouchere
	else
		echo -e "\n ${redColour}[!] La tecnica introducida no existe${endColour}"
		helpPanel
	fi
else
	helpPanel
fi
```
