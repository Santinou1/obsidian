La herramienta DIRB , va a reconocer a traves de un ataque de diccionario, cada uno de los directorios escondidos del servidor web.

Si queres visualizar el manual ejecuta el siguiente comando.

```sh
man dirb
```


El codigo para ejecutar el escaneo de los directorios es

```sh
dirb http://192.168.0.247/ -o directorios.txt
```

La flag -o la utilizo para guardar la data en un txt.