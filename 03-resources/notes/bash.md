---
mocs:
    - "[[public-notes/03-resources/tools.moc.md|Tools & Environment]]"
tags:
    - dev/tools
---

- **Fundamentos**
    
    - Qué es Bash y diferencias con otras shells.
        
    - Navegación en el sistema (`ls`, `cd`, `pwd`).
        
    - Manejo de archivos y directorios (`cp`, `mv`, `rm`, `touch`, `mkdir`).
        
    - Permisos (`chmod`, `chown`).
        
- **Operadores y Redirecciones**
    
    - Redirecciones `>`, `>>`, `<`.
        
    - Pipes `|`.
        
    - Uso de `cat`, `less`, `head`, `tail`, `grep`, `awk`, `sed`.
        
- **Variables**
    
    - Variables de entorno (`$PATH`, `$HOME`).
        
    - Variables definidas por el usuario.
        
    - Expansión de variables y comillas (`"`, `'`, `` ` ``).
        
- **Control de flujo**
    
    - Condicionales (`if`, `else`, `elif`).
        
    - Operadores lógicos (`&&`, `||`).
        
    - Bucles (`for`, `while`, `until`).
        
    - `case`.
        
- **Funciones y Scripts**
    
    - Crear y ejecutar scripts (`#!/bin/bash`).
        
    - Funciones y parámetros (`$1`, `$2`, `$@`).
        
    - Variables locales y globales.
        
- **Gestión avanzada**
    
    - Procesos (`ps`, `kill`, `jobs`, `fg`, `bg`).
        
    - Manejo de señales (`trap`).
        
    - Cron jobs (automatización).
        
    - Debug de scripts (`set -x`, `bash -x script.sh`).
        
- **Buenas prácticas**
    
    - Manejo de errores (`set -e`, `|| exit 1`).
        
    - Escribir scripts portables.
        
    - Documentar con `#` y usar nombres claros.
# **hello world**
+ sha bang "#!"
	+ tell the os is a script that needs to be run by the interpreter located in the path `#!/bin/bash`
	+ `which bash` shows the location of the path
# **variables**
```bash
PRICE_PER_APPLE=5

# Encapsulating the variable name with ${} is used to avoid ambiguity

MyFirstLetters=ABC
echo "The first 10 letters in the alphabet are: ${MyFirstLetters}DEFGHIJ"

```

Variables can be assigned with the value of a command output. This is referred to as substitution. Substitution can be done by encapsulating the command with \`\` (known as back-ticks) or with $()

```bash
FILELIST=`ls`
```


# Arguments
+ Arguments can be passed to the script when it is executed, by writing them as a space-delimited list following the script file name.
+ Inside the script, the $1 variable references the first argument in the command line, $2 the second argument and so forth.
+ The variable $# holds the number of arguments passed to the script
+ The variable $# holds the number of arguments passed to the script

# Arrays
+ ```bash
my_array=(apple banana "Fruit Basket" orange)
```
+ The total number of elements in the array is referenced by ${#arrayname\[@]}