# Enumeración de servicios comunes y gestores de contenido

21-FTP

HYDRA

22-SSH

HYDRA

80-HTTP

Gobuster, wfuff, fuff, whatweb, diresearch

443-HTTPS

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

SMB

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
// crackmapexec 
poetry run crackmapexec smb IP 
poetry run crackmapexec smb IP --shares
```

Wordpress

```
// wpscan
// wpscan -e parametro --> parametro para decir si buscar usuarios,plugins,etc.
// con el api token, que se consigue creando una cuenta en wpscan nos ofrece un escaneo mas completo
```

