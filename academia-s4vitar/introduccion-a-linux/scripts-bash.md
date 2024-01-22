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

