### Rol de usuario  

* Haz un fork del repositorio desde la web https://github.com/SoCFPGA-learning/CYC1000

* Clona al ordenador local el fork que ahora está en tu propio GitHub (remoto)

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


