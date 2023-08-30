# Actividad 4
# Crear un systemd unit
## Juan Pablo García Ceballos
## 201901598

 
## Pasos de instalacion

1. Se crea un script en el cual se programara la funcionalidad del servicio. saludo.sh

```
#!/bin/bash
echo "Bienvenido, La fecha de hoy es: $(date)"
```
Para que el script tenga permisos se ejecuta:
```
chmod +x saludo
```

2. Se crea un archivo de systemd unit en la carpeta /etc/systemd/system/, nombrandolo 

```
sudo nano /etc/systemd/system/actividad4.service
```

3. Para crear el servicio se modifica con los siguiente comandos guardando los cambios.

```
[Unit] 
Description=Imprimir Saludo  

[Service]
Type=simple 
ExecStart=/home/linux/Escritorio/saludo.sh 

[Install] 
WantedBy=multi-user.target  
```

4. Para actualizar los servicios e incluir el servicio creado:
```
sudo systemctl daemon-reload  
```

5. Para iniciar el servicio se utiliza el comando: 
```
sudo systemctl start actividad4.service
```

NOTA: Para validar que el servicio se esta ejecutando:

```
sudo systemctl status actividad4.service  
```