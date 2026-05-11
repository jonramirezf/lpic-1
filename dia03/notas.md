Filesystem: 
Es la manera que linux administra y organiza los datos dentro de un disco.
idea:
Un disco sin filesystem es solo: espacio bruto, Bits,sectores,boques, pero no sabe donde empieza un archivo, donde termina
que nombre tiene, que permisos tiene.

El filesystem crea orden organiza: Archivos,Carpetas,Permisos,Bloques,nombres y espacio libre.

Analogía disco sin filesystem: terreno Vacio No hay calles, casas o direcciones.
disco  con ext4:como una ciudas organizada ahora si existen calles , casas o direcciones (linux puede guardar archivos,encontrarlos borrar cosas) 

Entonces que es un Filesystem?
Son distintos sistemas/formas de organizar datos en el disco 
cada uno tiene: ventajas, velocidad, compatibilidad

Filesystem importantes:

ext2: extended filesystem 2 
Antiguo, simple , sin journaling 

ext3: ext2+journaling : Mas seguro frente apagados fuertes

ext4:Versión moderna y más usada: Rapida, eficiente y estable 

xfs:Muy usado servidores , RedHat,Fedora (Archivos grandes, rendimiento)

vfat:usa mucho para usb , efi partitions compatible con windows,pendrive,camaras.

swap: Se usa como memoria virtual cuando falta ram 

ext : 
Extended filesystem
Una familia de filesystem creada para linux  
------------------------------------------------------------------------------------------------------------
Comandos nuevos usado: blkid
** blkid
blkid = block id
Sirve para consultar información de dispositivos de bloques. 
ej:sudo blkid /dev/sdb1 
/dev/sdb1: UUID="788fb4c5-4bd9-421a-b3c3-43148f6995f8" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="f979653d-01"
Revisa esa particion especifica muestra UUID,filesystem,tipo,label

** Umask
es la mascara que quita permisos a archivos/directorios nuevos 
Idea linux crea permiso base , luego umask elimina algunos 
base normal Archivos 666 rw-rw-rw-