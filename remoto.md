# Repositorios remotos

Git es un sistema de control de versiones distribuido. Esto significa que podemos trabajar en un proyecto de forma colaborativa con otras personas. Para ello, necesitamos un repositorio remoto en el que se almacenen los cambios que hagamos en nuestro proyecto.

## Crear un repositorio remoto

Para crear un repositorio remoto, necesitamos una cuenta en una plataforma de alojamiento de repositorios. Algunas de las más populares son:

- [GitHub](https://github.com)
- [GitLab](https://gitlab.com)
- [Bitbucket](https://bitbucket.org)

Durante el curso utilizaremos GitHub, pero los comandos que veremos a continuación son válidos para cualquier plataforma.

## Comandos básicos para trabajar con repositorios remotos

### `git remote`

El comando `git remote` nos permite ver los repositorios remotos que tenemos configurados en nuestro repositorio local.

```bash
git remote -v
```

### `git remote add`

El comando `git remote add` nos permite añadir un repositorio remoto a nuestro repositorio local.

```bash
git remote add origin
```

### `git push`

El comando `git push` nos permite subir los cambios de nuestro repositorio local al repositorio remoto.

```bash
git push origin main
```

### `git pull`

El comando `git pull` nos permite descargar los cambios del repositorio remoto a nuestro repositorio local, si queremos especificar la rama de la que queremos descargar los cambios, podemos hacerlo de la siguiente manera:

```bash
git pull origin main
```

### `git clone`

El comando `git clone` nos permite clonar un repositorio remoto en nuestro disco duro.

```bash
git clone
```

## gh

GitHub CLI es una herramienta que nos permite trabajar con GitHub desde la línea de comandos. Para instalarla, podemos hacerlo de la siguiente manera:

```bash
sudo apt install gh
```

Una vez instalada, podemos autenticarnos con nuestra cuenta de GitHub:

```bash
gh auth login
```

Nos pedirá que introduzcamos nuestras credenciales de GitHub y nos generará un token de autenticación.

Algunos comandos utiles con gh

```bash
gh repo list
gh repo clone <user>/<repo>
gh repo create <repo>
gh repo delete <user>/<repo>
gh pr list
gh pr create
gh pr checkout <pr>
gh pr merge <pr>
gh gist list
gh gist create
gh gist delete <id>
gh gist clone <id>
```

## Ramas en repositorios remotos

Las ramas en los repositorios remotos funcionan de la misma manera que en los repositorios locales. 
Es importante trabajar con ramas para separar el flujo de trabajo y evitar conflictos al fusionar los cambios.

Cuando subas cambios a un repositorio remoto desde una rama local, puedes hacer un *pull request* para fusionar los cambios en la rama principal del repositorio remoto.

