PREGUNTAS 

1.	¿Por qué el segundo push del apartado 2.2 fue rechazado? ¿Qué dos operaciones hace git pull por debajo?
•	Cuando el miembro B (isaac) hizo su push, se subió correctamente a GitHub.
•	Cuando el miembro C (Xavi) Intento hacer su push el servidor lo rechazó porque ya se había hecho la sincronización con la rama de Isaac, el repositorio de xavi estaba desactualizado, lo que debería haber hecho xavi era hacer pull de su rama primero para tener todos los cambios actualizados en la su rama local antes de hacer el push final a main.

•	git-fetch  Se conecta al repositorio remoto , descarga todas las nuevas ramas actualizando las referencias remotas (como origin/main).
•	git-merge  Fusiona cambios recién descargados del remoto con tu rama local actual.

2.	En vuestro historial, señalad un merge fast-forward y un merge commit. ¿Qué los diferencia?
Fast-Forward, en la actividad 2.2 ya que hemos hecho commit y push desde main
Merge commit, actividad 2.4, ya que cada uno hace un commit y push desde su propia rama creada.

3.	¿Por qué rellenar filas distintas de la tabla no dio conflicto y cambiar Última revisión sí?
•	Porque al cambiar diferentes líneas de un mismo archivo no interfiere a la hora de realizar el “git push”, ya que el error proviene cuando editas una misma línea del mismo archivo ya que la información se solapa y para corregir el error tienes que seleccionar manualmente lo que quieres dejar. 

4.  Pegad el mensaje de error del push a main protegida y explicad qué regla lo ha bloqueado.

    - Este es el error que aparece a la hora de hacer push:

        - error: failed to push some refs to ‘https://github.com/isainrono/grupo2Stucom.git’

    - Esta es la regla creada que ha ocasionado el bloqueo: 
    
        - Block force pushes ()

5.  ¿Qué comando sacó .env del control de versiones sin borrarlo? ¿Por qué la contraseña sigue siendo un
problema y qué haríais en un proyecto real? (Pista: la respuesta empieza por lo
que hay que hacer con la contraseña, no con el historial.)

    - el comando es git rm --cached .env

        - git rm → Esto lo que hace es decirle a git que deje de hacer seguimiento del fichero

        --cached → Esto solo asegura que lo borra del índice de GIT (Control de Versiones) pero igual sigue en acceso desde local.

    - La contraseña sigue siendo un problema ya que al subirse así sea por unos segundos, esta contraseña
    ya está comprometida, ya aparece en el historial de versiones, por lo que el
    proceso a seguir de manera inmediata es revocar, cambiarla o invalidarla, creer
    que al ser solo por unos segundos nadie la ha visto es un riesgo que no se
    puede correr.

    - Al GIT ser un sistema de control de versiones, por más que en el último commit se elimine el archivo .env en los commit anteriores se podrá ver, y si alguien a clonado el repositorio o ha hecho una rama de commits anteriores bastaría con buscarlo con un comando como git log -p para examinar el historial y encontrarlo fácilmente.

6.  ¿Qué hace mejor GitHub Desktop que la terminal, y qué no puede hacer? ¿Con cuál habéis entendido mejor el conflicto?

    - Permite ver de manera más limpia los cambios realizados.
    - Las lineas que se han añadido de color verde
    - Las lineas que se han borrado de color rojo esto permite que los cambios sean más intuitivos antes de hacer un commit.
    - Se pueden marcar bloques o líneas de código para hacer un commit, esto es mucho más visual y práctico que hacerlo mediante terminal con git add -p.
    - Puedes ver de manera más visual y gráfica, las ramas que tienes, en qué rama te encuentras, y los cambios que se tienes sin guardar sin necesidad de ejecutar comando como git branch.

    - Que no se puede hacer con Desktop:

        – Crear reglas de protección de ramas
        – Configurar webhooks
        – Cambiar permisos avanzados de los miembros
del repositorio (Es obligatorio hacer desde la terminal grafica web de github)
        – Operaciones complejas de github

    - La mejor manera de entender los conflictos fue con los marcadores explícitos, es una manera muy visual que tiene github de mostrar los conflictos entre autores, además que resalta a la vista cuando un trozo de código empieza y termina de cada autor.

        – Marcadores explícitos <<<<<<<, =======, >>>>>>>

7. Roles: ¿qué puede hacer un Maintain que no pueda un Write? ¿Quién podría haber quitado la protección de main?
 
El rol de Maintain tiene privilegios casi administrativos entre ellos:

– Modificar configuración general del repositorio (Nombre, Visibilidad, Descripción)

– Puede añadir, eliminar o modificar los permisos de otros miembros dentro del repositorio

– Puede configurar servicios externos, webhooks y herramientas conectadas al repositorio.

– Tiene mayor control sobre la gestión de ramas y flujos de trabajo.

– El Rol de write está supeditado a leer, escribir código, abrir Pull Requests y hacer    fusiones permitidas.

Los roles de Maintain y Write no tienen permisos para modificar o desactivar reglas de protección de la rama main, por lo que el único que podia quitar la protección de main era el
admin, o en su defecto los usuarios con propiedad de owner.

8. Si mañana un miembro sube un force push a main, ¿qué se pierde y qué lo impide en vuestro repositorio?

“git push --force” reescribe todo el historial del repositorio con tu rama local si se hace desde main, eso quiere decir que todo el trabajo o commit hecho por otros colaboradores se perderá en el caso de que la rama local de quien lo haga no esté actualizada con los cambios de los demás colaboradores.

En nuestro caso lo impide las reglas que ha declarado el administrador cuando se protege la rama main, estas son.

– La prohibición explícita de force push

– La prohibición de push directo

9. En la Fase 1 compartíais un portátil y en la Fase 2 cada uno tenía el suyo. ¿Qué diferencia práctica tiene eso para la identidad del autor de cada commit y para cómo aparecen los conflictos?

Al trabajar tres personas desde un mismo equipo en local teníamos que usar el comando:

git config --globaluser.name "nombre del miembro"

git config --globaluser.email "correo del miembro"

Para así poder dejarregistro de quién realizaba los cambios pertinentes dentro de los documentos.

Al trabajar en local no había ningún problema a la hora de realizar ningún “git push” ya que no hay ninguna incompatibilidad entre los ficheros, los problemas vienen a la hora de trabajar cada uno con su equipo, ya que realizamos “git push” donde hay archivos y líneas que hemos editado todos y ahí es donde dan los problemas.