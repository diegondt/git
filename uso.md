# Flujo de trabajo en Git

Imaginemos un escenario en el que iniciamos un proyecto en el que solo vamos a trabajar nosotros. En este caso, el flujo de trabajo es muy sencillo:

1. Creamos una carpeta para el proyecto.
2. Inicializamos un repositorio de Git con `git init`.
3. Hacemos cambios en el repositorio, crear archivos, modificarlos, eliminarlos, etc.
4. Añadimos los cambios al área de preparación con `git add <file>`.
5. Confirmamos los cambios con `git commit -m <mensaje>`.

```mermaid
graph TD
    subgraph "Terminal"
        0[mkdir proyecto] --> 1[git init]
        1 --> 2[nano README.md]
        2 --> 3[git add README.md]
        3 --> 4["git commit-m 'Edit README.md'"]
        4 --> 2
    end
    subgraph "Carpeta del proyecto"
        A[Crear carpeta] --> B[Inicializar repositorio]
        B --> C[Modificar archivos]
        C --> D[Añadir cambios al área de preparación]
        D --> E[Confirmar cambios]
        E --> C
    end
```

## Estructura de cambios en el repositorio

Los cambios se representan como una rama en la historia del proyecto:

```mermaid
    %%{init: { 'logLevel': 'debug', 'theme': 'forest' , 'themeVariables': {
              'commitLabelFontSize': '16px'
       } } }%%
gitGraph:
commit id: "Creamos README.md"
commit id: "Añadimos descripcion del proyecto"
commit id: "Hola mundo en python"
commit id: "Descargamos dependencias"
commit id: "Añadimos archivo de configuración"
commit id: "Feat: script para llamar a la API"
```

## Ramas en Git

Hemos visto como los cambios se acumulan en una rama en la historia del proyecto. En Git, las ramas son una forma de separar el flujo de trabajo en diferentes líneas de tiempo. Por defecto, Git crea una rama principal llamada `main`. Sin embargo, podemos crear nuevas ramas para trabajar en nuevas funcionalidades sin afectar el flujo de trabajo principal.

```mermaid
graph TD
    subgraph "Terminal"
        0[git branch feature]
        0 --> 1[git checkout feature]
        1 --> 2[nano script.py]
        2 --> 3[git add script.py]
        3 --> 4[git commit -m 'Feat: script para llamar a la API']
        4 --> 2
    end
    subgraph "Carpeta del proyecto"
        A[Crear rama feature] --> B[Cambiar a rama feature]
        B --> C[Modificar archivos]
        C --> D[Añadir cambios al área de preparación]
        D --> E[Confirmar cambios]
        E --> C
    end
```

## Fusionar ramas

Una vez que hemos terminado de trabajar en una rama, podemos fusionarla con la rama principal usando el comando `git merge <branch>`.

```mermaid
    %%{init: { 'logLevel': 'debug', 'theme': 'forest' , 'themeVariables': {
              'commitLabelFontSize': '16px'
       } } }%%
gitGraph:
commit id: "Creamos README.md"
commit id: "Añadimos descripcion del proyecto"
commit id: "Hola mundo en python"
branch feature
commit id: "Descargamos dependencias"
commit id: "Añadimos archivo de configuración"
commit id: "Feat: script para llamar a la API"
checkout main
merge feature
commit id: "Merge branch feature"
```

## Resolución de conflictos

En ocasiones, al fusionar dos ramas, puede haber conflictos entre los cambios realizados en ambas ramas. En este caso, Git nos pedirá que resolvamos los conflictos manualmente.

VSCode nos muestra los conflictos en los archivos afectados. Podemos resolverlos manualmente y luego confirmar los cambios.

Los conflictos pueden asustar, pero recordad que en realidad, solo teneis tres opciones:

1. Aceptar los cambios de la rama actual.
2. Aceptar los cambios de la rama a fusionar.
3. Modificar los cambios manualmente porque te interesa una mezcla de ambos o ninguno.

## TLDR

- Iniciamos con `git init`.
- Hacemos cambios en el repositorio con `git add` y `git commit`.
- Estos cambios se acumulan en una rama en la historia del proyecto.
- Podemos crear nuevas ramas para trabajar en nuevas funcionalidades con `git branch <branch>`.
- Podemos fusionar ramas con `git merge <branch>`.
- En caso de conflictos, resolvemos manualmente y confirmamos los cambios.

## Referencias y recursos

- [No Deep Shit Git](https://rogerdudler.github.io/git-guide/)
- [Learn Git Branching](https://learngitbranching.js.org/?locale=es_ES)
- [Git Visualizator](https://git-school.github.io/visualizing-git/)
- [Git guide](https://glasskube.dev/guides/git/)