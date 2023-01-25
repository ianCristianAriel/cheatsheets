<!-- Inicializacion de seguimiento de una carpeta por parte de git -->
git init 

<!-- Crea un proyecto con un nombre espesificado -->
git init [aca va el nombre]

<!-- Agregar archivos de la carpeta al area de ensayo local. Se debe utilizar siempre antes de hacer un commit, por ejemplo tambien cuando un archivo
del area de ensayo local sufre modificaciones -->
git add (aqui va el nombre del archivo)
<!-- Agrega al area de ensayo todos los archivos de la carpeta -->
git add .

<!-- Muestra las diferencias del archivo entre el área de espera y la última versión del archivo -->
$ git diff --staged

<!-- Guarda los archivos que se encontravan en el area de ensayo local en el repositorio local -->
git commit
<!-- Agrega una descripcion entre las comillas -->
git commit -m "" 

Mueve el archivo del área de espera, pero preserva su contenido
$ git reset [file]

<!-- Muestra el estado de los archivos de la carpeta que no se les esta haciendo seguimiento o no se le guardaron cambios -->
git status -s

<!-- Muestra los commits realizados, con su id -->
git log --online

<!-- Restaura los archivos de la carpeta en seguimiento a un commit anterior -->
git reset --hard (aqui va el codigo del commit)

<!-- Consola VIM, modifica commits realizados (descripcion, etc) -->
git commit --amend

<!-- Sube los commits a un repositorio en github -->
git remote add origin (aqui va el link que te proporciona github cuando se crea el repositorio)

<!-- Actualiza los comits del repositorio remoto -->
git push -u origin master

<!-- Trae los commits realizados en remoto al repositorio local -->
git pull

<!-- Guarda el rpoyecto en una determinada version -->
git tag (aqui va la fecha y la version por convencion) -m "(aqui va la descripcion)"

<!-- Descarga los archivos del repositorio remoto -->
git clone (aqui va el codigo de descarga que proporciona github dentro de la carpeta del proyecto, cliqueando el boton "code")

<!-- Crea una rama en paralelo, la cual contara con los commits de la rama de la cual se creo -->
git branch (aqui va el nombre de la rama)

<!-- Muestra las ramas disponibles (muestra con un asterisco y en verde la rama que se esta utilizando)-->
git branch

<!-- Se crea una rama y se selecciona para empezar a trabajar -->
git checkout -b "[aqui va el nombre de la rama]"

<!-- Se hace un comit y se envia la rama al repositorio remoto  -->
git push origin [nombre de la rama modificada]

<!-- Se selecciona una de las ramas disponibles para trabajar -->
git checkout (aqui va el nombre de la rama)

<!-- Utilizando la rama master la fuciona con una rama que se le espesifique -->
git merge (aqui va el nombre de la rama)

<!-- Elimina una rama en espesifico -->
git branch -d (aqui va el nombre de la rama)

<!-- Desecha todo el historial y regresa al commit especificado -->
$ git reset --hard [commit]

<!-- Estos codigos se pueden introducir desde gitbash como desde el terminal de vsc -->
