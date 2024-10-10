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
