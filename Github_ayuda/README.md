# Ayuda y colaboración en GitHub

Vamos a ver como puedes colaborar en los repositorios tanto si eres miembro de la organización SocFGPA-learning como si no. 

En los siguientes ejemplos se usa el repositorio CYC1000. Recuerda cambiar los comandos por el repositorio adecuado.

Para conocer Git, consulta esta guía sobre el uso de Git desde la línea de comandos:

* https://rogerdudler.github.io/git-guide/index.es.html

Primero debes instalar Git (por ejemplo si usas una distro Debian/Ubuntu):

`sudo apt-get install git`

### Rol de owner

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

* Haz un fork del repositorio desde la web https://github.com/SoCFPGA-learning/CYC1000

* Clona al ordenador local el fork que ahora está en tu propio usuario

  `git clone  https://github.com/TU-USUARIO/CYC1000`

* Actualizando cambios en tu fork:

```sh
git add README.md
git commit -m "modificación README"
git push
```

* Propón los cambios realizados en el repositorio original: desde tu web de usuario https://github.com/TU-USUARIO/CYC1000 crea un Pull Request.  
* El administrador del repositorio original revisará/comentará/aceptará los cambios propuestos.

En caso que tu fork se haya quedado des-actualizado (en la web puedes ver si tu fork está por detrás en número de commits), para actualizar tu fork con el repositorio original sigue estos pasos ([+info](https://stackoverflow.com/questions/7244321/how-do-i-update-a-github-forked-repository)):

```sh
#cambia CYC1000 por el repósitorio que toque
git remote add upstream https://github.com/SoCFPGA-learning/CYC1000
git fetch upstream
git checkout main
git rebase upstream/main
git push -f origin main
#main en los nuevos repos, master en los antiguos
```



### Herramientas de edición y actualización

* Para editar en Markdown los ficheros .md puedes usar Typora https://typora.io/

* Script para actualizar de golpe todos los cambios [upd.sh](./upd.sh). Colócalo en la raiz del repositorio. Ten en cuenta que es peligroso añadir todos los ficheros cambiados, ya que puede ser que no quieras actualizar cierto fichero en el que aún estás haciendo cambios.

* Fichero [.gitignore](./.gitignore) para que no sean visibles ciertos archivos en la versión web. Colócalo en la raiz del repositorio con el siguiente contenido:

  ```
  upd.sh
  clean.sh
  .gitignore
  ```
  
  


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

