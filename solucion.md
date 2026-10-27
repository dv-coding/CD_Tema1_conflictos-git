## Ejercicio 3 — Resolución de conflictos

**Enlace al repositorio:** [https://github.com/dv-coding/CD_Tema1_conflictos-git](https://github.com/dv-coding/CD_Tema1_conflictos-git)

**Salida del terminal:**

```bash
dev@VM-W11DEV UCRT64 /c/DAM/ED/CD_Tema1_conflictos-git
$ git init -b main
Initialized empty Git repository in C:/DAM/ED/CD_Tema1_conflictos-git/.git/

dev@VM-W11DEV UCRT64 /c/DAM/ED/CD_Tema1_conflictos-git (main)
$ echo 'Hola desde main' > mensaje.txt

dev@VM-W11DEV UCRT64 /c/DAM/ED/CD_Tema1_conflictos-git (main)
$ git add mensaje.txt
warning: in the working copy of 'mensaje.txt', LF will be replaced by CRLF the next time Git touches it

dev@VM-W11DEV UCRT64 /c/DAM/ED/CD_Tema1_conflictos-git (main)
$ git commit -m 'Se crea fichero mensaje.txt con el saludo inicial'
[main (root-commit) 1db5c78] Se crea fichero mensaje.txt con el saludo inicial
 1 file changed, 1 insertion(+)
 create mode 100644 mensaje.txt

dev@VM-W11DEV UCRT64 /c/DAM/ED/CD_Tema1_conflictos-git (main)
$ git switch -c feature/nuevo-saludo
Switched to a new branch 'feature/nuevo-saludo'

dev@VM-W11DEV UCRT64 /c/DAM/ED/CD_Tema1_conflictos-git (feature/nuevo-saludo)
$ echo 'Hola desde la nueva rama' > mensaje.txt

dev@VM-W11DEV UCRT64 /c/DAM/ED/CD_Tema1_conflictos-git (feature/nuevo-saludo)
$ git commit -am 'Se modifica el saludo en la rama de la nueva feature'
warning: in the working copy of 'mensaje.txt', LF will be replaced by CRLF the next time Git touches it
[feature/nuevo-saludo 1ab848b] Se modifica el saludo en la rama de la nueva feature
 1 file changed, 1 insertion(+), 1 deletion(-)

dev@VM-W11DEV UCRT64 /c/DAM/ED/CD_Tema1_conflictos-git (feature/nuevo-saludo)
$ git switch main
Switched to branch 'main'

dev@VM-W11DEV UCRT64 /c/DAM/ED/CD_Tema1_conflictos-git (main)
$ echo 'Hola, mundo!' > mensaje.txt

dev@VM-W11DEV UCRT64 /c/DAM/ED/CD_Tema1_conflictos-git (main)
$ git commit -am 'Se actualiza el saludo en la rama principal'
warning: in the working copy of 'mensaje.txt', LF will be replaced by CRLF the next time Git touches it
[main 2c166c3] Se actualiza el saludo en la rama principal
 1 file changed, 1 insertion(+), 1 deletion(-)

dev@VM-W11DEV UCRT64 /c/DAM/ED/CD_Tema1_conflictos-git (main)
$ git merge feature/nuevo-saludo
Auto-merging mensaje.txt
CONFLICT (content): Merge conflict in mensaje.txt
Automatic merge failed; fix conflicts and then commit the result.

dev@VM-W11DEV UCRT64 /c/DAM/ED/CD_Tema1_conflictos-git (main|MERGING)
$ cat mensaje.txt
<<<<<<< HEAD
Hola, mundo!
=======
Hola desde la nueva rama
>>>>>>> feature/nuevo-saludo

dev@VM-W11DEV UCRT64 /c/DAM/ED/CD_Tema1_conflictos-git (main|MERGING)
$ echo 'Hola, mundo!' > mensaje.txt

dev@VM-W11DEV UCRT64 /c/DAM/ED/CD_Tema1_conflictos-git (main|MERGING)
$ cat mensaje.txt
Hola, mundo!

dev@VM-W11DEV UCRT64 /c/DAM/ED/CD_Tema1_conflictos-git (main|MERGING)
$ git add mensaje.txt
warning: in the working copy of 'mensaje.txt', LF will be replaced by CRLF the next time Git touches it

dev@VM-W11DEV UCRT64 /c/DAM/ED/CD_Tema1_conflictos-git (main|MERGING)
$ git commit -m 'Se resuelve conflicto de merge conservando el texto de main'
[main bc0cba8] Se resuelve conflicto de merge conservando el texto de main

dev@VM-W11DEV UCRT64 /c/DAM/ED/CD_Tema1_conflictos-git (main)
$ git log --oneline --graph --all
*   bc0cba8 (HEAD -> main) Se resuelve conflicto de merge conservando el texto de main
|\
| * 1ab848b (feature/nuevo-saludo) Se modifica el saludo en la rama de la nueva feature
* | 2c166c3 Se actualiza el saludo en la rama principal
|/
* 1db5c78 Se crea fichero mensaje.txt con el saludo inicial

dev@VM-W11DEV UCRT64 /c/DAM/ED/CD_Tema1_conflictos-git (main)
$ git remote add origin https://github.com/dv-coding/CD_Tema1_conflictos-git

dev@VM-W11DEV UCRT64 /c/DAM/ED/CD_Tema1_conflictos-git (main)
$ git push -u origin main
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 2 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (10/10), 971 bytes | 323.00 KiB/s, done.
Total 10 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To https://github.com/dv-coding/CD_Tema1_conflictos-git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.

dev@VM-W11DEV UCRT64 /c/DAM/ED/CD_Tema1_conflictos-git (main)
$ git push --all origin
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
remote:
remote: Create a pull request for 'feature/nuevo-saludo' on GitHub by visiting:
remote:      https://github.com/dv-coding/CD_Tema1_conflictos-git/pull/new/feature/nuevo-saludo
remote:
To https://github.com/dv-coding/CD_Tema1_conflictos-git
 * [new branch]      feature/nuevo-saludo -> feature/nuevo-saludo
```