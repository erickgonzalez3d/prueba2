## cusrso git desde 0
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