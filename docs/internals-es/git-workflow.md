Flujo de trabajo con Git para los contribuyentes de Yii 2
=========================================================

¿Quires contribuir a Yii2? ¡Genial! Pero para incrementar la probabilidad de que tus cambios sean aceptados rápidamente, por favor, sigue los siguientes pasos (los dos primeros pasos sólo son necesario realizarlos la primera vez que contribuyas). Si eres nuevo con git y github, podrías mirar primero [ayuda de github](http://help.github.com/), [prueba git](https://try.github.com)
o aprender algo sobre [modelo de datos interno de git](http://nfarina.com/post/9868516270/git-is-simpler).

### 1. [Bifurca (Fork)](http://help.github.com/fork-a-repo/) el repositorio Yii en github y clona tu bifurcación para tu entorno desarrrollo

```
git clone git@github.com:YOUR-GITHUB-USERNAME/yii2.git
```

Si tienes problemas preparando GIT con GitHub en Linux, o estás teniendo errores como Permiso Denegado (clave pública) ("Permission Denied (publickey)"),
entonces debes [prepara tu instalación de GIT para trabajar con GitHub](http://help.github.com/linux-set-up-git/)

### 2. Añadir el directorio principal del repositorio Yii como un git remoto llamado  "upstream"

Cambiar al directorio donde has clonado Yii, normalmente, "yii2". Entonces ejecuta el siguiente comando:

```
git remote add upstream git://github.com/yiisoft/yii2.git
```

### 3. Asegurarte que hay creado un asunto sobre el tema de lo que tu estás trabajando y si requiere un esfuerzo significante para arreglarlo

Todas las nuevas capacidades y errores corregidos deben tener un asunto asociado para proveer un sólo punto de referencia para la discusión y documentación. Gasta un poco de tiempo para mirar a través de la lista de asuntos, para encontrar uno que corresponda con la contribución que tienes pensado hacer. Si encuentras uno ya en la lista de asuntos, entonces por favor deja un comentario sobre este asunto indicando que quieres trabajar sobre él. Si no encuentras un asunto que corresponda con lo que tienes pensado hacer, por favor crea un asunto para tu nuevo asunto o crea directamente una petición de extracción (pull request) si es un arreglo directo. Esto le permite al equipo revisar tu sugerencia, y proveer la apropiada sobrealimentación sobre la marcha.

> Para cambios pequeños o documentación sobre asuntos o directamente un arreglo, no necesitas crear un asunto, una petición de extracción (pull request) es suficiente en este caso.

### 4. Traer el  último código desde la principal rama de Yii

```
git fetch upstream
```

Esto es lo primero que has de hacer para cada nueva contribución asegurándote que estás trabajando con el último código.

### 5. Crea una nueva rama (branch) para tu característica basada en la actual rama master de Yii
> Esto es muy importante dado que no vas a poder enviar mas de un petición de extracción (pull request) desde tu cuenta si estás usando la rama master.

Cada error corregido o cambio distinto debe ir en su propia rama. Los nombres de las ramas deben de ser descriptivos e iniciarse con el número de asunto con el que tu código está relacionado. Si no estas arreglando ningún asunto en particular, entonces evita el número.
Por ejemplo:

```
git checkout upstream/master
git checkout -b 999-nombre-de-tu-rama-va-aqui
```

### 6. Haz tu magia, escribe tu código

Asegúrate que funciona :)

Los tests unitarios son siempre bienvenidos. Código probados y bien protegido, simplifica enormemente las tareas de comprobación de tus contribuciones.
Los tests unitarios fallidos con una descripción del asunto son también aceptados.

### 7. Actualiza el registro de cambios (CHANGELOG)

Edita el fichero de registro de cambios (CHANGELOG) para incluir tu cambio, y debes insertarlo al inicio del fichero bajo el encabezado "Work in progress" (trabajo realizándose) , la línea en el fichero de registro de canbios debe parecerse a la siguiente:

```
Bug #999: una descripción del error arreglado (Tu nombre)
Enh #999: una descripción de la mejora (Tu nombre)
```

`#999` es el asunto al que se refiere `Bug` o `Enh`.
El fichero de de registro de cambios puede de ser agrupado por tipo  (`Bug`,`Enh`) y ordenado por el número de asunto.

Para pequeños arreglos, p.e. los tipos y cambios en la documentación, no es necesario la actualización del registro de cambios (CHANGELOG).

### 8. Remite (Commit) tus cambios

Añade los ficheros/cambios que quiera remitiendo al  [área de montaje (staging area)](http://gitref.org/basic/#add) con el comando

```
git add path/to/my/file.php
```

Puedes usar la opción `-p` para seleccionar los cambios que quieres en tu envío.

Remite tus cambios con un mensaje descriptivo de envío. Asegúrate mencionar el número de ticket con `#XXX` así github puede, de forma automática, enlazar tu envío  con el ticket:

```
git commit -m "Aquí va una breve descripción de este cambio que arregla el ticket #42 "
```

### 9. Tráete el último código de Yii desde el canal de subida (upstream) en tu rama

```
git pull upstream master
```

Esto te asegura que tienes el último código en tu rama antes de abrir tu petición de extracción (pull request). Si existen algunos conflictos en la mezcla, debes arreglarlos ahora y enviar los cambios de nuevo. Esto asegura que va a ser fácil para el equipo Yii mezclar tus cambios con una sola pulsación.

### 10. Habiendo resuelto algunos conflictos, envía tu código a github

```
git push -u origin 999-el-nombre-de-tu-rama-va-aqui
```

El parámetro `-u` asegura que tu rama va a enviar y traer de la rama de github de forma automática. Si escribes `git push` permite saber, la siguiente vez, hacia donde debe enviar.

### 11. Abrir una [pull request](http://help.github.com/send-pull-requests/) en vez de un canal de subida (upstream).

Ve a tu repositorio en github y pulsa "Pull Request", escoge una rama en la parte de la derecha e introduce algunos detalles en la caja de comentarios. Para enlazar esta petición de extracción (pull request) a un asunto pon en cualquier lugar en el comentario enviado `#999` donde 999 es el número de asunto.

> Se hace notar que cada petición de extracción (pull-request) debe corregir un sólo cambio.

### 12. Alguien quiere revisar tu código

Alguien puede querer revisar tu código, y te podrían preguntar por algunos cambios, si esto oucrre ve al paso #6 (no necesitas abrir una nueva petición de extracción "pull request" si la actual continúa estando abierta). Si tu código es aceptado será mezclado en la rama principal y ser parte de la nueva edición de Yii. Si no es aceptado, no te desanimes, diferentes personas necesitan distintas opciones y Yii no puede tener todo para todos, tu código quedará todavía a disposición en github como referencia para quienes lo necesiten.

### 13. Limpiándolo

En cualquiera de los casos en los que tu código sea aceptado o no, debes borrar las ramas con las que has trabajado en tu repositorio local y `origin`.

```
git checkout master
git branch -D 999-el-nombre-de-tu-rama-va-aqui
git push origin --delete 999-el-nombre-de-tu-rama-va-aqui
```

### Nota:

Para detectar rápidamente regresiones, cada mezcla (merge) enviada al código base de Yii en github, debe de ser recogido por [Travis CI](http://travis-ci.org) para un test de ejecución automatizado. El núcleo del equipo no quiere sobrecargar este servicio, [Saltar ci `[ci skip]`](http://about.travis-ci.org/docs/user/how-to-skip-a-build/) puede ser incluido en la descripción de la mezcla si la petición de extracción (pull request):

* afecta a javascript, css o ficheros de imagen solamente,
* actualiza la documentación,
* modifica cadenas reparadas solamente (p.e. actualizaciones de traducciones)

Haciendo esto se evita a travis iniciar los tests de ejecución con los cambios que no está cubiertos por los tests en primer lugar.

> Información : Travis CI es un sistema distribuido de generación e integración contínua libre. Poermite conectar tu repositorio github y, después de cada push, regenerar le proyecto. Soporta múltiples lenguajes teniendo un runtime para cada uno de ellos.

### Resúmen de comandos (para contribuyentes avanzados)

```
git clone git@github.com:YOUR-GITHUB-USERNAME/yii2.git
git remote add upstream git://github.com/yiisoft/yii2.git
```

```
git fetch upstream
git checkout upstream/master
git checkout -b 999-name-of-your-branch-goes-here

/* haz magia, actualiza el registro de cambios si es necesario */

git add path/to/my/file.php
git commit -m "A brief description of this change which fixes #42 goes here"
git pull upstream master
git push -u origin 999-name-of-your-branch-goes-here
```
