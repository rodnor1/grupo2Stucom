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
