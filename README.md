# Trabajando con log/branch y el HEAD en git
## Romén Gilberto García Gómez

## Ejercicio 1
### Mostramos el historial de cambios del repositorio

```bash
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git log
commit e269d4abed3e98ffae77eb490927d323eabdb54b (HEAD -> main, origin/main, origin/HEAD)
Author: Romén Gilberto García Gómez <romengilberto08@gmail.com>
Date:   Thu Oct 10 18:02:25 2024 +0100

    Initial commit
```
### Creamos la carpeta capítulos y el archivo capitulo1.txt dentro de ella

```bash
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ mkdir capitulos
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ cat > capitulos/capitulo1.txt
it es un sistema de control de versiones ideado por linus Torvalds.
```

### Aañadimos los cambios a la zona de intercambio temporal, luego hacemos commit y mostramos de nuevo el historial de cambios del repositorio

```bash
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git add .
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git commit -m "Añadido capítulo 1."
[main 51094a2] Añadido capítulo 1.
 1 file changed, 1 insertion(+)
 create mode 100644 capitulos/capitulo1.txt
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git log
commit 51094a24170be1bfdc4ccf65ca98c4da5183eaa4 (HEAD -> main)
Author: PRORIX <romengilberto08@gmail.com>
Date:   Thu Oct 10 18:21:33 2024 +0100

    Añadido capítulo 1.

commit e269d4abed3e98ffae77eb490927d323eabdb54b (origin/main, origin/HEAD)
Author: Romén Gilberto García Gómez <romengilberto08@gmail.com>
Date:   Thu Oct 10 18:02:25 2024 +0100
```


## Ejercicio 2
### Cremos el archivo capitulo2.txt

```bash
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ cat > capitulos/capitulo2.txt
El flujo de trabajo básico con Git consiste en:
1- Hacer cambios en el repositorio.
2- Añadir los cambios a la zona de intercambio temporal.
3- Hacer un commit de los cambios.
```

### Añadimos los cambios a la zona de intercambio temporal, hacemos un commit de los cambios y mostramos las diferencias entre la última version y dos versiones anteriores

```bash
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git add .
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git commit -m "Añadido capítulo 2."
[main 192caf3] Añadido capítulo 2.
 1 file changed, 4 insertions(+)
 create mode 100644 capitulos/capitulo2.txt
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git diff HEAD~2..HEAD
diff --git a/capitulos/capitulo1.txt b/capitulos/capitulo1.txt
new file mode 100644
index 0000000..ef62ab0
--- /dev/null
+++ b/capitulos/capitulo1.txt
@@ -0,0 +1 @@
+it es un sistema de control de versiones ideado por linus Torvalds.
diff --git a/capitulos/capitulo2.txt b/capitulos/capitulo2.txt
new file mode 100644
```


## Ejercicio 3
### Cremos otro fichero de texto llamado capitulo3

```bash
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ cat > capitulos/capitulo3.txt
Git permite la creación de ramas lo que permite tener distintas versiones del mismo proyecto y trabajar de manera simultanea en ellas.
```

### Añadimos de nuevo los cambios a la zonan de intercambio temporal, hacemos commit y diff

```bash
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git add .
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git commit -m "Añadido capítulo 3."
[main da4a118] Añadido capítulo 3.
 1 file changed, 2 insertions(+)
 create mode 100644 capitulos/capitulo3.txt
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git log
commit da4a11809221453ecfec6c0d843c9e63ce486a27 (HEAD -> main)
Author: PRORIX <romengilberto08@gmail.com>
Date:   Thu Oct 10 18:37:22 2024 +0100

    Añadido capítulo 3.

commit 192caf3615a3e29f0d366d97997b9b6a40014fbd
Author: PRORIX <romengilberto08@gmail.com>
Date:   Thu Oct 10 18:31:28 2024 +0100
```

## Ejercicio 4
#### Creamos el fichero indice.txt

```bash
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ cat > indice.txt
Indice de los cápitulos, con conceptos avanzados de git
```

### Añadimos los cambios, hacemos commit y mostramos quien ha hecho los cambios

```bash
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git add .
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git commit -m "Se crea el indice"
[main 6f947d0] Se crea el indice
 1 file changed, 1 insertion(+)
 create mode 100644 indice.txt
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ echo "Indice de los capitulos, con conceptos avanzados de git" >> indice.txt
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git commit -m "Añadido el índice."
En la rama main
Tu rama está adelantada a 'origin/main' por 4 commits.
  (usa "git push" para publicar tus commits locales)

Cambios no rastreados para el commit:
  (usa "git add <archivo>..." para actualizar lo que será confirmado)
  (usa "git restore <archivo>..." para descartar los cambios en el directorio de trabajo)
        modificados:     indice.txt

sin cambios agregados al commit (usa "git add" y/o "git commit -a")
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git annotate indice.txt
6f947d0e        (    PRORIX     2024-10-10 18:43:47 +0100       1)Indice de los cápitulos, con conceptos avanzados de git
00000000        (Not Committed Yet      2024-10-10 18:45:25 +0100       2)Indice de los capitulos, con conceptos avanzados de git
```

## Eercicio 5
### Creamos una nueva rama y mostramos todas las ramas del repositorio

```bash
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git branch bibliografia
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git branch -av
  bibliografia        6f947d0 Se crea el indice
* main                6f947d0 [adelante 4] Se crea el indice
  remotes/origin/HEAD -> origin/main
  remotes/origin/main e269d4a Initial commit
```

## Ejercicio 6
### Creamos el fichero capitulo4.txt

```bash
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ cat > capitulos/capitulo4.txt
  En este capítulo veremos cómo usar GitHub para alojar repositorios en remoto.
```

### Añadimos nuevamente los cambios a la zona de intercambio temporal, hacemos commit y mostramos el historial

```bash
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git add .
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git commit -m "Añadido capítulo 4."
[main cbe7751] Añadido capítulo 4.
 2 files changed, 2 insertions(+)
 create mode 100644 capitulos/capitulo4.txt
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git log --graph --all --oneline
* cbe7751 (HEAD -> main) Añadido capítulo 4.
* 6f947d0 (bibliografia) Se crea el indice
* da4a118 Añadido capítulo 3.
* 192caf3 Añadido capítulo 2.
* 51094a2 Añadido capítulo 1.
* e269d4a (origin/main, origin/HEAD) Initial commit
```


## Ejercicio 7
### Vamos a modificar la rama bibliografía, crearemos el fichero bibliografia.txt
```bash
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git checkout bibliografia
Cambiado a rama 'bibliografia'
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ cat > bibliografia.txt
Chacon, S. and Straub, B. Pro Git. Apress.
```

### Añadimos los cambios, hacemos commit y mostramos el historial de todas las ramas

```bash
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git commit -m "Añadida la primera referencia bibliográfica."
En la rama bibliografia
Archivos sin seguimiento:
  (usa "git add <archivo>..." para incluirlo a lo que será confirmado)
        bibliografia.txt

no hay nada agregado al commit pero hay archivos sin seguimiento presentes (usa "git add" para hacerles seguimiento)
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git log --graph --all --oneline
* cbe7751 (main) Añadido capítulo 4.
* 6f947d0 (HEAD -> bibliografia) Se crea el indice
* da4a118 Añadido capítulo 3.
* 192caf3 Añadido capítulo 2.
* 51094a2 Añadido capítulo 1.
* e269d4a (origin/main, origin/HEAD) Initial commit
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git add .
```


## Ejercicio 8
### Fusionamos la rama bibliografia con la main, mostramos el historial, elinimaos la rama bibliografía y mostramos nuevamente el historial

```bash
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git checkout main
A       bibliografia.txt
Cambiado a rama 'main'
Tu rama está adelantada a 'origin/main' por 5 commits.
  (usa "git push" para publicar tus commits locales)
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git merge bibliografia
Ya está actualizado.
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git log --graph --all --oneline
* cbe7751 (HEAD -> main) Añadido capítulo 4.
* 6f947d0 (bibliografia) Se crea el indice
* da4a118 Añadido capítulo 3.
* 192caf3 Añadido capítulo 2.
* 51094a2 Añadido capítulo 1.
* e269d4a (origin/main, origin/HEAD) Initial commit
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git branch -d bibliografia
Eliminada la rama bibliografia (era 6f947d0).
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git log --graph --all --oneline
* cbe7751 (HEAD -> main) Añadido capítulo 4.
* 6f947d0 Se crea el indice
* da4a118 Añadido capítulo 3.
* 192caf3 Añadido capítulo 2.
* 51094a2 Añadido capítulo 1.
* e269d4a (origin/main, origin/HEAD) Initial commit
```


## Ejercicio 9
### Creamos nuevamente la rama bibliografia, nos movemos a ella, y cambiamos el fichero bibliografia.txt

```bash
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git branch bibliografia
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git checkout bibliografia
A       bibliografia.txt
Cambiado a rama 'bibliografia'
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ cat > bibliografia.txt
Chacon, S. and Straub, B. Pro Git. Apress.
Loeliger, J. and McCullough, M. Version control with Git. O’Reilly.
```

### Añadimos los cambios, hacemos un commit, fusionamos ambas ramas y resolvemos el conflicto del fichero bibliografia.txt

```bash
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git commit -a -m "Añadida nueva referencia bibliográfica."
[bibliografia 6f9db3b] Añadida nueva referencia bibliográfica.
 1 file changed, 2 insertions(+)
 create mode 100644 bibliografia.txt
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git checkout main
Cambiado a rama 'main'
Tu rama está adelantada a 'origin/main' por 5 commits.
  (usa "git push" para publicar tus commits locales)
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ cat > bibliografia.txt
Chacon, S. and Straub, B. Pro Git. Apress.
Loeliger, J. and McCullough, M. Version control with Git. O’Reilly.
Hodson, R. Ry’s Git Tutorial. Smashwords (2014)
```

### Añadimos los cambios, hacemos commit y mostramos el historial completo

```bash
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git commit -a -m "Solucionado conflicto bibliografía."
[main 22486f8] Solucionado conflicto bibliografía.
bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$ git log --graph --all --oneline
*   22486f8 (HEAD -> main) Solucionado conflicto bibliografía.
|\  
| * 6f9db3b (bibliografia) Añadida nueva referencia bibliográfica.
* | 4748a66 Añadida nueva referencia bibliográfica.
|/  
* cbe7751 Añadido capítulo 4.
* 6f947d0 Se crea el indice
* da4a118 Añadido capítulo 3.
* 192caf3 Añadido capítulo 2.
:
```

# Trabajando con tags, merge entre ramas y reset

## Ejercicio 1
### Creamos una nueva etiqueta, la empujamos y mostramos todas las etiquetas

```bash
C:\Users\Usuario\romen-ejercicio-git-libro>git tag 1.0.1

C:\Users\Usuario\romen-ejercicio-git-libro>git push origin --tags
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To https://github.com/PRORIX/romen-ejercicio-git-libro
 * [new tag]         1.0.1 -> 1.0.1

C:\Users\Usuario\romen-ejercicio-git-libro>git tag
1.0.0
1.0.1

C:\Users\Usuario\romen-ejercicio-git-libro>

```

## Ejercicio 2
### Hacemos un cambio sencillo, revertimos el cambio y mostramos el resultado

```bash

C:\Users\Usuario\romen-ejercicio-git-libro>notepad capitulo1.txt

C:\Users\Usuario\romen-ejercicio-git-libro>git add capitulo1.txt

C:\Users\Usuario\romen-ejercicio-git-libro>git commit -m "Agregado el cambio sencillo"
[main 489fa11] Agregado el cambio sencillo
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 capitulo1.txt

C:\Users\Usuario\romen-ejercicio-git-libro>git revert
usage: git revert [--[no-]edit] [-n] [-m <parent-number>] [-s] [-S[<keyid>]] <commit>...
   or: git revert (--continue | --skip | --abort | --quit)

    --quit                end revert or cherry-pick sequence
    --continue            resume revert or cherry-pick sequence
    --abort               cancel revert or cherry-pick sequence
    --skip                skip current commit and continue
    --[no-]cleanup <mode> how to strip spaces and #comments from message
    -n, --no-commit       don't automatically commit
    --commit              opposite of --no-commit
    -e, --[no-]edit       edit the commit message
    -s, --[no-]signoff    add a Signed-off-by trailer
    -m, --[no-]mainline <parent-number>
                          select mainline parent
    --[no-]rerere-autoupdate
                          update the index with reused conflict resolution if possible
    --[no-]strategy <strategy>
                          merge strategy
    -X, --[no-]strategy-option <option>
                          option for merge strategy
    -S, --[no-]gpg-sign[=<key-id>]
                          GPG sign commit
    --[no-]reference      use the 'reference' format to refer to commits


C:\Users\Usuario\romen-ejercicio-git-libro>git log
commit 489fa11c914a9f34398fd4b5d8b338d0fa24bbe7 (HEAD -> main)
Author: PRORIX <romengilberto08@gmail.com>
Date:   Wed Nov 20 22:47:02 2024 +0000

    Agregado el cambio sencillo

commit a12989ee6796ebd8fb10374c441ac956a96a0fa1 (tag: 1.0.1, origin/main, origin/HEAD)
Author: Romén Gilberto García Gómez <romengilberto08@gmail.com>
Date:   Thu Oct 10 19:53:34 2024 +0100

    README.md

commit 22486f830f8e4d2f28e8be6c9903baf91e459e5a (tag: 1.0.0)
Merge: 4748a66 6f9db3b
Author: PRORIX <romengilberto08@gmail.com>
Date:   Thu Oct 10 19:48:55 2024 +0100

    Solucionado conflicto bibliografía.

commit 4748a66765431e7118598582632866620049cb94
Author: PRORIX <romengilberto08@gmail.com>
Date:   Thu Oct 10 19:47:15 2024 +0100

    Añadida nueva referencia bibliográfica.

commit 6f9db3bd23af96770b2ff8c2459db345e99735b8
Author: PRORIX <romengilberto08@gmail.com>
Date:   Thu Oct 10 19:41:59 2024 +0100

    Añadida nueva referencia bibliográfica.

commit cbe775115d547e5ca59c802e3278a327ff95088b
Author: PRORIX <romengilberto08@gmail.com>
Date:   Thu Oct 10 19:01:40 2024 +0100

    Añadido capítulo 4.

commit 6f947d0e9037951d8d62ee56264cf3654079c29b
Author: PRORIX <romengilberto08@gmail.com>
Date:   Thu Oct 10 18:43:47 2024 +0100

    Se crea el indice

commit da4a11809221453ecfec6c0d843c9e63ce486a27
Author: PRORIX <romengilberto08@gmail.com>
Date:   Thu Oct 10 18:37:22 2024 +0100

    Añadido capítulo 3.

commit 192caf3615a3e29f0d366d97997b9b6a40014fbd

```

## Ejercicio 5
### Creamos una nueva rama con un cambio nuevo, hacemos un commit y lo aplicamos, luego mostramos el historial de la rama main

```bash
C:\Users\Usuario\romen-ejercicio-git-libro>git checkout -b nueva-funcionalidad
Switched to a new branch 'nueva-funcionalidad'

C:\Users\Usuario\romen-ejercicio-git-libro>echo "En este capítulo veremos cómo gestionar múltiples ramas en Git." > capitulo5.txt

C:\Users\Usuario\romen-ejercicio-git-libro>git add capitulo5.txt

C:\Users\Usuario\romen-ejercicio-git-libro>git commit -m "Añadido capitulo5.txt con información sobre ramas en Git"
[nueva-funcionalidad 90b28f0] Añadido capitulo5.txt con información sobre ramas en Git
 1 file changed, 1 insertion(+)
 create mode 100644 capitulo5.txt

C:\Users\Usuario\romen-ejercicio-git-libro>git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

C:\Users\Usuario\romen-ejercicio-git-libro>git cherry-pick 1234abcd5678efgh
fatal: bad revision '1234abcd5678efgh'

C:\Users\Usuario\romen-ejercicio-git-libro>git log
commit 489fa11c914a9f34398fd4b5d8b338d0fa24bbe7 (HEAD -> main)
Author: PRORIX <romengilberto08@gmail.com>
Date:   Wed Nov 20 22:47:02 2024 +0000

    Agregado el cambio sencillo

commit a12989ee6796ebd8fb10374c441ac956a96a0fa1 (tag: 1.0.1, origin/main, origin/HEAD)
Author: Romén Gilberto García Gómez <romengilberto08@gmail.com>
Date:   Thu Oct 10 19:53:34 2024 +0100

    README.md

commit 22486f830f8e4d2f28e8be6c9903baf91e459e5a (tag: 1.0.0)
Merge: 4748a66 6f9db3b
Author: PRORIX <romengilberto08@gmail.com>
Date:   Thu Oct 10 19:48:55 2024 +0100

    Solucionado conflicto bibliografía.

commit 4748a66765431e7118598582632866620049cb94
Author: PRORIX <romengilberto08@gmail.com>
Date:   Thu Oct 10 19:47:15 2024 +0100

    Añadida nueva referencia bibliográfica.

commit 6f9db3bd23af96770b2ff8c2459db345e99735b8
Author: PRORIX <romengilberto08@gmail.com>
Date:   Thu Oct 10 19:41:59 2024 +0100

    Añadida nueva referencia bibliográfica.

commit cbe775115d547e5ca59c802e3278a327ff95088b
Author: PRORIX <romengilberto08@gmail.com>
Date:   Thu Oct 10 19:01:40 2024 +0100

    Añadido capítulo 4.

commit 6f947d0e9037951d8d62ee56264cf3654079c29b
Author: PRORIX <romengilberto08@gmail.com>
Date:   Thu Oct 10 18:43:47 2024 +0100

    Se crea el indice

commit da4a11809221453ecfec6c0d843c9e63ce486a27
Author: PRORIX <romengilberto08@gmail.com>
Date:   Thu Oct 10 18:37:22 2024 +0100

    Añadido capítulo 3.

commit 192caf3615a3e29f0d366d97997b9b6a40014fbd
Author: PRORIX <romengilberto08@gmail.com>
Date:   Thu Oct 10 18:31:28 2024 +0100

    Añadido capítulo 2.

commit 51094a24170be1bfdc4ccf65ca98c4da5183eaa4
Author: PRORIX <romengilberto08@gmail.com>
Date:   Thu Oct 10 18:21:33 2024 +0100

    Añadido capítulo 1.

commit e269d4abed3e98ffae77eb490927d323eabdb54b
Author: Romén Gilberto García Gómez <romengilberto08@gmail.com>
Date:   Thu Oct 10 18:02:25 2024 +0100

    Initial commit
(END)

```

## Ejercicio 4
### Hacemos un cambio en la rama main, comparamos los cambios.

```bash

C:\Users\Usuario\romen-ejercicio-git-libro>echo "Este es el proyecto donde gestionamos múltiples ramas con Git." >> README.md

C:\Users\Usuario\romen-ejercicio-git-libro>git add README.md

C:\Users\Usuario\romen-ejercicio-git-libro>git commit -m "Añadida una breve descripción en README.md"
[main eece686] Añadida una breve descripción en README.md
 1 file changed, 1 insertion(+)

C:\Users\Usuario\romen-ejercicio-git-libro>git diff main..nueva-funcionalidad
diff --git a/README.md b/README.md
index d4476c2..2626a2b 100644
--- a/README.md
+++ b/README.md
@@ -279,4 +279,3 @@ bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$
 * 192caf3 Añadido capítulo 2.
 :
 ```
-"Este es el proyecto donde gestionamos m<A3>ltiples ramas con Git."
diff --git a/capitulo5.txt b/capitulo5.txt
new file mode 100644
index 0000000..7a9a46e
--- /dev/null
+++ b/capitulo5.txt
@@ -0,0 +1 @@
+"En este cap<A1>tulo veremos c<A2>mo gestionar m<A3>ltiples ramas en Git."

C:\Users\Usuario\romen-ejercicio-git-libro>git diff nueva-funcionalidad..main
diff --git a/README.md b/README.md
index 2626a2b..d4476c2 100644
--- a/README.md
+++ b/README.md
@@ -279,3 +279,4 @@ bae2@jpexposito-VirtualBox:~/Escritorio/Repositorios/romen-ejercicio-git-libro$
 * 192caf3 Añadido capítulo 2.
 :
 ```
+"Este es el proyecto donde gestionamos m<A3>ltiples ramas con Git."
diff --git a/capitulo5.txt b/capitulo5.txt
deleted file mode 100644
index 7a9a46e..0000000
--- a/capitulo5.txt
+++ /dev/null
@@ -1 +0,0 @@
-"En este cap<A1>tulo veremos c<A2>mo gestionar m<A3>ltiples ramas en Git."

```

## Ejercicio 5
### Creamos un conflicto de fusion, hacemos un merge y realizamos un commit una vez resuelto

```hash
C:\Users\Usuario\romen-ejercicio-git-libro>git checkout main
Already on 'main'
Your branch is ahead of 'origin/main' by 2 commits.
  (use "git push" to publish your local commits)

C:\Users\Usuario\romen-ejercicio-git-libro>echo "Este es el contenido en la rama main." > capitulo2.txt


C:\Users\Usuario\romen-ejercicio-git-libro>git add capitulo2.txt

C:\Users\Usuario\romen-ejercicio-git-libro>git commit -m "Modificado capitulo2.txt en main"
[main 4a9f933] Modificado capitulo2.txt en main
 1 file changed, 1 insertion(+)
 create mode 100644 capitulo2.txt

C:\Users\Usuario\romen-ejercicio-git-libro>git checkout nueva-funcionalidad
Switched to branch 'nueva-funcionalidad'

C:\Users\Usuario\romen-ejercicio-git-libro>echo "Este es el contenido en la rama nueva-funcionalidad." > capitulo2.txt

C:\Users\Usuario\romen-ejercicio-git-libro>git add capitulo2.txt

C:\Users\Usuario\romen-ejercicio-git-libro>git commit -m "Modificado capitulo2.txt en nueva-funcionalidad"
[nueva-funcionalidad 4277d04] Modificado capitulo2.txt en nueva-funcionalidad
 1 file changed, 1 insertion(+)
 create mode 100644 capitulo2.txt

C:\Users\Usuario\romen-ejercicio-git-libro>git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 3 commits.
  (use "git push" to publish your local commits)

C:\Users\Usuario\romen-ejercicio-git-libro>git merge nueva-funcionalidad
Auto-merging capitulo2.txt
CONFLICT (add/add): Merge conflict in capitulo2.txt
Automatic merge failed; fix conflicts and then commit the result.

C:\Users\Usuario\romen-ejercicio-git-libro>git add capitulo2.txt

C:\Users\Usuario\romen-ejercicio-git-libro>git commit -m "Resuelto conflicto de fusión en capitulo2.txt"
[main 15c90a7] Resuelto conflicto de fusión en capitulo2.txt

```

## Ejercicio 6
### Realizamos un merge de la nueva rama en main, y hacemos revert

```hash
C:\Users\Usuario\romen-ejercicio-git-libro>git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 3 commits.
  (use "git push" to publish your local commits)

C:\Users\Usuario\romen-ejercicio-git-libro>git merge nueva-funcionalidad
Auto-merging capitulo2.txt
CONFLICT (add/add): Merge conflict in capitulo2.txt
Automatic merge failed; fix conflicts and then commit the result.

C:\Users\Usuario\romen-ejercicio-git-libro>git add capitulo2.txt

C:\Users\Usuario\romen-ejercicio-git-libro>git commit -m "Resuelto conflicto de fusión en capitulo2.txt"
[main 15c90a7] Resuelto conflicto de fusión en capitulo2.txt

C:\Users\Usuario\romen-ejercicio-git-libro>git checkout main
Already on 'main'
Your branch is ahead of 'origin/main' by 6 commits.
  (use "git push" to publish your local commits)

C:\Users\Usuario\romen-ejercicio-git-libro>git merge nueva-funcionalidad
Already up to date.

```

## Ejercicio 7
### Eliminar una etiqueta

```hash
C:\Users\Usuario\romen-ejercicio-git-libro>git tag -d

C:\Users\Usuario\romen-ejercicio-git-libro>git push origin :refs/tags/<1.0.0>
La sintaxis del comando no es correcta.

C:\Users\Usuario\romen-ejercicio-git-libro>git push origin
Enumerating objects: 20, done.
Counting objects: 100% (20/20), done.
Delta compression using up to 12 threads
Compressing objects: 100% (16/16), done.
Writing objects: 100% (18/18), 1.94 KiB | 991.00 KiB/s, done.
Total 18 (delta 6), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (6/6), completed with 1 local object.
To https://github.com/PRORIX/romen-ejercicio-git-libro
   a12989e..15c90a7  main -> main

```

## Ejercicio 8
### Haz un commit en la rama main y luego restablece el estado del repositorio al commit anterior utilizando git reset --hard.

```hash

C:\Users\Usuario\romen-ejercicio-git-libro>git commit -m "Ejercicio terminado"
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean

C:\Users\Usuario\romen-ejercicio-git-libro>git reset --hard
HEAD is now at 15c90a7 Resuelto conflicto de fusión en capitulo2.txt

```
