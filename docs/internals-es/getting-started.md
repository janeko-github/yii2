Comenzando el desarrollo con Yii2
=====================================

1. Clona tu rama (fork) de yii2 `git clone git@github.com:<yourname>/yii2.git`.
2. Cambia al directorio del repositorio `cd yii2`.
3. Ejecuta `./build/build app/link basic` para instalar las dependencias con composer para la aplicación básica.
	Este comando puede instalar paquetes externos de composer con normalidad pero también puede enlazar el actual repositorio de yii2 al repositorio actual donde estés situado (checkout), donde tienes una instancia de todo el código instalado.
4. Hacer lo mismo para la aplicación avanzada si es necesario: `./build/build app/link advanced`
   Este comando también puede ser usado para actualizar dependencias, pues ejecuta internamente `composer update` .
5. Ahora ya tienes tu zona de trabajo para el desarrollo (playground) y  poder modificar las capacidades de Yii 2.

Puedes también añadir el canal del repositorio de yii2 para enviar los cambios con el nombre upstream:

```j
git remote add upstream https://github.com/yiisoft/yii2.git
```
> Información: Composer es una herramienta para administración de dependencias en PHP

Por favor, refiérase a [Diagrama de flujo para los contribuyentes de Yii2](git-workflow.md) para los detalles de como crear un petición de envío de cambios (pull requests).

Tests unitarios
----------

Para ejecutar los tests unitarios tienes que instalar los paquetes de composer para el repositorio dev-repo.
Ejecuta `composer update` en el directorio raiza del repositorio para obtener los últimos paquetes.

Puedes ahora ejecutar los tests unitarios ejecutando `phpunit`.

Puedes limitar los tests a un grupo de tests con los que estés trabajando.. p.e. para ejecutar solamente los tests para los validadores y redis
`phpunit --group=validators,redis`.

Extensiones
----------

Para trabajar con extensiones debes instalarlas en la aplicación donde quieras probarlas.
Sólo añádelos al fichero `composer.json` como haces normalemente p.e. añadir `"yiisoft/yii2-redis": "*"` a la sección `require` de la aplicación básica.
Ejecutando `./build/build app/link basic` vas a instalar la extensión con sus dependencias y crear un enlace simbólico a `extensions/redis` de modo que no estás trabajando con el directorio del proveedor de servicios de composer (vendor) si no que trabajas con el repositorio de yii2 directamente.

Tests funcionales y de aceptación para las aplicaciones
------------------------------------------------

Mira `apps/advanced/tests/README.md` y `apps/basic/tests/README.md` para aprender sobre como ejecutar los tests de Codeception.

> Información: Codeception es un en una infraestructura (framework) que nos permite crear y ejecutar pruebas unitarias así como realizar test sobre interfaces de usuario.
