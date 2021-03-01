# Ayuda y colaboración en GitHub

Vamos a ver como puedes colaborar en los repositorios tanto si eres miembro de la organización SocFGPA-learning como si no. 

Aquí usaremos la herramienta Git desde la línea de comandos. Tambien puedes instalar [GitHub Desktop](https://desktop.github.com/).

En los siguientes comandos se usa de ejemplo el repositorio CYC1000. Recuerda cambiar "CYC1000" por el repositorio adecuado.

Para conocer Git, consulta esta guía sobre el uso de Git desde la línea de comandos:

* https://rogerdudler.github.io/git-guide/index.es.html

Primero debes instalar Git (por ejemplo desde una distro Debian/Ubuntu):

```
sudo apt-get install git
```

### Rol de miembro de SocFPGA-learning (owner)

Ejecuta en la línea de comandos:

```sh
#cambia CYC1000 por el repósitorio que toque
git clone  https://github.com/SoCFPGA-learning/CYC1000
cd CYC1000
```

Hacer los cambios o añadir contenido. Por ejemplo si actualizas el fichero README.md, para actualizar el repositorio local y remoto:

```sh
git add README.md
git commit -m "modificación README"
git push
```

### Rol de usuario  

Para una descripción mas detallada y trabajar con ramas "branch" mira este [documento](https://github.com/SoCFPGA-learning/General/tree/main/Contributing#pull-requests) en inglés.

La versión obsoleta en castellano esta [aquí](rol_usuario.md).

### Herramientas de edición y actualización

* Para editar en Markdown los ficheros .md una muy buena herramienta es Typora (https://typora.io/)

* Script para actualizar de golpe todos los cambios [upd.sh](./upd.sh)

  * Colócalo en la raiz del repositorio. Ten en cuenta que es peligroso añadir todos los ficheros cambiados, ya que puede ser que no quieras actualizar cierto fichero en el que aún estás haciendo cambios

* Fichero [.gitignore](./.gitignore) para que no sean visibles ciertos archivos en la versión web

  * Colócalo en la raiz del repositorio con el siguiente contenido:
  
  ```
  upd.sh
  clean.sh
  .gitignore
  ```
  
* [clean.sh](./clean.sh) Script para limpiar las carpetas del Quartus

  * Colócalo en cada carpeta de proyecto Quartus y ejecútalo antes de subir los proyectos a GitHub.


### Comandos útiles

```sh
git status #para ver los cambios desde el último commit
git log    #para ver los commits
git show  xxxxxxx_commit_id_xxxxxxx   #para ver los cambios de un commit
git clone http://github.com/usuario/repositorio  #para clonar un repo
git pull   #para actualizar el repo local con la versión remota

#Para borrar el último commit local y remoto
git reset HEAD~ 				
git push  origin +main   #main en los nuevos repos, master en los antiguos

```

