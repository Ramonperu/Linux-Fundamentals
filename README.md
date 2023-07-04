# FUNDAMENTALS LINUX 

Bienvenidos a la guía para principiantes de Linux realizada por Ramón Peinado Ruiz.

## CONCEPTOS BASICOS

### EL VALOR DE LINUX

Linux suele ser el sistema operativo elegido en el Centro de Operaciones de Seguridad (SOC). Estas son algunas de las razones para elegir Linux:

**Linux es de código abierto**: cualquier persona puede adquirir Linux sin coste alguno y modificarlo para adaptarlo a sus necesidades específicas. Esta flexibilidad permite a los analistas y administradores crear a medida un sistema operativo específico para el análisis de seguridad.
**La CLI de Linux es muy potente**: La interfaz de línea de comandos (CLI) de Linux es extremadamente potente y permite a los analistas realizar tareas no sólo directamente en un terminal, sino también de forma remota.
**El usuario tiene más control sobre el sistema operativo:** El usuario administrador en Linux, conocido como usuario raíz o superusuario, tiene poder absoluto sobre el ordenador. A diferencia de otros sistemas operativos, el usuario root puede modificar cualquier aspecto del ordenador con sólo pulsar unas teclas. Permite al usuario root tener un control preciso sobre la forma en que el sistema operativo gestiona los paquetes de red.
**Permite un mejor control de la comunicación de red** - El control es una parte inherente de Linux. Debido a que el sistema operativo se puede ajustar en prácticamente todos los aspectos, es una gran plataforma para la creación de aplicaciones de red. 

**La flexibilidad que ofrece Linux**: es una gran característica para el SOC. Todo el sistema operativo puede adaptarse para convertirse en la plataforma de análisis de seguridad perfecta. Por ejemplo, los administradores pueden añadir sólo los paquetes necesarios al sistema operativo, haciéndolo más ligero y eficiente. Pueden instalarse y configurarse herramientas de software específicas para que funcionen conjuntamente, lo que permite a los administradores construir un ordenador personalizado que encaje perfectamente en el flujo de trabajo de un SOC.

La imagen muestra Sguil, que es la consola del analista de ciberseguridad en una versión especial de Linux llamada Security Onion. 

<img src="/img/14ºimagenn.PNG" style="zoom:150%;" />



Herramientas típicas de un SOC:

- Software de captura de paquetes de red.
- Herramientas de análisis de malware.
- Sistemas de detección de intrusos (IDS).
- Cortafuegos.
- Gestores de registros.
- Gestión de eventos e información de seguridad (SIEM).
- Sistemas de tickets.

------



### DIRECTORIOS Y SISTEMAS DE ARCHIVOS

*En Linux y Unix todo es un fichero. Los directorios son ficheros, los ficheros son ficheros, y los dispositivos son ficheros. A veces a los dispositivos se les llama nodos, pero siguen siendo ficheros*.

Los sistemas de ficheros de Linux y Unix se organizan en una **estructura jerárquica**, de tipo árbol. El nivel más alto del sistema de ficheros es `/` o directorio raíz. Todos los demás ficheros y directorios están bajo el directorio raíz. Por ejemplo, `/home/ramon/cheeses.odt` muestra la ruta completa al fichero `cheeses.odt` que está en el directorio `ramon`, que a su vez está bajo el directorio `home`, que por su parte está bajo el directorio raíz (`/`).

Ejemplo 

**Directorio raíz de una distro MINT**

<img src="/img/2ºimagenn.png" style="zoom:150%;" />

Por debajo del directorio raíz (`/`) hay un importante grupo de directorios común a la mayoría de las distribuciones de GNU/Linux. A continuación hay una lista de los directorios que aparecen normalmente bajo el directorio raíz (`/`):

- `/bin` - aplicaciones *bin*arias importantes.
- `/boot` - Ficheros de configuración del arranque, núcleos y otros ficheros necesarios para el arranque (*boot*) del equipo.
- `/dev` - los ficheros de *dispositivo.*
- `/etc` - ficheros de configuración, scripts de arranque, *etc*.
- `/home` - directorios personales (*home*) para los diferentes usuarios.
- `/initrd` - usado cuando se crea un proceso de arranque *initrd* personalizado.
- `/lib` - librerías del sistema (*lib*raries).
- `/lost+found` - proporciona un sistema de "perdido+encontrado" (*lost+found*) para los ficheros que existen debajo del directorio raíz (`/`).
- `/media` - particiones montadas (cargadas) automáticamente en el disco duro y medios (*media*) extraíbles como CDs, cámaras digitales, etc.
- `/mnt` - sistemas de archivos *m*o*nt*ados manualmente en el disco duro.
- `/opt` - proporciona una ubicación donde instalar aplicaciones opcionales (de terceros).
- `/proc` - directorio dinámico especial que mantiene información sobre el estado del sistema, incluyendo los *proc*esos actualmente en ejecución.
- `/root` - directorio personal del usuario *root* (superusuario); también llamado "barra-root".
- `/sbin` - *bin*arios importantes del *s*istema.
- `/srv` - puede contener archivos que se *s*i*rv*en a otros sistemas.
- `/sys` - archivos del sistema (*sys*tem).
- `/tmp` - *t*e*mp*orary files.
- `/usr` - aplicaciones y archivos a los que puede acceder la mayoría de los *us*ua*r*ios.
- `/var` - archivos *var*iables como archivos de registros y bases de datos.

------



### PERMISOS:

*Permiten crear **restricciones** al realizar determinadas operaciones sobre archivos o directorios.* Son capaces de diferenciar quién los está usando: 

Si es su **propietario**, si es un **grupo** autorizado para ello o si son **otros**.

Tenemos una secuencia de **10 caracteres**: -rwxr-xr–-

<img src="/img/16ºimagenn.PNG"/>



Empecemos a definir valores de izquierda a derecha.

El **tipo de archivo** puede ser:

|      | **Identifica**                                               |
| ---- | ------------------------------------------------------------ |
| –    | Archivo                                                      |
| d    | Directorio                                                   |
| b    | Archivo de bloques especiales (Archivos especiales de dispositivo) |
| c    | Archivo de caracteres especiales (Dispositivo tty, impresora…) |
| l    | Archivo de vinculo o enlace (soft/symbolic link)             |
| p    | Archivo especial de cauce (pipe o tubería)                   |

Los **permisos** pueden ser:

| **Permiso** | **Identifica**       |
| ----------- | -------------------- |
| –           | Sin permiso          |
| r           | Permiso de lectura   |
| w           | Permiso de escritura |
| x           | Permiso de ejecución |

------



### CONSULTA DE LOGS

Los **logs o registros del sistema** son ficheros de texto que registran cronológicamente la totalidad de actividades e incidencias importantes que ocurren en el sistema operativo o red. Es una herramienta que puede ayudar a los administradores de sistemas a:

- Detectar la causas de los problemas que puede tener un equipo o servidor.
- Registrar y detectar ataques informáticos por parte de un hacker.
- Detectar comportamientos anómalos de programas o servicios que tenemos instalados en nuestro equipo.
- Ver el rendimiento de un ordenador o servidor.
- Averiguar que ocurrió en una determinada actualización de un equipo

Ejemplos de la información que contienen los logs:

- Los paquetes que se instalan y desinstalan en el sistema operativo.
- Información sobre los accesos remotos a nuestro equipo.
- Los intentos fallidos de autenticación de los usuarios al equipo.
- Registro de errores que se dan en los programas o servicios que usamos.
- Los accesos o salidas bloqueadas por nuestro firewall.

Dentro de `/var/log` encontramos **la gran mayoría de información de servicios, sistema... etc**. La configuración de servicios como un nginx, mysql o cualquier otra aplicación que deje logs se guardara por defecto aqui dentro.

`demsg`: Es un comando que lista el buffer de mensajes del núcleo. Este buffer contiene una gran variedad de **mensajes importantes generados durante el arranque del sistema** y durante la depuración de aplicaciones. Nos puede ser útil para la **detección de posibles errores de nuestro sistema y en el hardware**

`journalctl`: Muestra logs generados por los servicios gestionados por systemctl.

Los logs de servicios están configurados en `/etc/rsyslog.d`

En el interior tenemos un archivo de configuración donde podemos definir distintos parámetros :

- -Guardar logs de error avisos o toda la información.
- -La ubicación.
- -La rotación y eliminación de los logs a lo largo del tiempo.

------



### CONFIGURACIÓN DE ENTORNO DE TRABAJO:

Una de las variables de entorno mas famosas que un usuario del sistema puede llegar a manejar es el **$PATH**.

<img src="/img/31ºimagenn.PNG"/>

Es una variable que le dice al sistema que cuando se ejecute cualquier comando, por ejemplo "ls", le diga al sistema que vaya a buscar ese ejecutable a cualquiera de esas carpetas. En caso de no encontrarlo devuelve un "Not found".

Podemos averiguar donde se encuentra el ejecutable de "ls" con un simple `whereis ls` que nos localiza el archivo binario, el código fuente y la página del manual de un determinado comando.

<img src="/img/32ºimagenn.PNG"/>

La mayoría de los binarios deberían de estar dentro de un path, cuando instalas algo fuera de estos directorios y tu path no lo recoge, has de añadirlo manualmente.

Nuestro bash tiene una serie de **archivos de configuración** ocultos, ejecutando un `ls -la` podemos verlos a simple vista:

<img src="/img/33ºimagenn.PNG"/>

Uno de los **archivos de configuración** mas interesantes es este **.bashrc**, modificar aspectos de este archivo de configuración sin los conocimientos adecuados puede dejarnos sin shell, se recomienda hacer un backup y/o tener un segundo usuario para poder acceder a la maquina en caso de errores.

Dentro de este archivo hay mucha información, normalmente son cosas que se ejecutan al entrar para facilitarnos el uso. 

Este archivo permite una alta personalización del sistema:

- Una de la utilidades mas básicas que podemos configurar son los **ALIAS** (Atajos de teclado que podemos definir a nuestro gusto). 

- Dentro de **.bashrc **es donde **definimos nuestro $PATH o lo ampliamos**. Podemos definir otra variable en vez de $PATH, mucho mas simple que solo busque dentro de la ubicación que le indiquemos.

- Podemos personalizar nuestro shell en cuanto a colores se refiere y datos que se muestran. 

<img src="/img/34ºimagenn.PNG"/>

Ejemplo:

**Definición de alias**

<img src="/img/35ºimagenn.PNG"/>

Guardamos y si entramos y salimos se recargaría, o bien hacemos un llamada con `source .bashrc` y comprobamos que el alias se ejecuta correctamente

<img src="/img/36ºimagenn.PNG"/>





Ejemplo:

**Ampliación del $PATH**

<img src="/img/37ºimagenn.PNG"/>

Añadimos al final del archivo **.bashrc** la ruta que queremos añadir para que el $PATH busque binarios dentro de esta misma, volvemos a hacer un `source .bashrc` y comprobamos que nuestro $PATH esta actualizado

<img src="/img/38ºimagenn.PNG"/>



Ejemplo:

**Definición de otra variable independiente del $PATH**

<img src="/img/39ºimagenn.PNG"/>

Si no ejecutamos el `source .bashrc` antes de hacerle un echo a LIBRERIAS no  nos devolverá nada

<img src="/img/40ºimagenn.PNG"/>

Ejemplo:

**Personalización del shell**

<img src="/img/41ºimagenn.PNG"/>

Al eliminar el comentario el "prompt" ya por defecto se va a ver coloreado.

<img src="/img/42ºimagenn.PNG"/>

Hay muchas opciones de personalización del bash modificando la variable PS1. 

Esta variable es un poco difícil de entender a continuación se muestran los parámetros principales:

- **\u@** – El nombre de usuario logueado seguido del símbolo @.
- **\h** – El nombre de host.
- **\w** – El directorio de trabajo actual.

Algunos parámetros extra:

- **\d** – Fecha actual en formato <sábado, septiembre, 26>
- **\j** – Número de tareas ejecutadas por la terminal.
- **\v** – Versión de Bash.

------



### ENLACE DURO:

*Entendemos un enlace duro como un "mote" para un archivo, el archivo es el mismo, la manera de llamarlo es distinta, el enlace duro esta limitado a:*

1. **Solamente puede hacerse entre ficheros(No carpetas, no directorios).**

2. **Dentro del mismo sistema de ficheros.**

Ejemplo:

**Ejecutamos**

`ln f1 f2` -> Accedamos mediante f1 o f2 el interior del archivo será lo mismo 

<img src="/img/3ºimagenn.PNG"/>

Ambos compartirán el mismo identificador si ejecutamos ls -li (Comando para ver identificadores o inodos). A su vez si modificamos el archivo el cambio se vera en ambos accediendo desde sus distintos "motes" o enlaces duros.	

### ENLACE SIMBOLICO:

*Entendemos como enlace simbólico lo que es un enlace directo en Windows, normalmente es para carpetas o ficheros fuera de su ubicación*

1. **No dispone de limitaciones**.

`ln -s f1 f3`

<img src="/img/1ºimagenn.png"/>

------



### RUTAS RELATIVAS Y ABSOLUTAS

*Entendemos **ruta absoluta** como aquella ruta en la que partimos de la raíz para indicar la ruta completa*

Ejemplo

<img src="/img/4ºimagenn.PNG"/>

*Entendemos como **ruta relativa** aquella ruta en la que usamos una parte de la ruta actual para acceder a otra parte de esta.*

Ejemplo:

<img src="/img/5ºimagenn.PNG"/>

Como se observa aprovechamos que estamos en etc y entramos en ssh directamente sin tener que ponerle la ruta absoluta que en este caso seria cd /etc/ssh.

------



### PIPELINES - TUBERIAS O |:

*Se entiende como pipeline la manera de incluir una salida de un comando como entrada de otro comando*.

------



### PROGRAMACION DE TAREAS

Podemos tener diferentes tareas programadas, incluso por usuarios. Dentro del directorio etc/ encontramos un fichero el cual se muestra de la siguiente manera si ejecutamos un `cat crontab`:

<img src="/img/28ºimagenn.PNG"  />

Como se observa podemos indicar la fecha y hora exacta, el usuario y el comando que vamos a ejecutar. 

Para indicar por ejemplo que queremos que se ejecute todos los dias de un mes dejaremos el espacio designado con un `*`.

Observamos también que hay otros "cron" separados por carpetas para ejecutar cosas cada hora, dia, semana o mes.

Para añadir una entrada nueva necesitamos permisos de root y nuestro editor de texto.

Todos los usuarios disponen de un cron y todos estos crons se ejecutaran con los permisos independientes de cada usuario.

Podemos **llamar al cron de nuestro usuario** directamente con `crontab -e`:

Nos preguntara que editor queremos por defecto al abrirlo

<img src="/img/29ºimagenn.PNG"  />

Este fichero funciona de la misma manera pero no hace falta indicar el usuario.

------



## COMANDOS

A continuación se van a explicar las herramientas necesarias para el uso de la línea de comandos de Linux de manera simple y ejemplificada.

### AYUDAS

Todos o casi todos los comandos vienen con un manual de ayuda que se consigue con:

`comando --help o comando -h`

Si la información del comando supera la cantidad mostrable en pantalla lo combinaremos con un | more para que pagine y muestre la información paulatinamente.

Todo esto se transforma en man de manual y en esta versión la información esta mucho mejor estructurada. Salimos del manual con q.

A parte de estas dos ayudas podemos invocar a la shell **FISH**, tras instalarla esta shell al tabular nos ira informando de posibles comandos y su información correspondiente.

### COMANDOS BASICOS

`Ls`: Lista del directorio actual.

`ls -l `: Lista de ruta actual o concreta con + inf.

`ls -la`: Lista y muestra archivos y archivos ocultos.

`ls -li`: Lista de ruta actual + inodos.							

`pwd  `: Muestra ruta actual.	

`cd `: Cambio de directorio.

`cd .. `: Subes un directorio por encima de donde te encuentres.

`find`: Búsqueda en disco por determinados parametros.

`locate`: Herramienta de búsqueda mas cómoda, hay que instalarla y mantener la base de datos actualizada para que no muestre archivos eliminados.

------



### SALIDAS DE COMANDOS Y REDIRECCIONES:

`echo $?`: Nos indica el estado de la ultima ejecución, devuelve un numero, 0 si se ha ejecutado correctamente, 1 si devuelve un error.

Cuando ejecutamos un comando o script el sistema nos puede devolver dos respuestas:

Si devuelve un resultado obtenemos **la salida estándar** identificada con un **1**.

Si devuelve un error obtenemos **la salida de error** identificada con un **2**.

Estas salidas pueden tener un alto valor de información para los administradores a continuación se muestra su utilidad.



Ejemplo:

**Volcar la salida temporal**

Obtenemos la salida estándar

<img src="/img/62ºimagenn.PNG"  />

La volcamos(sobrescribe) a un archivo temporal con un `ls -l > /tmp/1`, podemos comprobarlo posteriormente

<img src="/img/63ºimagenn.PNG"  />

Si por ejemplo queremos añadir sin sobrescribir lo ya escrito, por ejemplo añadamos la salida estandar de la raíz

`ls -l / >> /tmp/1`

<img src="/img/64ºimagenn.PNG"  />

Ejemplo:

**Volcar la salida de error**

Obtenemos la salida del error

<img src="/img/65ºimagenn.PNG"  />

La volcamos en el archivo temporal y comprobamos que se haya guardado

<img src="/img/66ºimagenn.PNG"  />

------



### FECHA Y HORA

`date`: Muestra la fecha en pantalla.

`sudo timedatectl set-timezone`: Especifica zona horaria.

**Los servidores deben tener la fecha actualizada**, no tener la hora bien puede ser critico para un sistema, para asegurarnos que nuestra maquina se mantiene actualizada hemos de configurar un servidor de tiempo y hay dos maneras de realizarlo.

- Instalar un servicio local y configurarlo para que fuera actualizando.
- Instalar un servicio externo y configurarlo.



### DISTRIBUCION TECLADO

Suele suceder que la distribución de teclas que coge el sistema de manera default no se corresponde con la de nuestro teclado.

`sudo loadkeys es`: Permite cambiar la distribución de teclas de manera no permanente.

`sudo dkpg reconfigure console-setup`: Permite elegir codificación fuente set de caracteres...

------



### INSTALACION Y GESTION PAQUETES

`apt-get`: Aplicación para gestionar paquetes.

`apt`: Aplicación para gestionar paquetes mas reciente y depurada.

`apt remove`: Desinstala un paquete en concreto.

`apt purge`: Desinstala y purga todas las configuraciones del paquete. Invita a realizar un `apt autoremove`.

`apt autoremove`: Quita los paquetes extra que suelen venir y se descargan de manera automáticamente.

`dkpg`: Herramienta de gestion de paquetes. No tiene en cuenta las dependencias y has de descargarlas de manera manual.

Otra manera de instalar paquetes de manera mas visual es `aptitude`:

<img src="/img/22ºimagenn.PNG"/>

------



### PERMISOS

`chmod`: Permite cambiar los permisos

Ejemplo:

**Cambio de permisos**

<img src="/img/17ºimagenn.PNG"/>

Vamos a **analizar los permisos** de miprimerscrip.sh:

​																		-rw-rw-r--

Es un **archivo**, el **propietario** puede **leer** y **escribir**,el **grupo** puede **leer** y **escribir** ,**otros** usuarios solo pueden **leer**.

Comprobamos que no podemos ejecutarlo: 

<img src="/img/18ºimagenn.PNG"/>

Le damos permiso al usuario de ejecución:

​																`chmod u+x miprimerscript.sh`

<img src="/img/19ºimagenn.PNG"/>

Como se observa los caracteres han cambiado a -rwxrw-r--1 y el color del script ahora se muestra en verde al ser ejecutable:

<img src="/img/21ºimagenn.PNG"/>

Para **dar permisos** a alguien que no seria el usuario cambiamos `u+x` por:

`g+x`: Para grupo.

`o+x`: Para otros

`a+x`: Para todos

Para **retirar** un permiso usaremos un signo `-`:

`g-x`: Para grupo.

`o-x`: Para otros

`a-x`: Para todos

------



### RECURSOS SISTEMA

`df -h `: Estado del disco.

`free -h`: Estado de la memoria.

`uptime`: Carga del sistema.

`cat /proc/cpuinfo`: Muestra cpu's.

`ps`:Procesos actuales.

`top `: Muestra todos los procesos en treal.

`htop`: Mismo comando, mejora visual.

<img src="/img/12ºimagenn.PNG"/>

- PID: "Process id", para diferenciar cualquier proceso.
- User: Usuario que lanza el proceso.
- NI(nice): Lo educada que es la tarea, utilidad con prioridad de CPU particular.
- PRI: Prioridad que asigna el kernel a una lista de tareas.

` shutdown`: Apaga el sistema.

------



### GESTION DE USUARIOS

 `adduser "nombreusuario"`: Crea al usuario y los recursos necesarios.Solicita contraseña.

`deluser "nombreusuario"`: Elimina usuarios.

Podemos editar la lista de sudoers: Lista de usuarios que si pueden utilizar el sudo.

`visudo` como usuario root o `sudo visudo` para editar la lista.

`passwd`: Cambia contraseña usuario actual

------



### MOVIMIENTO, COPIA Y ELIMINACION DE FICHEROS Y DIRECTORIOS

`mkdir`: Creación de un directorio debajo del actual

`cp "fichero" "copiafichero"`: Realiza una copia del fichero(Un inodo distinto).

Ejemplo con directorio:

-rp para que copie todo de manera recursiva y para que mantenga los mismos permisos.	

`*cp -rp directorio copiadirectorio*`

<img src="/img/6ºimagenn.png"  />



`mv "fichero" "nuevonombre"`: renombra ficheros y directorios.

`mv "fichero" /ruta`: Mueve fichero.

Si es dentro de la misma ruta en la que te encuentra "directorio/".

`rm "/rutaficheroaborrar`: Borra un fichero de una ruta concreta.

`file fichero-directorio/`: Te indica que tipo de fichero o directorio es.

`scp`: Es muy similar a `cp` comando para copiar archivos, con una adición: puede incluir nombres de host remotos en los nombres de ruta de origen o destino

`sftp`:Es un programa de copia de archivos similar a `ftp`. Utiliza un túnel encriptado SSH para copiar archivos.

El comando ` stat` proporciona una información mas detallada acerca de un fichero-directorio:

<img src="/img/7ºimagenn.PNG"  />

`grep -i "abuscar" "nombre fichero" `: Incluye un parámetro a la búsqueda.

-i obvia diferencia con mayusculas y minusculas

`grep -iv "aexcluir" "nombre fichero"`: Excluye un parámetro de la búsqueda.



Ejemplo

**Cortar columnas**

<img src="/img/9ºimagenn.PNG"  />

- -d Indica el delimitador(por eso introducimos los espacios).
- -f indica la columna con la cual te vas a quedar.

------



### ARCHIVOS COMPRIMIDOS

`gzip`: Comprime un archivo borrando su versión original.

`gunzip`: Devuelve el archivo a su formato original.

`zcat`: Muestra el contenido de un archivo comprimido.

Ejemplo:

Paquetizacion carpeta

`*tar cfv "nombreacomprimir" rutacarpetacomprimir/*`

- v para mostrar en pantalla que va a paquetizar.
- c para decirle que estas creando.
- f para ponerle el parámetro del nombre.
- z si queremos que **comprima** todo esto y disminuya su tamaño (.tgz).

- x si queremos que **descomprima** todo esto y lo devuelva a su versión original



Ejemplo:

**Descomprimir archivo**

<img src="/img/11ºimagenn.PNG"  />

------



### ADMINISTRACIÓN DE DISCOS

`lsblk`: Muestra los discos del sistema.

`mkfs.`: Nos permite formatear, a continuación del punto hemos de indicar que tipo de formato se le dará al disco tras el formateo y tras esto hemos de indicar que partición queremos formatear.

`fdisk -l` : Muestra todas las particiones existentes en nuestro sistema.

`fdisk -l /dev/"nombredeldisco"`: Muestra un disco en especifico.

`fdisk /dev/"nombredeldisco"`: Nos pone a trabajar sobre un disco en concreto, si queremos ver todas las opciones disponibles sobre este presionaremos m.

<img src="/img/43ºimagenn.PNG"  />



Ejemplo

**Particionar un disco**

Le indicamos al sistema mediante el comando `fdisk /dev/sda`, esperamos a que nos muestre lo siguiente:

<img src="/img/44ºimagenn.PNG"  />

Presionamos`p` para mostrar en pantalla la tabla de partición:

<img src="/img/45ºimagenn.PNG"  />

 Seleccionamos `n`: Para crear una nueva partición y a continuación se nos preguntan parámetros de la misma, primaria(`p`) o extendida(`e`),<img src="/img/46ºimagenn.PNG"  />

Nº de partición, primer sector y ultimo sector. 

De manera extra se nos menciona que la partición nº1 dispone de una "ext4 signature" esto básicamente es una marca/indicador de que hay algo dentro de nuestro disco, también puede identificar a una partición, sin embargo, este disco es un pendrive que acabamos de formatear para el ejemplo y se encuentra vacío, podemos seguir con total seguridad.



Ejemplo

**Cambiar tipo de partición**

Seleccionamos`t`: Para cambiar el tipo de partición, posteriormente nos pedirán un código hexadecimal un alias o la posibilidad de listar todos los tipos de particiones a nuestra disposición

<img src="/img/47ºimagenn.PNG"  />



Ejemplo 

**Formateo de particion**

`mkfs.ext4 /dev/sda1`

Podemos elegir muchos sistemas de fichero para montar, seleccionamos el ext4 por que es uno de los mas extendidos, normalmente se elige en función del uso que se le vaya a dar al disco/particion

<img src="/img/48ºimagenn.PNG"  />

Si deseáramos por ejemplo formatear el disco entero y eliminar esa partición indicaríamos en la ruta el nombre del disco:

<img src="/img/49ºimagenn.PNG"  />



Ejemplo

**Montar un disco**

Planteamos que nuestro disco tiene dos particiones una de 1.4G y otra de 500M, vamos a montar la de 500M

<img src="/img/50ºimagenn.PNG"  />

Hemos de decirle al sistema donde esta el disco para que este pueda utilizarlo.

Vamos a crear un directorio donde montarlo.

<img src="/img/51ºimagenn.PNG"  />

Después de esto montamos el disco, pero antes hemos de formatearlo, si no obtenemos el error mostrado en la imagen.

<img src="/img/52ºimagenn.PNG"  />

` mount -t ext4 /dev/sda1 /home/ramon/discomontado`

Si ejecutamos un `df -h` veremos que ya se encuentra montado

<img src="/img/53ºimagenn.PNG"  />

Otra manera de comprobarlo es la siguiente:

<img src="/img/54ºimagenn.PNG"  />

------



### GESTION DE TAREAS Y SERVICIOS

##### TAREAS

Para evitar que un proceso se nos quede ejecutando y no podamos realizar ninguna tarea extra tenemos las siguientes herramientas.

 `ctrl+z`: Podemos pausar el proceso.

`jobs`: Nos muestra las tareas pendientes.

`screen`: Permite abrir múltiples instancias de terminal dentro de una sola sesión, nos permite dejar el proceso en ejecución al cerrarlo ya que continuara en segundo plano. 

Ejemplo

**Parar una proceso y ponerlo en segundo plano**

Vamos a usar el comando sleep para que nuestro consola se quede ejecutando esta tarea:

<img src="/img/55ºimagenn.PNG"  />

La pausamos y posteriormente la ponemos en segundo plano.

`bg %1` escribimos %1 porque es el numero del proceso de nuestra tarea, al ser la primera y única no hay mas opciones.

<img src="/img/56ºimagenn.PNG"  />

Si escribimos `sleep 1500 &` la tarea se ira directamente a segundo plano.

Para recuperar la tarea en pantalla hemos de escribir `fg %1` de la misma manera indicando el numero del proceso de nuestra tarea.



##### SERVICIOS

Vamos a instalar `NGINX` con un simple `apt install nginx`, una vez instalado comprobamos que el servicio se ha iniciado:

<img src="/img/57ºimagenn.PNG"  />

Para parar un servicio usamos el comando `systemctl stop nginx.service`.

<img src="/img/58ºimagenn.PNG"  />

Para arrancar el servicio de nuevo usamos el comando `systemctl start nginx.service.`

<img src="/img/59ºimagenn.PNG"  />

Para mostrar el estado del servicio usamos el comando `systemctl status nginx.service.`

<img src="/img/60ºimagenn.PNG"  />



Si nos esta fallando el servicio podemos acceder a logs mas ampliados de la siguiente manera.

`journalctl -u nginx.service -xe`

<img src="/img/61ºimagenn.PNG"  />

------



### NET

`ip add`: Muestra información de las interfaces, podemos averiguar nuestra direcciones ip.

`ip link show`: Muestra las interfaces de red 

`ip link`: Configurar agregar y eliminar interfaces de red

`ip route show`  : Muestra rutas.

`nmap`: Muestra los puertos, su estado (abierto / cerrado) y los protocolos.

`tcpmdump`: Herramienta de detección de paquetes

`dig`: (Domain Information Groper) es una herramienta flexible para interrogar a los servidores de nombres DNS.

`nslookup`: nslookup es una herramienta de línea de comandos muy práctica y fácil de usar, cuya función básica es encontrar la dirección IP de un equipo determinado o realizar una búsqueda DNS inversa (es decir, encontrar el nombre de dominio de una determinada dirección IP)

`curl`: Sirve para transferir datos hacia o desde un servidor con URL. Admite HTTP, FTP, POP3, IMAP, SMTP, SCP, SFTP, TFTP, TELNET, LDAP…

`wget`: Usado para recuperar contenido y archivos de varios servidores web. Admite FTP, SFTP, HTTP y HTTPS.

`iwconfig`: Información wifi.

<img src="/img/15ºimagenn.PNG"  />

Ejemplo 

**Cambio IP**

<img src="/img/23ºimagenn.png"  />

En azul nuestra IP, en verde nuestra puerta de enlace, y en naranja la red a la que pertenecemos.

Accedemos a /etc/netplan, configuramos el fichero 1-network-manager-all.yaml,

`nano 1-network-manager-all.yaml` Necesitamos permisos de root para editar este fichero:

<img src="/img/24ºimagenn.PNG"  />

Tras modificar el archivo aplicamos el siguiente comando

`netplan try` nos pedirá confirmar los cambios realizados:

<img src="/img/25ºimagenn.PNG"  />

**Existe otro comando que se usa menos por razones de seguridad `netplan apply`, aplica los cambios directamente sin preguntar*

Comprobamos que nuestra ip haya cambiado a la 192.168.1.54:

<img src="/img/26ºimagenn.PNG"  />

Comprobamos que seguimos resolviendo direcciones haciendo un ping.

<img src="/img/27ºimagenn.PNG"  />

------



### FIREWALL

`sudo ufw enable`: Activar Firewall.

`sudo ufw disable`: Deshabilitar firewall.

`sudo ufw allow ssh` / `sudo ufw allow 22/tcp`: Habilitar ssh.

`sudo ufw allow "nºpuerto"/protocolo `: Habilitar regla firewall.

`sudo ufw status`: Verificar si la regla se aplico.

------



### SSH  

`sudo apt install openssh-server`: Instalar ssh.

`sudo systemctl start sshd`: Activar protocolo ssh.

`sudo netstat -plntu | grep ssh` :  Chequear puerto ssh.

Si queremos cambiar el puerto de ssh hemos de cambiar parámetros dentro del archivo de configuración `sshd_config`  que se encuentra en `/etc/ssh/` 

#### CREACION DE CLAVES SSH

La clave SSH implica generar un par de claves compuesto por dos largas cadenas de caracteres: una pública y otra privada. La clave pública se instala en el servidor y se desbloquea mediante la conexión con un cliente SSH que emplea la clave privada correspondiente. Si las dos claves coinciden, el servidor SSH concede acceso sin requerir una contraseña. Se le puede añadir una contraseña para aumentar la seguridad

`ssh-keygen`: Generación de ambas.

Pregunta en que ruta queremos guardarla y con que nombre `/home/usuario/.ssh/nombredelaclave`  , si no usa la ruta y el nombre default:

 (`/home/usuario/.ssh/id_rsa`) Pide un passphrase para la validación de la clave publica/privada, tras esto de vuelve un fingerprint.

------





## BIBLIOGRAFIA y AGRADECIMIENTOS

Esta guía básica no podía haber sido realizada sin la ayuda de estos dos cursos:

Aprende a usar la línea de comandos de Linux			Esther Yébenes 		Linkedin Learning.

Operating Systems Basics 																					Cisco Networking Academy.

Mencionar también la gran ayuda recibida por parte de toda la comunidad de Linux y sus foros .

