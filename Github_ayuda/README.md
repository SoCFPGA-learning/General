# Colaboración repos GitHub

Vamos a ver el ejemplo con el repo CYC1000 según seas miembro owner en la organización SocFGPA-learning o si quieres colaborar sin serlo.

Consulta esta guía sobre el uso de Git desde la línea de comandos:

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

* Clona al ordenador local el fork que ahora está en tu própio usuario

  `git clone  https://github.com/TU-USUARIO/CYC1000`

* Actualizando cambios en tu fork:

```sh
git add README.md
git commit -m "modificación README"
git push
```

* Propón los cambios realizados en el repositorio original: desde tu web de usuario https://github.com/TU-USUARIO/CYC1000 crea un Pull Request.  
* El administrador del repositorio original revisará/comentará/aceptará los cambios propuestos.

Para actualitzar tu fork con el repositorio original sigue estos pasos([+info)](https://stackoverflow.com/questions/7244321/how-do-i-update-a-github-forked-repository):

```sh
#cambia CYC1000 por el repósitorio que toque
git remote add upstream https://github.com/SoCFPGA-learning/CYC1000
git fetch upstream
git checkout master
git rebase upstream/master
git push -f origin master
```



### Herramientas de edición y actualización

* Para editar en Markdown los ficheros .md puedes usar Typora https://typora.io/

* Script para actualizar de golpe todos los cambios [upd.sh](./upd.sh). Colócalo en la raiz del repositorio.

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
git pull   #para actualizar el repo local 

#Para borrar el último commit local y remoto
git reset HEAD~ 				
git push  origin +main   #main en los nuevos repos, master en los antiguos

```

