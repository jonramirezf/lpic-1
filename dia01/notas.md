# Día 01 - /dev y discos (enfocado en sda)

/dev/sda — Disco principal
Qué entendí

El disco principal del sistema es /dev/sda.
Este disco está dividido en particiones, y cada partición puede cumplir una función específica dentro del sistema.

En mi caso:

/dev/sda2 contiene /boot (archivos de arranque)
/dev/sda3 contiene el sistema (/) y también los usuarios (/home)

Esto significa que el sistema operativo y los archivos de usuario están en la misma partición.

Cómo lo vi

Usé los siguientes comandos:

lsblk

Muestra la estructura del disco, particiones y puntos de montaje.

sudo fdisk -l

Muestra información más detallada como tipo de tabla (GPT), tamaños y sectores.

Columnas aprendidas en lsblk
NAME: nombre del dispositivo
SIZE: tamaño
TYPE: tipo (disk o part)
MOUNTPOINT: dónde está conectado
RM: removible (0 no, 1 sí)
RO: solo lectura (0 no, 1 sí)
Mountpoints (clave)

Linux no usa letras como Windows (C:, D:).
En su lugar usa carpetas dentro del sistema.

Ejemplos:

/ sistema principal
/home archivos de usuarios
/boot arranque

Estas carpetas son puntos de montaje, es decir, lugares donde se conecta una partición.

Idea importante

Un disco físico se divide en particiones (parte lógica).
Luego esas particiones se conectan al sistema mediante carpetas.

Conclusión

Linux organiza todo dentro de un solo árbol que parte en /.
Los discos no se ven como unidades separadas, sino como partes conectadas al sistema mediante mountpoints.