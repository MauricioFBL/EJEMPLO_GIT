# GIT

```
git log --oneline - Te muestra el id commit y el título del commit.
git log --decorate- Te muestra donde se encuentra el head point en el log.
git log --stat - Explica el número de líneas que se cambiaron brevemente.
git log -p- Explica el número de líneas que se cambiaron y te muestra que se cambió en el contenido.
git shortlog - Indica que commits ha realizado un usuario, mostrando el usuario y el titulo de sus commits.
git log --graph --oneline --decorate y
git log --pretty=format:"%cn hizo un commit %h el dia %cd" - Muestra mensajes personalizados de los commits.
git log -3 - Limitamos el número de commits.
git log --after=“2018-1-2” ,
git log --after=“today” y
git log --after=“2018-1-2” --before=“today” - Commits para localizar por fechas.
git log --author=“Name Author” - Commits realizados por autor que cumplan exactamente con el nombre.
git log --grep=“INVIE” - Busca los commits que cumplan tal cual está escrito entre las comillas.
git log --grep=“INVIE” –i- Busca los commits que cumplan sin importar mayúsculas o minúsculas.
git log – index.html- Busca los commits en un archivo en específico.
git log -S “Por contenido”- Buscar los commits con el contenido dentro del archivo.
git log > log.txt - guardar los logs en un archivo txt
```

- inicializar git

```git init ```

- Estatus del proyecto

```git status   ```

- Añadir archivos para ser enviados

```git add archivo.algo```

- Sacar de envio 

```git rm archivo.algo```

- quitar de memoria ram

```git rm --cached archivo.algo```

- Configuracion de usuario

```git config --global user.name "Mauricio Bautista"```

```git config --global user.email Mauricio.Bautista@dentsu.com```

- listar Configuracion

```git config --list```

- Añadir todos los archivos de una carpeta

```git add .```

- Subir completamente archivos de carpeta

```git commit -m ""```

-revision estatus del repo

```git status```
- ver historial de cambios de un archivo

```git log archivo.algo```

- muestra diferencia entre version anterior y version nueva

```git show .\algo.txt```

- ESC SHIFT ZZ

```git commit```

- comparar contenido de acuerdo indices de comit

```git diff 07c6676d979928f924dc284f35f3f51f33e1a804 ee2fc3536aa3b4bc267f3155423ac202d72d386e```

- git diff archivo indicecomitcomparar indicecomparador

__________________________________________________________________
## EXISTEN 3 AREAS DIFERENTES EN git

![git areas](https://res.cloudinary.com/practicaldev/image/fetch/s--M_fHUEqA--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amazonaws.com/i/128hsgntnsu9bww0y8sz.png "a title")


## UNTRACKED AREA (Working directory)
    git no sabe que existe


## STAGGING AREA 
    AREA EN MEMORIA RAM  DESCONECTADA DE TODO

```git add```

## Repositorio (master)

    Donde se llega la ultima version


```git commit```

__________________________________________________________________

- REINCIAR COMPLETAMENTA VERSION ELEGIDA DE COMMIT

- elimina todo el historia de commita

```git reset id_cambio --hard```

__________________________________________________________________

```git reset id_cambio --soft```

- mostrar cambios de todos los archivos

```git diff```

- ver el cambios especificos de cada archio

```git log --stat```

- Regresar auna version del archivo sin cambiar en master

```git checkout indice_commit archivo.algo```

- Regresar a master despues de un checkout sin commit

```git checkout master archivo.algo```

- Realizar un commit sin hacer git add

```git commit  -am "commit correciondel contenedor"```

git commit  -a

- revisar donde esta la cabecera y uñtimos cambios

```git log --stat```

- Crear una nueva rama

```git branch cabecera```

- Mover la cabecera a otra rama

```git checkout rama```

- Mover caberea a master

```git checkout master```

- Para hacer un merge se debe estar en la rama principal y despues hacer merge en este caso

```git checkout master```

```
git branch
git merge cabecera
git status
```
- Para hacer un merge cuando hay error hay que revisar las partes que se deciden quedar o eliminar

```git checkout master

git branch
git merge cabecera
git status
|Solucionar conflicto de versiones|
git merge cabecera
```

Git reset y git rm son comandos con utilidades muy diferentes, pero aún así se confunden muy fácilmente.

``git rm``

Este comando nos ayuda a eliminar archivos de Git sin eliminar su historial del sistema de versiones. 
Esto quiere decir que si necesitamos recuperar el archivo solo debemos “viajar en el tiempo” y recuperar el último commit antes de borrar el archivo en cuestión.

Recuerda que git rm no puede usarse así nomás. Debemos usar uno de los flags para indicarle a Git cómo eliminar los archivos que ya no necesitamos en la última versión del proyecto:

``git rm --cached``: 

Elimina los archivos del área de Staging y del próximo commit pero los mantiene en nuestro disco duro.
git rm --force: Elimina los archivos de Git y del disco duro. Git siempre guarda todo, por lo que podemos acceder al registro de la existencia de los archivos, 
de modo que podremos recuperarlos si es necesario (pero debemos usar comandos más avanzados). 

``git reset``

Este comando nos ayuda a volver en el tiempo. Pero no como git checkout que nos deja ir, mirar, pasear y volver. 
Con git reset volvemos al pasado sin la posibilidad de volver al futuro. Borramos la historia y la debemos sobreescribir. No hay vuelta atrás.

Este comando es muy peligroso y debemos usarlo solo en caso de emergencia. Recuerda que debemos usar alguna de estas dos opciones:

Hay dos formas de usar git reset: con el argumento --hard, borrando toda la información que tengamos en el área de staging (y perdiendo todo para siempre). 
O, un poco más seguro, con el argumento --soft, que mantiene allí los archivos del área de staging para que podamos aplicar nuestros últimos cambios pero desde un commit anterior.

``git reset --soft``: 

Borramos todo el historial y los registros de Git pero guardamos los cambios que tengamos en Staging, así podemos aplicar las últimas actualizaciones a un nuevo commit.
git reset --hard: Borra todo. Todo todito, absolutamente todo. Toda la información de los commits y del área de staging se borra del historial.
¡Pero todavía falta algo!

``git reset HEAD``: 

Este es el comando para sacar archivos del área de Staging. No para borrarlos ni nada de eso, solo para que los últimos cambios de estos archivos no se envíen al 
último commit, a menos que cambiemos de opinión y los incluyamos de nuevo en staging con git add, por supuesto.
¿Por qué esto es importante?
Imagina el siguiente caso:

Hacemos cambios en los archivos de un proyecto para una nueva actualización. Todos los archivos con cambios se mueven al área de staging con el comando git add. Pero te das cuenta de 
que uno de esos archivos no está listo todavía. Actualizaste el archivo pero ese cambio no debe ir en el próximo commit por ahora.

¿Qué podemos hacer?

Bueno, todos los cambios están en el área de Staging, incluido el archivo con los cambios que no están listos. Esto significa que debemos sacar ese archivo de Staging 
para poder hacer commit de todos los demás.

¡Al usar git rm lo que haremos será eliminar este archivo completamente de git! Todavía tendremos el historial de cambios de este archivo, 
con la eliminación del archivo como su última actualización. 
Recuerda que en este caso no buscábamos eliminar un archivo, solo dejarlo como estaba y actualizarlo después, no en este commit.

En cambio, si usamos git reset HEAD, lo único que haremos será mover estos cambios de Staging a Unstaged. 
Seguiremos teniendo los últimos cambios del archivo, el repositorio mantendrá el archivo (no con sus últimos cambios pero sí con los últimos en los que hicimos commit) 
y no habremos perdido nada.

Conclusión: Lo mejor que puedes hacer para salvar tu puesto y evitar un incendio en tu trabajo es conocer muy bien la diferencia y los riesgos de todos los comandos de Git.

## RAMAS EN GIT
### Cambio de rama
``git branch nombre_rama``
### Cambio de rama
``git checkout nombre_rama``
### Mostrar las ramas  
``git branch``
### Ver las rams y su historia
``git show-branch``
### Ver las ramas y su historia con mas detalle
``git show-branch --all``

# ALIAS 
git config  alias.arbolbonito "log --graph --abbrev-commit --decorate --date=relative --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"

git arbolbonito

# TAGS
```
git tag -a version -m "mensaje" ubicacion
git tag -a v0.2 -m "resultado primeras clases git" 930a6a2
```
# ver los tags
```
git tag
```
# ver los tag y suasosiacion
```
git show-ref --tags
```
# CARGAR TAGS
```
git pull origin master
git push origin --tags
```
## ELIMINAR TAG
```
git tag -d dormido
git push origin :refs/tags/dormido
```

## Generar una nueva llave SSH: (Cualquier sistema operativo)

``ssh-keygen -t rsa -b 4096 -C "youremail@example.com"``

## Comprobar proceso y agregarlo (Windows)
```
eval $(ssh-agent - s)
ssh-add ~/.ssh/id_rsa
```







