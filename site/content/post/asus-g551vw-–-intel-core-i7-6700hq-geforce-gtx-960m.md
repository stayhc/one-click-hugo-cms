---
title: Asus G551VW – Intel Core i7-6700HQ / GeForce GTX 960M
date: 2017-12-02T15:19:37-03:00
description: >-
  Esto es una recopilación de información obtenida de diferentes fuentes para
  poder instalar una distro (Linux Mint en mi caso, pero aplicable a otras
  distros) en esta maldita configuración de hardware.
---
Esto es una recopilación de información obtenida de diferentes fuentes para poder instalar una distro (Linux Mint en mi caso, pero aplicable a otras distros) en esta maldita configuración de hardware.

## Pre requisitos

* Secure boot debe estar desactivado en la BIOS, en algunos casos no es necesario.
* Si intentas instalar en dual boot con windows, fast boot tiene que estar desactivado.
* USB/LoQueSea con la imagen grabada de la distro.

## Instalación

* Bootear la unidad grabada en tu pc.
* Cuando cargue el grub, con las opciones de instalación de la distro, presionar la tecla ”e” para poder modificar los parámetros de booteo del kernel de **quiet splash**
* Seleccionar por completo el texto quiet splash y reemplazarlo por lo siguiente.


```
modprobe.blacklist=nouveau acpi_osi=! idle=nomwait acpi_enforce_resources=lax acpi_backlight=native
```



**\*Es una sola linea de texto, copiar texto entero\***

**\*\*\*Si no se reemplaza ”quiet splash” solo obtendrás una pantalla negra o quedara congelado/loop ejecutando una acción sin poder dejarte continuar con la instalación\*\*\***

* Una vez reemplazado el texto, presiona F10 para bootear.
* Ahora deberí­a cargar el entorno gráfico o grub (dependiendo de la distro) que te permitirá la Instalación.
* Configura y reinicia.

## Configuración inicial

* Conectate a una red (de preferencia por cable).
* Actualiza tu sistema.


```
sudo apt update
```

```
sudo apt upgrade
```

## Instalando el controlador de nvidia

**\*\*\*Si no quieres tener que reemplazar los parámetros de booteo del kernel en cada reinicio es fundamental instalar los driver de nvidia, porque los nouveau son la principal causa de este dolor de culo\*\*\***

* Agrega los repositorios de nvidia (Aplicable solo a distros derivadas de ubuntu, pls no preguntas weonas)


```
sudo add-apt-repository ppa:graphics-drivers/ppa
```

```
sudo apt update
```

* Instala los drivers.


```
sudo apt install nvidia-384
```

**\*Puedes reemplazar el valor numérico ”384” por la versión mas actual en caso de haber una\***

**\*\*\*Si intentas cambiar el perfil prime en la configuración del driver nvidia por el intel (power saving mode) lo mas probable es que al reiniciar el equipo la pantalla quede negra\*\*\***

**\*\*\*\*\*En caso que el aviso anterior no fue suficiente para evitar cambiarlo tu estupidez, tendrás que entrar en modo de recuperación el cual se encuentra en el grub (opciones avanzadas del kernel), cargas el modo de recuperación en el cual el entorno gráfico estará por modo software, abres la terminal y ejecutas el siguiente comando ”sudo prime-select nvidia” , reinicias tu equipo y todos felices\*\*\*\*\***

Cuando encuentre la forma de poder usar la tarjeta de video Intel, para ahorrar batería y evitar que se caliente, modificare esta no-guia, besitos.
