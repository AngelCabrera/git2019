# Conceptos sobre Git y Github - Curso, Platzi, Freddy Vega, 2019

## Introducción a git y github

### ¿Qué es un sistema de control de versiones?

El control de versiones es un sistema que registra los cambios realizados sobre un archivo o conjunto de archivos a lo largo del tiempo, de modo que puedas recuperar versiones específicas más adelante. Cualquier tipo de archivo que encuentres en un ordenador puede ponerse bajo control de versiones.

Te permite revertir archivos a un estado anterior, revertir el proyecto entero a un estado anterior, comparar cambios a lo largo del tiempo, ver quién modificó por última vez algo que puede estar causando un problema, quién introdujo un error y cuándo, y mucho más. Usar un VCS también significa generalmente que si fastidias o pierdes archivos, puedes recuperarlos fácilmente. Además, obtienes todos estos beneficios a un coste muy bajo.

### ¿Qué es Git?

Git es un sistema de control de versiones distribuido, fue diseñado por Linus Torvalds, pensando en la eficiencia y la confiabilidad del mantenimiento de versiones de aplicaciones cuando éstas tienen un gran número de archivos de código fuente.

### ¿Qué es Github?

Es una forja para alojar proyectos utilizando el sistema de control de versiones Git. Se utiliza principalmente para la creación de código fuente de programas de computadora.

Github puede considerarse como la red social de código para los programadores y en muchos casos es visto como tu curriculum vitae.

## Comandos y Conceptos Básicos de Git

### ¿Cuáles son las tres secciones principales de un proyecto de Git?

- El directorio de Git (**Git Directory**, Repository)
- El directorio de trabajo (**Working Directory**)
- El área de preparación (**Staging Area**)

### ¿Qué es el Staging Area y Git Directory?

Al ejecutar el comando _"git init"_ (comando para iniciar un repositorio git) ocurren dos cosas:

- Se crea una carpeta _.git_. El cual es el directorio o repositorio donde Git almacena los metadatos y la base de datos de objetos para tu proyecto. Es la parte más importante de Git, y es lo que se copia cuando clonas un repositorio desde otro ordenador.
- Se crea un sencillo archivo que define el _staging area_, generalmente está contenido en el _directorio de Git_, que almacena información acerca de lo que va a ir en tu próxima confirmación.

### ¿Cuál es el ciclo básico de trabajo en GitHub?

1. Modificas una serie de archivos en tu directorio de trabajo.
2. Preparas los archivos, añadiendolos a tu área de preparación.
3. Confirmas los cambios, lo que toma los archivos tal y como están en el área de preparación, y almacena esas instantáneas de manera permanente en tu directorio de Git.

![Secciones Github](https://git-scm.com/figures/18333fig0106-tn.png)

### Estados de un archivo

Si una versión concreta de un archivo está en el directorio de Git, se considera confirmada (**committed**). Si ha sufrido cambios desde que se obtuvo del repositorio, pero ha sido añadida al área de preparación, está preparada (**staged**). Y si ha sufrido cambios desde que se obtuvo del repositorio, pero no se ha preparado, está modificada (**modified**).

### ¿Qué es un _Branch_ y como funciona un _Merge_ en Git?

Git es una base de datos muy precisa con todos los cambios y crecimiento que ha tenido nuestro proyecto. Los commits son la única forma de tener un registro de los cambios. Pero las ramas amplifican mucho más el potencial de Git.

Todos los commits se aplican sobre una rama. Por defecto, siempre empezamos en la rama master (pero puedes cambiarle el nombre si no te gusta) y creamos nuevas ramas, a partir de esta, para crear flujos de trabajo independientes.

Crear una nueva rama se trata de copiar un commit (de cualquier rama), pasarlo a otro lado (a otra rama) y continuar el trabajo de una parte específica de nuestro proyecto sin afectar el flujo de trabajo principal (que continúa en la rama master o la rama principal).

Los equipos de desarrollo tienen un estándar: Todo lo que esté en la rama master va a producción, las nuevas features, características y experimentos van en una rama “development” (para unirse a master cuando estén definitivamente listas) y los issues o errores se solucionan en una rama “hotfix” para unirse a master tan pronto como sea posible.

Crear una nueva rama lo conocemos como Checkout. Unir dos ramas lo conocemos como Merge.

Podemos crear todas las ramas y commits que queramos. De hecho, podemos aprovechar el registro de cambios de Git para crear ramas, traer versiones viejas del código, arreglarlas y combinarlas de nuevo para mejorar el proyecto.

Solo ten en cuenta que combinar estas ramas (sí, hacer “merge”) puede generar conflictos. Algunos archivos pueden ser diferentes en ambas ramas. Git es muy inteligente y puede intentar unir estos cambios automáticamente, pero no siempre funciona. En algunos casos, somos nosotros los que debemos resolver estos conflictos “a mano”.

### ¿Cuáles son los comandos básicos para crear repositorios y commits?

- **git init**: inicializa un repositorio de GIT en la carpeta donde se ejecute el comando.
- **git add**: añade los archivos especificados al _staged area_.
- **git commit -m "commit description"**: confirma los archivos que se encuentran en el área de preparación y los agrega al repositorio.
- **git commit -am "commit description"**: añade al staging area y hace un commit mediante un solo comando. (No funciona con archivos nuevos)
- **git status**: ofrece una descripción del estado de los archivos (untracked, ready to commit, nothing to commit).
- **git rm (. -r, filename) (--cached)**: remueve los archivos del index.
- **git config --global user.email "tu@email.com"**: configura tu email.
- **git config --global user.name "Tu Nombre"**: configura tu nombre.
- **git config --list"**: lista las configuraciones (puedes ver el usuario y el correo del usuario).

### ¿Cómo analizar cambios en los archivos de un proyecto Git?

- **git log**: lista de manera descendente los commits realizados.
- **git log --stat**: además de listar los commits, muestra la cantidad de bytes añadidos y eliminados en cada uno de los archivos modificados.
- **git log --all --graph --decorate --oneline**: muestra de manera comprimida toda la historia del repositorio de manera gráfica y embellezida.
- **git show _filename_**: permite ver la historia de los cambios en un archivo.
- **git diff (commit1) (commit2)**: compara diferencias entre en cambios confirmados.

### ¿Cómo volver en el tiempo con branches y checkout?

- **git reset (commit) --soft/hard**: regresa al commit especificado, eliminando todos los cambios que se hicieron después de ese commit.
- **git checkout (commit/branch) (filename)**: permite regresar al estado en el cual se realizó un commit o branch especificado, pero no elimina lo que está en el staged area.

## Flujo de Trabajo Básico en Git

### ¿Cuáles son las bases para trabajar con un repositorio remoto?

- **git remote add origin (link)**: enlaza el repositorio local con el repositorio remoto.
- **git push origin (branchName)**: exportar los archivos confirmados en el repositorio local al repositorio remoto.
- **git pull origin (branchName)**: importa los archivos del repositorio remoto al repositorio local y al working directory.
- **git fetch**: importa los archivos remotos al repositorio local pero no al working directory.
- **git merge**: una vez hecho el git fetch, hace falta hacer un git merge para que los archivos importados aparezcan en el working directory.

### ¿Cómo trabajar con Ramas o Branches de Git?

- Al crear una nueva rama se copia el último commit en esta nueva rama. Todos los cambios hechos en esta rama no se reflejarán en la rama master hasta que hagamos un **merge**.
- **git branch _branchname_**: crea una nueva rama.
- **git checkout _branchname_**: nos mueve a la rama especificada.
- **git merge _branchname_**: fusiona la rama actual con la rama especificada y crea un nuevo commit de esta fusión.
- **git branch**: lista las ramas creadas.

### ¿Cómo resolver conflictos en Git?

Al trabajar en dos o más ramas sobre las mismas líneas de código, ocurrirían conflictos a la hora de hacer merge. Git automáticamente nos especificaría en nuestro código dónde se encuentran los conflictos.

Para resolver este problema debemos especificar la rama de donde queremos obtener el cambio, quedarnos con esas modificaciones y realizar un commit para completar el merge.

## Trabajando con repositorios remotos en Github

### Llaves públicas y privadas Github

Las llaves públicas se conectan con las llaves privadas. Las llaves públicas se comparten sin problemas, las llaves privadas no se deben compartir.

Las llaves públicas sirven para cifrar los mensajes privados. Las llaves privadas sirven para descifrar los mensajes cifrados con la llave pública.

De esta manera podemos compartir información de manera segura.

- **git remote set-url origin url-ssh-del-repositorio-en-github**: establece la url del repositorio remoto a través de ssh.

### Tags y versiones en Git y Github

- **git tag -a nombre_del_tag -m "Mensaje para guardar el tag" commit_id**: permite agregar un tag en git para identificar lo que se desea.
- **git show-ref --tags**: muestra el id que referencia a un tag.
- **git tag**: muestra los tags que se han creado.
- **git tag -d tagname**: elimina el tag especificado.
- **git push origin --tags**: exporta los tags al repositorio en github.
- **git push origin :refs/tags/nombre_del_tag_a_borrar**: permite hacer los cambios en los tags en github.

### Ramas en github

- **git push origin _branchname_**: exporta la rama o los cambios al repositorio remoto.
- **git pull origin _branchname_**: importa la rama especificada al working directory y al repositorio local o los cambios ocurridos.

### Pull Requests en Github

Pull Requests son herramientas de GitHub para solicitar modificaciones en el repositorio remoto, permiten que los colaboradores del proyecto revisen los cambios y dependiendo de su criterio, acepten estos cambios y lo fusionen con la rama master o los descarten, también pueden solicitar cambios a este pull request para luego aceptarlo.

## Múltiples entornos de trabajo

### Reorganizando el trabajo realizado

- **git rebase _branchname_ (desde rama nueva a rama a unir)**: solo útil para los cambios locales, une dos ramas y modifica la historia.
- **git rebase _branchname_ (sentido contrario)**: luego de hacer el primer rebase, hacemos este rebase.

### Guarda cambios en memoria y recupéralos cuando necesites

- **git stash**: agrega los cambios a un lugar temporal para permitirte cambiar de rama o lugar sin hacer commit.
- **git stash list**: lista los cambios que se encuentran en stash.
- **git stash pop**: trae los cambios de regreso.
- **git stash branch _branchname_**: crea una rama y aplica el stash.

### Limpiar tu proyecto de archivos no deseados (Archivos untracked)

- **git clean -f**: borra archivos no deseados.
- **git clean -df**: permite borrar archivos y carpetas.
- **git clean --dry-run**: especifica lo que se va a borrar.

### Git Cherry-Prick: Traer commits viejos al head de un branch

- **git cherry-pick _commit-reference_**: trae solamente el commit especificado a la rama que se desee desde la rama que se quiera.

### Git Ammend: Reconstruir commits en git

**git commit --ammend**: fusiona el commit actual con el commit anterior y te permite escribir un nuevo mensaje.

### Git Reset y Reflog: Úsese en caso de emergencia

- **git reflog**: muestra todos los cambios del HEAD.
- **git reset --hard _commit-id_**: regresa en el tiempo si han habido problemas en los commits recientes.

### Buscar dentro de archivos y commits con Grep y log

- **git grep -c -n _Palabra_**: muestra donde, cuantas veces o en que líneas se utiliza la palabra especificada.

- **git log -S "\_Palabra"**: muestra las veces que se utilizó la palabra en los commits.
