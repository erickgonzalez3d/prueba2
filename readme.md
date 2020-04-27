## curso git desde 0
flujo de trabajo en git
primero creamos y elegimos un directorio TRABAJOprincipal
lo podemos hacer manualmente o desde la terminal de git con el comando mkdir TRABAJOprincipal

con los comandos ls y cd desde la terminal de git nos ubicamos en el directorio TRABAJOprincipal

 inicializamos el repositorio en git {git init}
 (esto crea una carpeta oculta .git)dentro del directorio  con los archivos de git

 creamos o ponemos documentos, estos estan en el directorio pero no estan en el repositorio y tampoco estan trakeados.

  primero los trakeamos y despues los guardamos en repositorio

 para trakearlos hacemos un (git add <archivo>)
git
  git add . para todos los  archivos en el directorio
  git add -A para los archivos ya trakeados 
  git add *.css para los archivos con esa extensión

cuando borro un archivo del directorio que estaba en el repositorio, git nota el cambio y para borrarlo del repositorio debo hacer un git add al archivo borrado y luego un git commit para grabar el cambio 

  si queremos destrakearlo usamos un (git rm --cached <archivo>)

 luego para guardarlo en el repositorio (git commit -m "mensaje descriptivo del cambio")

para ver el cambio en un archivo uso comando (git diff) esto lo puedo hacer cuando hago un cambio en el archivo y todavia no he hecho el git add    


puedo hacer un cambio cuando el archivo esta en zona de espera o trakeado, y al hacer un git status me mostrara el archivo trakeado del ultimo git add y el archivo con  el ultimo cambio (pues no he dado git add a ese cambio) y me mostrara los dos archivos en output de consola git

Podemos decir que hay tres areas que ocupan los archivos cuando trabajamos con git

1. directorio de trabajo
2. area de preparación
3. directorio de git

git add . agrega todos los archivos del directorio de trabajo al area de preparación

para quitar el archivo de la zona de espera uso el command  "git restore --staged <archivo>-- y verifique

cuando estamos trabajando con archivos que no queramos meter en el repositorio con git . podemos usar
  git add -A
  este comando le hace un git add a todos los archivos que ya estaban trakeados  

<git log> es el comando que muestra los commit hechos hasta el momento

al hacer un git add a todos los archivos trabajados el commit guarda los cambios de todos

para cambiar el commit uso git commit --amend

para ignorar archivos y no agregarlos en los commits creo el archivos .gitignore y en el
escribo los nombres de los archivos a ignorar

si el archivo .gitignore se sigue mostrando en el git status puedo agregar el nombre .gitignore dentro del archivo con ese nombre que es el que esta diciendo a cuales ignorar

tambien podemos hacer un git add .gitignore

el comando `git log --oneline`  muestra los commits como una lista con sus titulos o mensajes

el comando `git log --graph` muestra los commit con sus ramificaciones en un grafico

se puede combinar `git log --graph` y `git log --oneline` en el comando `git log --oneline --graph`  y mostrara los titulos con grafico

puedo indicar  cuantos comits quiero ver con `git log  -5` o el numero que quiera


puedo ver los commmits ordenandolos por fecha

con el comando `git log --after="AAAA-MM-DD hh:mm:ss`

con el comando ""`git log --before="AAAA-MM-DD hh:mm:ss`"

para filtrar en un rango de tiempo podemos conbinar usando --after="AAAA-MM-DD hh:mm:ss"  --before="AAAA-MM-DD hh:mm:ss" y nos mostrara los commit hechos en dicho rango de tiempo

git commit --amend se usa para cambiar el nombre del commit, pero tambien para agregar nuevos cambios que talvez no habia hecho o que estaban en el directorio pero no estaban en zona traking cuando hice el commit ..
dd 

el git restore  saca la modificación o el archivo  nuevo del area de detección para trakeo y deja en el directorio como no rastreado 

si ya lo agregue al area de preparación con <git add .> puedo sacarlo con {`git restore --staged`} y tambien funciona `{git reset HEAD |archivo|}`

el git checkout quita los cambios que tenga el archivo en seguimiento pero se ya estan en la zona de preparación no los quita, se tendria que hacer un git `{restore --staged}` y despues el checkout 
   
## sincronizar un repositorio con github desde consola

debo crear una cuenta en gitbub y un repositorio vacio este tendra una url 

En git teniendo un directorio de trabajo con un repositorio limpio o sin cambios por añadir 
usamos el comando `git remote add origin <url_de_repositorio_github>` esto enlazara los repositorios 

luego uso el comando `git push -u origin master` para enviar los archivos de repositorio local al de la nube 

hay que tener cuidado de no hacer un push cuando ya hay un commit 

para rectificar la dirección del repositorio en github hacemos un `git remote remove origin` 


--- 

### este es el cambio de desktop

   
   # TRABAJO CON GITHUB DESKTOP
      
      Instalo el programa en la maquina e inicio sesión de github en el luego puedo clonar el repositorio en una ruta local 

cuando hago un cambio en uno o mas archivos del repositorio, github desktop lo detecta 

tambien puedo crear el repositorio directamente desde l a interfaz de github, con la opción de `add repository` y eligiendo un directorio con archivos para subir o con la opcion de crear 

puedo hacer cambios desde la web github y despues sincronizarlos con el repositorio local 
para esta debo hacer un pull y push 

creo una rama cuando quiero hacer cambios a los archivos sin modificar la rama master luego comparo la rama master con la rama que modifique y hago un merge de los cambios hacia master y despues puedo borrar la rama que no necesito

## clonar un repositorio
ubicado en el directorio de trabajo uso el comando `git clone <url_del_repositorio_github> nombreQueQuiero`
a diferencia de descargar el repositorio, el git clone trae una copia del repositorio con todo su historial 

al hacer un `git log -- decorate --oneline --graph --all` me muestra un arbol de los commit con todas las ramas  

puedo ver las diferencias entre un commit y otro con sus numeros `git diff 17dc8c0 18dc8c0` 

para ir a un cambio en el tiempo uso el comando `git checkout <numeroDelCommit>` despues de esto al hacer un `git status` me indicara que el <HEAD> lo saque del commit master y esta en el actual commit 

<HEAD> representa el punto en el tiempo donde estamos ubicados, con el comando `git checkout` cambiamos en el tiempo si queremos volver al ultimo commit uso el `git checkout master` 

   
   ## etiqueta git tag
para marcar un punto en la historia del proyecto o una versión que estaba corriendo muy bien 
el comando `git tag` me permite ver las etiquetas que hay 
existen las etiquetas ligeras y las etiquetas anotadas 
ligeras 
las ligeras son un nombre, identificador, o marca que le ponemos a un commit se hace con el comando 
`git tag nombreEtiqueta`    -->> esto agrega el tag al ultimo commit hecho

le puedo poner etiquetas a cualquier punto de la historia 
las etiquetas anotadas sirven como un identificador mas preciso de un commit, como para establecer una versión ya que queda registrado el nombre del que hizo el tag y un mensaje adicional al propio del commit 







