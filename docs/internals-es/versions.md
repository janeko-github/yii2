Versionado Yii 
==============

Este documento sumariza la política de versionado de Yii. En general, Yii sigue la [Semántica de Versionado](http://semver.org/).

## Lanzamientos (release) parches `2.x.Y`
 
* Mantenidos en una rama llamada `2.x`
* principalmente contiene arreglos de errores y nuevas características menores
* Sin nuevas características importantes.
* ha de ser 100% hacia atrás compatible (**BC** **B**ackward **C**ompatibility) para asegurar una actualización libre de problemas. Con la única excepción de asuentos de seguridad que pueden requerir  ruptura de compatibilidad hacia atrás.
* El ciclo de lanzamientos es alrededor de  1 a 2 meses.
* No son necesarios prelanzamientos (alpha, beta, RC).
* Han de ser mezclados con la rama maestra constantemente (manualmente al menos una vez a la semana).


## Lanzamientos menores `2.X.0`

* Desarrollados en la rama maestra
* Principalmente contine nuevas carcaterísticas y errores corregidos
* Contine características menores y errores corregidos mezclados desde parches publicados
* Puede contener problemas de compatibilidad hacia atrás cuyos cambios son grabados en el fichero `UPGRADE-2.X.md`
* El ciclo de lanzamiento es alrededor de 6 a 8 meses
* Necesita de los prelanzamientos: `2.X.0-alpha`, `2.X.0-beta`, `2.X.0-rc`
* necesita nuevos lanzamientos superiores y un esfuerzo de marketing.


## Lazamientos superiores `X.0.0`

Nada planificado. 
