# Actividad 3 - 201901598

## Parte 1: Gestión de Usuarios
## 1. Creación de Usuarios: Crea tres usuarios llamados `usuario1`, `usuario2` y `usuario3`.
sudo adduser usuario1

sudo adduser usuario2

sudo adduser usuario3

Consola: Adding user usuario1 ...
Adding new group usuario1 (1001) ...
Adding new user usuario1 (1001) with group usuario1 ...
Creating home directory /home/usuario1 ...
Copying files from /etc/skel ...
New password: 
Retype new password:
passwd: password updated successfully
Changing the user information for usuario1
Enter the new value, or press ENTER for the default
Full Name []: 
Room Number []:
Work Phone []: 
Home Phone []:
Other []: 
Is the information correct? [Y/n] Y

## 2. Asignación de Contraseñas: Establece una nueva contraseñas para cada usuario creado.
sudo passwd usuario1

Consola: Changing password for user usuario1
New password: 
Retype new password: 
passwd: password updated successfully

## 3. Información de Usuarios: Muestra la información de `usuario1` usando el comando `id`.
sudo id usuario1

Consola:  uid=1001(usuario1) gid=1001(usuario1) grupos=1001(usuario1)

## 4. Eliminación de Usuarios: Elimina `usuario3`, pero conserva su directorio principal.
sudo deluser --remove-home usuario3

Consola: Removing user usuario3 ...
Warning: group usuario3 has no more members.
Done.
Removing directory /home/usuario3

## Parte 2: Gestión de Grupos
## 1. Creación de Grupos: Crea dos grupos llamados `grupo1` y `grupo2`.
sudo addgroup grupo1

sudoaddgroup grupo2

Consola:  Adding group grupo1 (GID 1002) 

## 2. Agregar Usuarios a Grupos: Agrega `usuario1` a `grupo1` y `usuario2` a `grupo2`.
sudo usermod -aG grupo1 usuario1

usermod -aG grupo2 usuario2

Consola: Adding user usuario1 to group grupo1 

## 3. Verificar Membresía: Verifica que los usuarios han sido agregados a los grupos utilizando el comando `groups`.
groups usuario1

groups usuario2

Consola: usuario1 : usuario1 grupo1

## 4. Eliminar Grupo: Elimina `grupo2`.
sudo delgroup grupo2

Consola:  Removing group grupo2  
          Done.

# Parte 3: Gestión de Permisos

## 1. Creación de Archivos y Directorios: Como `usuario1`, crea un archivo llamado `archivo1.txt` en su directorio principal y escribe algo en él. Crea un directorio llamado `directorio1` y dentro de ese directorio, un archivo llamado `archivo2.txt`.
su usuario1

nano archivo1.txt

mkdir directorio1

cd directorio1

nano archivo2.txt


## 2. Verificar Permisos: Verifica los permisos del archivo y directorio usando el comando `ls -l` y `ls -ld` respectivamente.
ls -l archivo1.txt

Consola: -rw-r--r-- 1 usuario1 usuario1 42 ago  9 18:15 archivo1.txt

ls -ld directorio1

Consola: drwxr-xr-x 2 usuario1 usuario1 4096 ago  9 18:17 directorio1

## 3. Modificar Permisos usando `chmod` con Modo Numérico: Cambia los permisos del `archivo1.txt` para que sólo `usuario1` pueda leer y escribir (permisos `rw-`), el grupo pueda leer (permisos `r--`) y nadie más pueda hacer nada.
sudo chmod 640 archivo1.txt

## 4. Modificar Permisos usando `chmod` con Modo Simbólico: Agrega permiso de ejecución al propietario del `archivo2.txt`.
sudo chmod u+x archivo2.txt

## 5. Cambiar el Grupo Propietario: Cambia el grupo propietario de `archivo2.txt` a `grupo1`.
sudo chown :grupo1 archivo2.txt

## 6. Configurar Permisos de Directorio: Cambia los permisos del `directorio1` para que sólo el propietario pueda entrar (permisos `rwx`), el grupo pueda listar contenidos pero no entrar (permisos `r--`), y otros no puedan hacer nada.
chmod 550 directorio1

## 7. Comprobación de Acceso: Intenta acceder al `archivo1.txt` y `directorio1/archivo2.txt` como `usuario2`. Nota cómo el permiso de directorio afecta el acceso a los archivos dentro de él.
cat archivo1.txt

## 8. Verificación Final: Verifica los permisos y propietario de los archivos y directorio nuevamente con `ls -l` y `ls -ld`.
ls -ld directorio1

ls -l archivo2.txt

# Reflexión: (Opcional)

## ¿Por qué es importante gestionar correctamente los usuarios y permisos en un sistema operativo?
Gestionar correctamente los usuarios y permisos en un sistema operativo, como Ubuntu, es fundamental por varias razones tales como Seguridad del sistema, Prevención de accesos no autorizados, etc. 
