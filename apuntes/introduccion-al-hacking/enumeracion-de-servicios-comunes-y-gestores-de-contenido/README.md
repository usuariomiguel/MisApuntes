# Enumeración de servicios comunes y gestores de contenido

### Servicios

{% tabs %}
{% tab title="FTP" %}

{% endtab %}

{% tab title="SSH" %}

{% endtab %}

{% tab title="HTTP" %}
* &#x20;Gobuster
* wfuff
* fuff
* whatweb
* dirsearch
{% endtab %}

{% tab title="HTTPS" %}
```
// openssl
openssl s_client -connect google.com:443
```

<pre><code><strong>// sslyze
</strong><strong>sslyze google.com
</strong></code></pre>

```
// sslscan
sslscan google.com
```
{% endtab %}

{% tab title="SMB" %}
```
// smbclient
smbclient -L IP -N //lista carpeta
smbclient //IP/carpeta -N  //te conectas
//para instalar en tu maquina y usar comandos tuyos
apt install cifs-utils
mkdir /mnt/nueva
mount -t cifs //IP/carpeta /mnt/nueva
// smbmap 
smb -H IP // igual que comando de smbclient pero sacar los permisos
smb -H IP -u USUARIO -p CONTRASEÑA
// crackmapexec 
poetry run crackmapexec smb IP 
poetry run crackmapexec smb IP --shares
crackmapexec smb IP -u {wordlist} -p {password} //fuerza bruta usuarios
```
{% endtab %}
{% endtabs %}

### Gestores de Contenido

{% tabs %}
{% tab title="Wordpress" %}
```
// wpscan --url URL
// wpscan --url URL -e parametro --> parametro para decir si buscar usuarios,plugins,etc.
// wpscan --url URL --passwords WORDLIST --> Fuerza bruta a los usuarios
// con el api token, que se consigue creando una cuenta en wpscan nos ofrece un escaneo mas completo
```
{% endtab %}

{% tab title="Joomla" %}
```
// JoomScan

git clone https://github.com/rezasp/joomscan.git
cd joomscan
perl joomscan.pl

// Usage
Do default checks...
perl joomscan.pl --url www.example.com
// or
perl joomscan.pl -u www.example.com
```
{% endtab %}

{% tab title="Drupal" %}
Droopescan

{% embed url="https://github.com/SamJoan/droopescan" %}

```
// git clone
python3 setup.py install 
pìp install -r requirements.txt
droopscan scan drupal --url http://IP:port
```
{% endtab %}

{% tab title="Magento" %}


{% embed url="https://github.com/steverobbins/magescan" %}
{% endtab %}
{% endtabs %}
