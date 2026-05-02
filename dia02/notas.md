###Gestión de discos en Linux (VirtualBox + /dev + particiones + mount)

###Descripción

En este laboratorio practiqué el flujo completo de gestión de discos en Linux utilizando VirtualBox.
Aprendí cómo se crea un disco virtual, cómo Linux lo detecta en /dev, cómo se divide en particiones y cómo se prepara para ser utilizado mediante filesystem y montaje

1. Creación del disco en VirtualBox
Inicie la máquina virtual y fui a la configuración de almacenamiento en VirtualBox.
Agregué un nuevo disco duro virtual con las siguientes características:

Formato: VDI (VirtualBox Disk Image)
Tamaño: 3 GB
Tipo: dinámico

Luego inicié nuevamente Fedora.

2.Comando lsblk 
Este comando permite visualizar los discos conectados al sistema y sus particiones.

¿Qué muestra?
Discos (ej: sda, sdb, sdc)
Particiones (ej: sda1, sdb1)
Tamaño de cada dispositivo
Tipo (disk o part)
Punto de montaje (dónde está conectado en el sistema)

3.Creación de partición con fdisk
Comando utilizado
sudo fdisk /dev/sdc
Qué hice dentro de fdisk?
Primero ejecuté:
m
Esto muestra todas las opciones disponibles dentro de fdisk.
Luego creé una nueva partición:
n
Seleccioné tipo primaria (p)
Elegí el número de partición (1)
Dejé valores por defecto para inicio y fin del disco
Finalmente guardé los cambios:
w
Resultado

Se creó la partición:

/dev/sdc1
Con tamaño total del disco (3 GB).

4. Creación del sistema de archivos (mkfs)
Comando utilizado
sudo mkfs.ext4 /dev/sdc1
 Qué hace

Crea un sistema de archivos ext4 en la partición, preparando el espacio para almacenar datos
Se crearon bloques (espacio del disco)
Se crearon nodos-i (estructura de archivos)
Se asignó un UUID (identificador único)

Luego verifiqué con:

lsblk -f

Y confirmé que /dev/sdc1 ahora tiene tipo ext4.

5. Montaje del disco
Comandos utilizados
sudo mkdir /disco_sdc
sudo mount /dev/sdc1 /disco_sdc
 Qué hace

Conecta la partición al sistema en una carpeta.

Verificación
lsblk

Resultado:

sdc1 → /disco_sdc

Montar significa hacer visible el contenido del disco en el sistema.
Sin mount, no se puede acceder a los datos.

6. Desmontaje del disco
Comando utilizado
sudo umount /dev/sdc1
 Qué hace

Desconecta la partición del sistema sin eliminarla.

 Verificación
lsblk

Resultado:

sdc1  (sin mountpoint)

El disco sigue existiendo, pero ya no está en uso.
Siempre se debe desmontar antes de retirar o modificar un disco.

CONCLUSIÓN FINAL DEL LABORATORIO

Aprendí el flujo completo de gestión de discos en Linux:

Crear disco (VirtualBox)
Detectarlo (lsblk)
Crear partición (fdisk)
Formatear (mkfs)
Montar (mount)
Usar
Desmontar (umount)

