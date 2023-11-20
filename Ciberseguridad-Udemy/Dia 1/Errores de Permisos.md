Tanto en el .ova de EducacionIT y el de Udemy de Alvaro, tenia errores de privilegios con sudo.
En uno no me dejaba escribir el comando "sudo su" porque no me aparecia nada.
Y en el otro iniciaba siempre en modo root.

En ambas maquinas lo que realice fue crear un nuevo usuario y posteriormente a ese asignarle la posibilidad de convertirse en root con usermod.

Y solucionado!!!

Los comandos que utilice fueron

*  `adduser nombre_usuario`
*  `usermod -aG sudo nombre_usuario`
