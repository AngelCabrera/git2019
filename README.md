# Conceptos sobre Git y Github - Curso, Platzi, Freddy Vega, 2019

### ¿Qué es un sistema de control de versiones?

El control de versiones es un sistema que registra los cambios realizados sobre un archivo o conjunto de archivos a lo largo del tiempo, de modo que puedas recuperar versiones específicas más adelante. Cualquier tipo de archivo que encuentres en un ordenador puede ponerse bajo control de versiones.

Te permite revertir archivos a un estado anterior, revertir el proyecto entero a un estado anterior, comparar cambios a lo largo del tiempo, ver quién modificó por última vez algo que puede estar causando un problema, quién introdujo un error y cuándo, y mucho más. Usar un VCS también significa generalmente que si fastidias o pierdes archivos, puedes recuperarlos fácilmente. Además, obtienes todos estos beneficios a un coste muy bajo.

### ¿Qué es Git?

Git es un sistema de control de versiones distribuido, fue diseñado por Linus Torvalds, pensando en la eficiencia y la confiabilidad del mantenimiento de versiones de aplicaciones cuando éstas tienen un gran número de archivos de código fuente.

### ¿Qué es Github?

Es una forja para alojar proyectos utilizando el sistema de control de versiones Git. Se utiliza principalmente para la creación de código fuente de programas de computadora.

Github puede considerarse como la red social de código para los programadores y en muchos casos es visto como tu curriculum vitae.

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
- **git show _filename_**: permite ver la historia de los cambios en un archivo.
- **git diff (commit1) (commit2)**: compara diferencias entre en cambios confirmados.

### ¿Cómo volver en el tiempo con branches y checkout?

- **git reset (commit) --soft/hard**: regresa al commit especificado, eliminando todos los cambios que se hicieron después de ese commit.
- **git checkout (commit/branch) (filename)**: permite regresar al estado en el cual se realizó un commit o branch especificado, pero no elimina lo que está en el staged area.

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
