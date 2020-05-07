###### copia rama <nueva>
# curso git desde 0

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
  git add *.css para los archivos con esa extensión*

cuando borro un archivo del directorio que estaba en el repositorio, git nota el cambio y para borrarlo del repositorio debo hacer un git add al archivo borrado y luego un git commit para grabar el cambio

  si queremos destrakearlo usamos un (git rm --cached <archivo>)

 luego para guardarlo en el repositorio (git commit -m "mensaje descriptivo del cambio")

puedo ahorrarme el commando de git add agregando parametros al comando commit el -a agragara el archivo a la zona de preparación -m el mensaje y los puedo unir y funcionan igual  -am  seria `git commit -am "mensaje" `

para ver el cambio en un archivo uso comando (git diff) esto lo puedo hacer cuando hago un cambio en el archivo y todavia no he hecho el git add    


puedo hacer un cambio cuando el archivo esta en zona de espera o trakeado, y al hacer un git status me mostrara el archivo trakeado del ultimo git add y el archivo con  el ultimo cambio (pues no he dado git add a ese cambio) y me mostrara los dos archivos en output de consola git

Podemos decir que hay tres areas que ocupan los archivos cuando trabajamos con git

1. directorio de trabajo
2. area de preparación
3. directordddio de git

git add . agrega todos los archivos del directorio de trabajo al area de preparación

para quitar el archivo de la zona de espera uso el command  "git restore --staged <archivo>-- y verifique

cuando estamos trabajando con archivos que no queramos meter en el repositorio con git . podemos usar
  git add -A
  este comando le hace un git add a todos los archivos que ya estaban trakeados  

<git log> es el comando que muestra los commit hechos hasta el momento,
cuando agrego --decorate me resalta la información principal del commit
si agrego --all me muestra todos los commits aunque esten por delante en el tiempo
--oneline me mostrara una solo linea con el commit
--graph muestra un mapa en codigo como ayuda grafica

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

para filtrar en un rango de tiempo podemos combinar usando --after="AAAA-MM-DD hh:mm:ss"  --before="AAAA-MM-DD hh:mm:ss" y nos mostrara los commit hechos en dicho rango de tiempo

git commit --amend se usa para cambiar el nombre del commit, pero tambien para agregar nuevos cambios que talvez no habia hecho o que estaban en el directorio pero no estaban en zona traking cuando hice el commit ..
dd

el git restore  saca la modificación o el archivo  nuevo del area de detección para trakeo y deja en el directorio como no rastreado

si ya lo agregue al area de preparación con <git add .> puedo sacarlo con {`git restore --staged`} y tambien funciona `{git reset HEAD |archivo|}`

el git checkout quita los cambios que tenga el archivo en seguimiento pero si ya estan en la zona de preparación no los quita, se tendria que hacer un git `{restore --staged}` y despues el checkout
porque es como saltar a otra rama sin haber guardado, pero esta en commits 

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
git tag lista las etiquetas en orden alfabetico
para marcar un punto en la historia del proyecto o una versión que estaba corriendo muy bien
el comando `git tag` me permite ver las etiquetas que hay, las ordena en orde alfabetico
existen las etiquetas ligeras y las etiquetas anotadas
ligeras
las ligeras son un nombre, identificador, o marca que le ponemos a un commit se hace con el comando
`git tag nombreEtiqueta`    -->> esto agrega el tag al ultimo commit hecho

le puedo poner etiquetas a cualquier punto de la historia

las etiquetas anotadas sirven como un identificador mas preciso de un commit, como para establecer una versión ya que queda registrado el nombre del que hizo el tag y un mensaje adicional al propio del commit
-para una atiqueta anotada `git tag -a <nombre> -m "mensaje"`

para ver abrir las etiquetas despues de un `git tag` usamos `git show <nombreDeEtiqueta>` y mostrara el commit completo con la etiqueta, tambien con un git log el commit se vera identificado con la etiqueta

para crear una etiqueta en un punto de la historia que no sea el HEAD uso el comando de la etiqueta + el numero de identificacion o marcado del commit `git tag <nombreEtiqueta> (1numerocommit23456)` el {numero del commit =o= SUMA DE COMPROBACIÓN} puede ser la version larga o la version corta

Puedo filtrar las etiqueta en comun como por ejemplo las versione v1, v1.2, v1.3.... agregando el parametro -l o --list al comando de esta forma `git tag -l "v1.*"` y me listara los tag que empiezan por v1.

asi como borro las ramas tambien puedo borrar las etiquetas con el comando `git tag -d nomEtiqueta`

y al igual que las ramas cuando se borra lo que eliminamos es el apuntador del commit pero no borramos el commit en si ya que este hace parte del historial de modificación


# ramas


Master es el nombre de un apuntador a la rama, asi como las etiquetas son apuntadores a los commits , master es un nombre por defecto pero podemos cambiarlo y no necesariamente tiene que ser la rama principal  
este apuntador o rama es movil se desplaza al ultimo commit

varia ramas o branches pueden estar apuntando a un mismo commit o punto en el tiempo
para ver la especificación tecnica usamos `git branch --help`

con el comando `git branch` se listan las ramas que hay en el repositorio

para crear una rama usamos el comando `git branch + nombreRama` desde cualquier rama donde estemos

para movernos entre los branch usamos el comando `git checkout nobreRama` cuando ejecutamos este comando el apuntador del `git log indicara la rama donde este asi HEAD -> rama, debemos tener en cuenta que cuando se crea el branch no se modifica la posición del head, solo hasta ejecutar el checkout

el directorio de trabajo debe estar limpio cuando cambiemos de rama o podriamos perder los cambios que aun no esten añadidos

podemos estar en un commit al que esten apuntando varias ramas  pero el HEAD  indicara a cual esta afectando los commits que hagamos  

al cambiar de branch y empezar a generar commits el HEAD va a continuar por el camino de ese branch dejando atras en el tiempo la rama desde la cual fue creada la actual

las ramas  apuntan al commit del momento en que creamos la rama y de hay en adelante al ultimo commit de la misma

si me devuelvo en el historial desde una rama alterna a un commit anterior del cual inicio esa rama no estare en esa rama

no hay un limite en la cantidad de ramas a crear

la rama master esta por defecto pero si se sigue deserrollando a lo largo de una rama esa podria ser la rama principal <cualquier rama puede ser la principal>


tambien puedo generar commit en las distintas ramas y estas tomaran su propio camino

puedo ver las ramas oculta con git branch --all y me mostrara la ramas que hay tanto el local como en linea

# fusion de ramas



para fusionar ramas se usa el comando `git merge`

primero verificamos en que rama estamos ubicados con el HEAD `git status` o con `git branch` este ultimo lo mostrara marcado y si usamos el `git branch -v` muestra el ultimo commit que hay en cada rama

no necesariamente tenemos que fusionar la rama con la mas cercana podemos hacerlo con cualquier otra

### git merge 

primero tenemos que ubicarnos en la RAMA DESTINO y ejecutamos el comando git merge <rama a fusionar>




` git push --set-upstream origin ramacon` este comando configura la rama actual como la que va a hacer los push al repositorio remoto

cuando fusionamos una rama y tiene conflictos con la actual debemos arreglar esos conflictos o añadirlos automaticamente y luego hacer un commit que confirme ese merge, en el apuntador del HEAD se mostrara el mensaje  <rama|MERGING> que indica que se esta haciendo  la corrección para el completar el merge con un commit, esto pasa cuando en dos ramas modificamos las mismas lineas de los archivos git mostrara un menseje asi en esas lineas de los archivos en conflicto

(>>>->>>->>>> ) HEAD Aca estaran las modificaciones en la rama actual
estan en el mismo numero de linea que en la otra rama
(=========)
cambios en la otra rama en las mismas lineas  
puedo borrar algunas lineas de cada rama o quedarme con todas y borro los simbolos de git
(->>>>)
-(-=====)
-(<-<<<<<)

  -1(<<<) (rama que le estoy haciendo merge)

para borrar una rama o branch uso el comando `git branch -d <nombre de la rama>`, si la rama no ha sido fusionada git no dejara eliminarla con este comando hasta que se fusionen los cambios  

para forzar la eliminacion de una rama usamos el comando `git branch -D rama` destacar que la de es mayuscula , este comando tiene el riesgo de borrar cambios que no hallamos incluido en la rama principal


el comando `git branch --no-merge` me indica cual rama no ha sido fusionada a la rama actual y si es un cambio que deseo eliminar y no fusionar con el proyecto puedo eliminarla con branch -D

el comando `git branch --merge` me muestra las ramas que esta fusionadas con la actual

si quiero ver los cambios que tiene otra rama con respecto a la actual utilizo el comando `git show otraRama` me mostrara un equivalente al `git diff` pero este aplicado a ramas

### git branch --no-merged
el comando me muestra en terminal la ramas que no estan fusionadas 


#### volver a un rama eliminada

si elimino una rama y quiero volver a trabajar en ella , puedo ir al ultimo commit que hubo en esa rama con un `git checkout <numCommit> `y crear un rama
indicandole que vamos a saltar a ella desde la actual con el comando `git checkout -b (nomRamarestaurada)`, despues de ejecutar este comando el  HEAD va a estar ubicado en la rama restaurada, desde hay puede seguir el desarrollo de la restaurada y volver a la rama master cuando quiera

# github

es una red social para compartir codigo, corregirlo o colaborar con otros proyectos atravez de repositorios

git remote add origin <url repositorio> nos conecta a el repositorio con esa url  y lo sincronizamos con nuestro repositorio local con `git push -u origin master`

si git no deja hacer un push a repositorio web podemos intentar cambiando el email y usuario por el de la cuenta en github, lo podemos ver con `git config --global --list` y si observo el local `git config --local --list` vemos la configuración de ese repositorio en especifico y debe tener una linea que indique el repositorio al que esta enlazado  

 remote.origin.url=https://github.com/ErickGonzalez3d/prueba2.git

SI NO estan conectados configuramos de nuevo el correo y el usuario de git con
`git config user.email "email" --global`  
`git config user.name "nombre" --global`

luego de esto probamos hacer un `git push -u origin` y  ya deberian sincronizarse el repositorio local y el de la nube de github

al estar sincronizados puedo subir archivos en el desde el directorio de trabajo y el consola debe aparecer un mensaje en una nueva linea de `git status` indicando que esta actualizado con origin/master

despues de sincronizados se crea la rama "oculta" origin/master, esta sera la rama de el repositorio que no se mostrara en el git branch
para ver esa rama  oculta `git branch --all`

de nuevo si hago cambios y los confirmo con commits y veo el `git status` me muestra una linea informando que hay commits que no estan el la rama origin/master por lo tanto no estan actualizados con el repositorio en la nube

Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

este seria el mensaje , que estamos por delante de la rama origin/master por el numero de commit y que hagamos un git push para publicar nuestros commits locales

### traer cambios de github al repositorio local

si quiero traer un repositorio de otra persona desde github hago un fork
al hacer un fork es como si estuviese haciendo una rama del repositorio de esa persona, que va a estar en nuestro repositorio en la nube o sea creo un repositorio propio de ese proyecto
luego puedo trabajar en el proyecto en linea en la web de github o puedo traer ese repositorio de la nube a un directorio de trabajo local al hacer un `git clone <urlDelRepositorio>` ,
esto crea un directorio de trabajo con el repositorio iniciado
se clona el estado actual de ese repositorio en su rama principal  y su historia.  NO traemos las otras ramas que tenga esa otra persona

verificamos que estemos vinculados al repositorio con 
`git config --local --list` el remote.origin.url=dirección-del-repo
el usuario y correo con `git config --global --list`
el user.name y user.email=correoCuentaGithub
desde este punto podemos modificar los archivos como veniamos trabajando haciendo adds y commits podemos crear ramas ya el repo es nuestro


al crear otra rama y hacer commits usamos <git push origin rama> y en el repositorio de github se creara la rama donde estamos trabajando y se subira con los cambios del ultimo comit,  estaran sincronizadas tanto en local como remoto...... de ocurrir un erro lo mas probable es que el usuario de github no sea el que tengamos comfigurado en el repositorio local 


de nuevo para crear un repositorio en github a partir de un directorio de trabajo local en github usamos la opción nuevoRepositorio y generamos la <url del repositorio de github>


cambio prueba 

luego en consola ubicados en el directorio del repositorio local viculamos al remoto
{git remote add origin <url del repositorio de github> }


en este punto estan vinculados pero NO sincronizados, pues para sincronizarlo necesitamos hacer un 
`git push -u origin master` y se enviaran los archivos locales a el repositorio en la nube , despues de eso el remoto sera el mismo que el local, puedo seguir modificando los archivos locales y se sincronizaran cada vez que haga un push 

## realizar aportes 
para aportar debo hacer un fork del proyecto original, clonarlo localmente y crear una rama para trabajar en ella.
al hacer un push de nuevo `git push origin ramaNueva` 

luego de esto verifico el user.name y user.email si no lo tengo configurado me saltara una ventana de confirmacion para la contraseña de github, la ingreso y ya estara vinculada y podre hacer el <git push origin ramaNueva> y los cambios que relice estan en esa rama del repositorio remoto 

cuando hago este push puede que me salte el error de que no tengo acceso desde el usuario actual ,
verifico el user.name y el user.email sean la misma cuenta del repositorio que estoy usando en github con 
git config --global -l 
git config --local -l 
y los cambio con 
git config user.name "usuario" --global 
git config user.email "mail" --global 

si esto no funciona puedo configurar dos usuarios eliminando las credenciales y configurando los usuarios por repositorios 

para realizar el aporte en github me situo en la rama que desarrolle y hago un pull request hacia la rama del editor original 

## Configurar usuarios en windows 

 hay que eliminar las credenciales en <panel de control \ todos los elementos del panel de control \ administrador de credenciales > elijo las credenciales de windows y busco las de las cuentas relacionadas con git y las quito 

luego en cada repositorio cambio la configuración local con el comando `git config --local --edit 

elimino la etiqueta de [user] con sus valores y coloco la siguiente: 

[credential]
 interactive = always 
 
esto hara que cada vez que enviemos un push pida el usuario y la contraseña,  porque no dejara guardar en cache la credencial de github  

esto hara que cada vez que enviemos un push pida el usuario y la contraseña,  porque no dejara guardar en cache la credencial de github

ahora puedo hacer push desde repositorios distintos con diferentes usuarios

= para trabajar desde una maquina con un solo usuario puedo eliminar la anterior configuración 

### pull request 
luego de crear una rama en un repositorio clonado y realizar los cambios a los archivos puedo aportarlos a otra persona con un pull request desde la rama actual a la rama de la persona a la cual vamos a colaborar 
luego tendremos que esperar a que la persona nos acepte o rechace el pull request 

en github la interfaz muestra los botones para el pull request y la elección de las ramas  

despues de realizar el pull request llega un mensaje a el correo de editor original con el enlace de pull para ver las diferencias aguegadas 
el programador original puede aceptar el pull y hacer merge de los cambios 
en el historial de commits se veran los commits de las personas que colaboraron.   
cuando el editor original acepta los cambios llega un correo al editor colaborador 
se debe activar la opcion watching en github para que lleguen los correos 


# pasos para los aportes 
1. Hacer un fork de algun repositorio 
2. clonar el repositorio desde la url de mi cuenta de github
3. Crear una segunda rama local 
4. Empezar el desarrollo y hacer los cambios al proyecto
5. Hacer commits de los cambios locales 
6. hacer un `git push origin ramaDesarrollo` (enviar los commit locales a la nube)
7. crear un pull request hacia la rama a colaborar de editor original 
8. esperar a que el dueño de la otra cuenta nos acepte el cambio

## sincronización cuando hice merge de un pull request  en remoto como editor original 
 al aceptar el merge del pull request estoy aceptando los cambios en el tiempo que hizo el colaborador y por lo tanto El HEAD de mi rama esta por detras de todos esos cambios, y por ende si hago un cambio en mi directorio local y quiero enviarlo con push me notificara el error , porque estoy mandando un cambio a una rama que no esta sincronizada, para resolverlo debo hacer un `git fetch para traer los cambios remotos del colaborador que estan en mi rama a una rama escondida en mi directorio local  y luego hacer un git merge desde la rama que estoy, de la que quiero adjuntar, o puedo hacer un git pull que es los dos pasos el fetch y el merge en uno solo 

## sincronización cuando hice merge de un pull request  
despues de hacer un merge de una rama en el repositorio remoto de un pull request, esa rama adquiere los commits del coloborador,  esos cambios no estan en el directorio local y ademas estan por delante del commit del HEAD local que era el que estaba sincronizado con el remoto.
para sincronizarlos de nuevo debo traer esos cambios del remoto al local para poder seguir desarrollando,
porque si no git no me dejara hacer push hacia la rama remota, para eso se usa un git fetch

##  git fetch 
Este comando traera los cambios de la rama en remoto y creara una rama escondida con los commits para que podamos verla y verificar cuales son los cambios antes de adjuntarla con un`git merge` a la rama en la que estamos trabajando, hacemos el merge y ya estamos sincronizados otravez con el remoto y podemos hacer push 
de nuestros cambios y el HEAD volvera a la punta de los commits .
podemos hacerlo tambien con el `git pull` 

## git pull 
este comando es la union del git fetch y el git merge del paso enterior 

## volver a sincronizar la rama del fork cuando el editor original hizo mas commits 

obtener los cambios que se han echo en el repositorio original si nuestra rama no las tiene? 

debemos vincular el repositorio original  
localmente podemos tener sincronizado el repositorio ajeno para hacer fetch y pull y ademas si somos parte de un equipo de trabajo se nos puede habilitar la opción de push 

con `git remote` vemos el repositorio propio vinculado

`git remote -v` igual a `git remote --verbose`
me muestra la url del repositorio propio al cual estoy vinculado remotamente 

podemos agregar otra ruta de un repositorio remoto 
con `git remote add <nombreparafetch> urlDelRepooriginal` el nombre sera el equivalente a origin al cual se manda el push, es como identificamos ese repositorio 

verificamos con git remote -v y deberia aparecer el repositorio original con el nombre que le dimos y url ajena  y el de nosotros con nombre origin

luego jalamos los cambios del repositorio original al nuestro con un `git fetch nombreRepo master`
y luego hacer merge de la rama oculta que trae el fetch 

tambien puedo hacer un `git pull nombreRepo master`

con eso nuestra rama ya tendra los ultimos cambios de la original 




##### Notas para adjuntar 
cuando sincronizo un directorio local con uno el la nube solo se suben las ramas a las que les haga un `git push origin NomRama`
 
en el protocolo https github va a pedir el usuario y la contraseña siempre 

### borrar una rama remota sincronicamente desde local 

cuando voy a borrar una rama de repositorio remoto tengo que borrarla primero el local, si esta no esta fusionada me salta un error para que la fusionemos, podemos fusionarla a la rama de desarrollo pero si no queremos hacerlo aun se puede  crear otra rama separada y hacer un merge desde esa, luego puedo borrarla  hacer un `git branch -d rama` hay estara borrada localmente para hacerlo remoto uso `git push origin --delete rama`

### `git push origin --delete rama`
elimina la rama del repositorio remoto 

### `git branch -d rama`
elimina la rama local 


## `git branch --no--merge`
para saber cual rama no hemos fusionado usamos el comando `git branch --no--merge` u listara solo las que estan con desarrollos independientes a la principal 



## cuidado con los merge 

cuando hacemos un merge de una rama a la que se le borro alguna caracteristica NO MOSTRARA mensaje de conflictos porque git no detecta conflictos con lineas que no existen, esto se produciria como un cambio natural 


# trabajo con sourcetree

es un GUI git user interface 

en la ventana izquierda en workspace me muestra el git status  , automaticamente detectara los cambios y mostra la diferencia 
graficamente muestra si estan en stagin o no y puedo hacer el commit desde la misma pestaña 

la pestaña de history es el equivalente del git log de la terminal 

cuando hacemos commit empieza un contador en el boton de push indicando cuantos commit no estan en remoto 

al hacer el push con el boton me muestra las ramas que tengo configuradas hacia las cuales puedo hacer el push 

navegando por el historial de sourcetre no se cambia el estado de los archivos 

se muestran los diferentes archivos mmodificados y sus diferencias 

para saltar  de rama en source en branches doy click derecho y checkout rama 

si cambio de rama desde terminal en sourcetree tambien cambiara y reconocera tambien los cambios de los archivos 

 Cuidado si cambio de rama en source, la terminal no mostrara el cambio de rama solo hasta que haga el commit debo volver a cambiar de rama para hacer commit en la rama que desee 

 cambio con origin master 
 
debo tener cuidado porque cuando cambio de rama en source no lo hace en terminal y al hacer el push lo manda a la rama en la que estoy en source debo verificar antes la rama con git branch 

tengo problema con la rama testing en source cuando hago el commit y el push no aparecen en el historial source, tengo que dar clic al la rama en historia u saltar entre ramas  para que se actualize 

si no hago los commits  desde la terminal sourcetree los va reconociendo simultaneamente 

### abrir proyecto y cambiar nombre 

 en la primera pestaña donde se muestra la lista de repositorios para abrirlos observo en que rama estoy ubicado en cada repositorio y puedo cambiar el nombre del Rep que se muestra en source (el local NO cambia)
si doy click en el listado se abrira el proyecto 

### la pestaña REMOTES 
Nos mostrara los repositorios a los cuales estemos vinculados remotamente y en cada uno de ellos la ramas  

con el boton de terminal abrimos la terminal si tenemos git bash 

# usar varios usuario con el uso de terminal de ubuntu 
   
   puedo usar otra terminal de ubuntu con otro repositorio local y conffigurar el nombre de usuario y la contraseña de github y a la vez tener la terminal de github
   



De igual manera puedo tener los dos repositorios de las dos terminales distintas abiertos en sourcetree y mandar los push hacia los repositorios que tenga configurados 

de todas manera hay acciones en la terminal que no ofrece la GUI sourcetree como filtrar los commits por fecha 

### merge y branch desde sourcetree 
podemos indicarle graficamente a cual rama estoy haciendolo y habilitar la opcion de hacer merge si no hay conflictos,
luego aparece una ventana para seleccionar la rama 

# BITBUCKET
es un servicio similar a github para subir repositorios en la nube 

## vincularnos con un repositorio remoto de bitbucket 
despues de loguearnos como en cualquier pagina con un email creamos un repositorio 
debo crearlo vacio para subir archivos que tenga locales si no me pedira hacer un pull del readme.md por defecto

cuando creamos un repositorio en bitbucket y le decimos que nos adicione el archivo  README.md ese va a contar como el primer commit de la historia y cuando vaya a hacer el push de mis archivos, los historiales coincidiran y  nos pedira que hagamos un pull para sincronizar los repositorios pero no estaran relacionados porque la historia del remoto es la del readme del remoto, diferente a la de readme.md local que tiene nuestro trabajo, saldra error de Git "fatal: refusing to merge unrelated histories " se produce cuando se fusionan dos proyectos no relacionados (es decir, proyectos que no son conscientes de la existencia de la otra y tienen historias de compromiso que no coinciden). 

para solucionar ese error tendriamos que crear una rama alterna desde el commit donde nos encontremos y y dejar el master en blanco   para no tener confllictos, luego hacer un 
git pull origin master --allow-unrelated-histories

desde la rama master borrar el readme.md y los archivos que tengan conflictos 
git add y commit de los cambios 
volver a hacer un push para sincronizar 

luego de borrar el readme.md  que viene por defecto, puedo volver a fusionar las ramas con la que habia hecho la copia 
hacer el commit y el push de ese merge y ya estaran sincronizadas  
si no me deja fusionar porque tienen historias distinta puedo copiar y peguar el contenido de los archivos y volver a hacer push 

pero mejor crear el repo sin el readme y este recibira el primer push que hagamos sin conflictos de historiales 



en terminal vemos los repositorios remotos con `git remote -v`
para no confundir los nombres de origin puedo cambiar los nombres de los repositorios que estan vinculados a github con " git remote rename <nombreViejo> <nombreNuevo> " 

luego vinculo el repositorio de bitbucket con el mismo nombre con 'git remote add bitbucket <url>'

si listamos de nuevo los repositorios remotos debe aparecer el de github y el de bitbucket git remote -v 
ya estamos vinculados con el repositorio de bitbucket y falta enviarle los archivos con push 

## ramas en bitbucket 

en la interfaz puedo elegir el commit desde el cual se hace la bifurcación 
cuando hago el commit puedo activar la casilla para que haga un push al remoto.  si no hay rama de ese nombre remotamente se creara 
al hacer un push la interfaz me da a elegir la rama a la cual hacerlo 
si hago push y tengo varios remotos el boton del push seguira notificando que hay uno o mas pendientes hasta que se hayan enviado a todos los remotos 
para eliminar un repositorio remoto usamos <git remote remove (nombreREPO)>

### configural repositorio con sourcetree 

creamos el repositorio remoto vacio, despues clicando en el boton de settings de sourcetree ponemos la url del repo con el servidor y usuario que vamos a usar y despues hacemos un push y ya estara nuetro repositorio local  subido  

podemos seguir trabajando y al hacer los push la interfaz me dara a elegir a cual remoto de los que tengo vinculados con el directorio local quiero enviar los cambios 

##### usamos  "git push -u " <  cuando es el primer push hacia el remoto>

siempre asegurandonos que estamos en el directorio del repo 

git push -u <nomRepo>  <rama ACTUAL a empujar>   podemos hacer un git push -u <nomRepo> --all para empujar todas las ramas pero si no queremos subirlas todas lo hacemos por rama  " 

siempre hay que estar en la rama que voy a hacer el push  desde una rama segundaria no me deja enviar al master 

 

Considere los siguientes dos casos que arrojan este error: Git "fatal: refusing to merge unrelated histories "

Ha clonado un proyecto y, de alguna manera, el .gitdirectorio se eliminó o corrompió. Esto lleva a Git a desconocer su historial local y, por lo tanto, provocará que arroje este error cuando intente empujar hacia o desde el repositorio remoto.

Ha creado un nuevo repositorio, le ha agregado algunas confirmaciones y ahora está intentando extraerlo de un repositorio remoto que ya tiene algunas confirmaciones propias. Git también arrojará el error en este caso, ya que no tiene idea de cómo se relacionan los dos proyectos.

Solución
El error se resuelve al alternar el interruptor de permitir historias no relacionadas . Después de un comando git pull o git merge, agregue la siguiente etiqueta:

git pull origin master --allow-unrelated-histories

### vim como editor de texto 
para que los commits se puedan hacer desde la terminal podemos configurar 

`git config --global core.editor "vim" `  el nombre del editor entre comillas 

# conexión ssh 

-vamos a disco c y creamos un directorio para las llaves ssh para evitat problemas de rutas 
-ejecutamos el comando `ssh-keygen -t rsa -C "email@gmail.com " --> se coloca el correo con el que nos registramos en github 
-indicamos la ruta del directorio   /c/llaves-ssh/nombrellave 

se generara una llave en el directorio , esa es la llave ,  para ver el contenido usamos cat

-cat /c/llaves-ssh/nombrellave.pub   esa es la llave publica que se registra en github 
-copiamos todo el contenido de la llave pub 
-vamos a nuestra cuenta de github a settings, despues a <ssh and GPG keys> en el boton de new key y pegamos el contenido de la .pub le ponemos un titulo y clicamos en add new key 
-vamos al repositorio y copiamos el enlace de conexión por ssh 
-agregamos el repositorio remoto por conexión ssh con `git remote add nomRepSSH url`
-activamos el agente ssh con `eval "$(ssh-agent -s)
-en el directorio local agregamos la llave con el comando <ssh-add /c/llaves-ssh/nomKey>
-verificamos que estemos vinculados con <git remote -v >

de esta formma podemos mandar push sin que nos pregunte el usuario y contraseña para cada repositorio que configuremos con la llave 



## github 

clono el repositorio 
