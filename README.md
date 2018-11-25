# Practica Curso de Git - Mobile Bootcamp VIII

* ¿Qué comando utilizaste en el paso 11? ¿Por qué? 
 ```git reset --hard HEAD~1```
 
 Este comando realiza dos acciones:
 1 Hace un reset en el staging area, por lo que limpia el staging area 
 2 Hace un checkout que limpia el working copy
 
 Con esto movemos el puntero de la rama styled al commit anterior
 
* ¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?
```
git reflog // Obtenemos que el commit borrado es 51fe005

git reset --hard 51fe005

git log --pretty=oneline
51fe005e74d8695eb1820e458713aab698959e16 (HEAD -> styled) Añadiendo estilo a git-nuestro.md
5c404c9589d0593137360bc8c48f3a2b97975e83 (master) Añado git-nuestro.md
```

* El merge del paso 13, ¿Causó algún conflicto? ¿Por qué?
```
git checkout styled // Aseguramos que estamos en styled
git merge master
Already up to date.
```
Dado que *styled* absorbe a *master* no se va a ver afectado el grafo, puesto que styled no tiene ningun commit pendiente por absorber. No causa conflicto y los punteros de *master* y *styled* permanencen intactos

* El merge del paso 19, ¿Causó algún conflicto? ¿Por qué?
```
git checkout styled // Nos movemos a styled
git merge htmlify // Da conflicto en el fichero
```
Si da conflicto en el fichero porque dos fuentes han modificado las mismas lineas y con el merge no quedan commits inaccesibles.

* El merge del paso 21, ¿Causó algún conflicto? ¿Por qué?
```
git checkout master
git merge styled
```
No causa conflicto porque a ojos del merge, solo la rama styled ha alterado lineas en el fichero y con el merge no quedan commits inaccesibles. Es un merge fast-forward

* ¿Qué comando o comandos utilizaste en el paso 25?
```
git log --graph --pretty=oneline
*   ada6783880118332d9d4165c139b280b6b39965e (HEAD -> master) Merge branch 'styled'
|\  
| *   d19a030cc756302f6acdc74a531c70fcc69f1db2 (styled) Merge branch 'htmlify' into styled
| |\  
| | * 0efc5e25eb72c733c8f9fb8672dc2c61f7b630f3 (htmlify) Añadiendo estilo html a git-nuestro.md
| |/  
|/|   
| * 51fe005e74d8695eb1820e458713aab698959e16 Añadiendo estilo a git-nuestro.md
|/  
* 5c404c9589d0593137360bc8c48f3a2b97975e83 Añado git-nuestro.md
```
Hay un merge no fast-forward entre master y style porque he forzado no tener fast forward

* El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?
```
git checkout master
git merge --no-ff title
```

Puede ser fast forward porque master no ha realizado ningun cambio y con el merge no quedan commits inaccesibles

* ¿Qué comando o comandos utilizaste en el paso 27?
```
git reset HEAD~1
```

* ¿Qué comando o comandos utilizaste en el paso 28?
```
git checkout
```

* ¿Qué comando o comandos utilizaste en el paso 29?
```
git branch -d title // Sabemos que va a fallar porque queda un commit inaccesible
git branch -D title // Este si la borra
```


* ¿Qué comando o comandos utilizaste en el paso 30?

```
git reflog
ada6783 (HEAD -> master) HEAD@{0}: reset: moving to HEAD~1
5860bf2 HEAD@{1}: merge title: Merge made by the 'recursive' strategy. // Queremos ir a este
ada6783 (HEAD -> master) HEAD@{2}: checkout: moving from title to master
86c2a12 HEAD@{3}: checkout: moving from master to title 

git reset --hard 5860bf2
```

* ¿Qué comando o comandos usaste en el paso 32?

```
git reflog
ada6783 (HEAD -> master) HEAD@{0}: reset: moving to HEAD~1
5860bf2 HEAD@{1}: merge title: Merge made by the 'recursive' strategy.
ada6783 (HEAD -> master) HEAD@{2}: checkout: moving from title to master
86c2a12 HEAD@{3}: checkout: moving from master to title
ada6783 (HEAD -> master) HEAD@{4}: reset: moving to HEAD~1
86c2a12 HEAD@{5}: merge title: Fast-forward
ada6783 (HEAD -> master) HEAD@{6}: checkout: moving from master to master
ada6783 (HEAD -> master) HEAD@{7}: checkout: moving from title to master
86c2a12 HEAD@{8}: commit: Añadiendo titulo a git-nuestro.md
ada6783 (HEAD -> master) HEAD@{9}: checkout: moving from master to title
ada6783 (HEAD -> master) HEAD@{10}: reset: moving to HEAD~1
5226db3 HEAD@{11}: checkout: moving from master to master
5226db3 HEAD@{12}: commit: Añadiendo titulo a git-nuestro.md
ada6783 (HEAD -> master) HEAD@{13}: merge styled: Merge made by the 'recursive' strategy.
5c404c9 HEAD@{14}: checkout: moving from styled to master
d19a030 (styled) HEAD@{15}: commit (merge): Merge branch 'htmlify' into styled
51fe005 HEAD@{16}: checkout: moving from htmlify to styled
0efc5e2 (htmlify) HEAD@{17}: commit: Añadiendo estilo html a git-nuestro.md
5c404c9 HEAD@{18}: checkout: moving from master to htmlify
5c404c9 HEAD@{19}: checkout: moving from styled to master
51fe005 HEAD@{20}: checkout: moving from master to styled
5c404c9 HEAD@{21}: checkout: moving from styled to master
51fe005 HEAD@{22}: reset: moving to 51fe005
5c404c9 HEAD@{23}: reset: moving to HEAD~1
51fe005 HEAD@{24}: commit: Añadiendo estilo a git-nuestro.md
5c404c9 HEAD@{25}: checkout: moving from master to styled
5c404c9 HEAD@{26}: commit (initial): Añado git-nuestro.md

git checkout 5c404c9
```
Nos movemos con un checkout al commit porque no nos han pedido que cambiemos el puntero de la rama master

* ¿Qué comando o comandos usaste en el punto 33?
```
git checkout master
```

