# Permisos especiales – SUID y SGID

* Permisos SGID, SUID y Sticky Bit: [Permisos SGID, SUID y Sticky Bit](https://deephacking.tech/permisos-sgid-suid-y-sticky-bit-linux/)
* Permisos especiales en Linux: [Permisos especiales en Linux – Sticky Bit, SUID y SGID](https://www.ochobitshacenunbyte.com/2019/06/17/permisos-especiales-en-linux-sticky-bit-suid-y-sgid/)
* Los bits SUID, SGID y Sticky: [Los bits SUID, SGID y Sticky](https://www.ibiblio.org/pub/linux/docs/LuCaS/Manuales-LuCAS/SEGUNIX/unixsec-2.1-html/node56.html)



**SUID:** Tienes permisos de usuario root aun no siendo root&#x20;

**SGID:** Tienes permisos de grupo root aun no siendo root&#x20;

Asignar privilegio SUID

```
chmod u+s fichero
chmod 4000 fichero 
```

Buscar archivos con SUID&#x20;

```
find / -type -f -perm -4000 2>/dev/null 
```

Asignar privilegio SGID

```
chmod g+s fichero
chmod 2000 fichero 
```

Buscar archivos con SUID&#x20;

```
find / -type -f -perm -2000 2>/dev/null 
```
