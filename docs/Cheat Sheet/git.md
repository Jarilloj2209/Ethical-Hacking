# Git Cheatsheet

> Guía rápida de comandos esenciales de Git para versionamiento de notas, documentación y proyectos del curso.

!!! tip "Objetivo"
Entender qué hace cada comando antes de ejecutarlo y construir un workflow consistente.

---

## Flujo mental de Git

```text
Editar archivos
        ↓
git add .
        ↓
git commit -m "mensaje"
        ↓
git push
        ↓
GitHub
```

!!! info "Piensa en Git así"
- `git add` → **Seleccionar cambios**
- `git commit` → **Guardar checkpoint**
- `git push` → **Subir cambios a GitHub**

---

## Configuración inicial

=== "Verificar instalación"

````
```bash
git --version
```

Verifica si Git está instalado correctamente.
````

=== "Configurar usuario"

````
```bash
git config --global user.name "Tu Nombre"
git config --global user.email "correo@ejemplo.com"
```

Esto asocia tus commits a una identidad.
````

=== "Ver configuración"

````
```bash
git config --list
```

Muestra toda la configuración activa.
````

??? question "¿Por qué importa configurar el usuario?"
GitHub usa estos datos para asociar los commits a tu cuenta.

---

## Inicializar un repositorio

### Crear repositorio Git

```bash
cd ethical-hacking-notes
git init
```

!!! success "Resultado"
La carpeta se convierte en un repositorio Git.

### Ver estado actual

```bash
git status
```

Ejemplo de salida:

```text
On branch main
Changes not staged for commit:
modified: docs/index.md
```

| Estado      | Significado                 |
| ----------- | --------------------------- |
| `untracked` | Git detectó archivos nuevos |
| `modified`  | Archivo editado             |
| `staged`    | Listo para commit           |

---

## Agregar cambios (`git add`)

### Agregar todo

```bash
git add .
```

!!! tip "Uso recomendado"
Ideal para proyectos personales como tus notas de MkDocs.

### Agregar un archivo específico

```bash
git add docs/cheatsheets/git.md
```

### Agregar una carpeta

```bash
git add docs/
```

??? example "Ejemplo práctico"
Modificaste:

````
- `docs/index.md`
- `docs/cheatsheets/git.md`

Entonces:

```bash
git add .
```
````

---

## Guardar cambios (`git commit`)

### Crear commit

```bash
git commit -m "Add Git cheatsheet"
```

!!! note "¿Qué es un commit?"
Un commit es un **checkpoint** de tu proyecto.

### Buenos vs malos commits

=== "✅ Buenos"

````
```bash
git commit -m "Add Linux cheatsheet"
git commit -m "Update networking notes"
git commit -m "Fix dark mode"
```
````

=== "❌ Malos"

````
```bash
git commit -m "asdf"
git commit -m "fix"
git commit -m "cambio"
```
````

---

## Conectar con GitHub

### Agregar repositorio remoto

```bash
git remote add origin https://github.com/usuario/repositorio.git
```

### Verificar conexión

```bash
git remote -v
```

Resultado esperado:

```text
origin https://github.com/usuario/repositorio.git (fetch)
origin https://github.com/usuario/repositorio.git (push)
```

---

## Subir cambios (`git push`)

### Primer push

```bash
git branch -M main
git push -u origin main
```

!!! info "Explicación rápida"
- `origin` → repositorio remoto
- `main` → rama principal
- `-u` → recordar conexión

### Push normal

Después del primero:

```bash
git push
```

---

## Descargar cambios (`git pull`)

```bash
git pull
```

!!! warning "Antes de trabajar"
Si colaboras con otras personas, ejecuta `git pull` antes de empezar.

---

## Branches

=== "Ver ramas"

````
```bash
git branch
```
````

=== "Crear rama"

````
```bash
git branch nueva-seccion
```
````

=== "Cambiar rama"

````
```bash
git checkout nueva-seccion
```
````

=== "Crear y cambiar"

````
```bash
git checkout -b nueva-seccion
```
````

??? question "¿Cuándo usar ramas?"
Cuando harás cambios grandes y no quieres romper la versión principal.

---

## Historial

### Ver historial completo

```bash
git log
```

### Historial resumido

```bash
git log --oneline
```

Ejemplo:

```text
ab12cd Add phishing notes
34ef56 Update dark mode
78gh90 Initial commit
```

---

## Workflow recomendado del curso

```mermaid
graph TD
A[Editar notas] --> B[git status]
B --> C[git add .]
C --> D[git commit -m "mensaje"]
D --> E[git push]
E --> F[GitHub Pages actualizado]
```

### Secuencia diaria

```bash
git status
git add .
git commit -m "Add OSINT notes"
git push
```

!!! success "Regla práctica"
Haz **commits pequeños y frecuentes**. Son más fáciles de entender y revertir.

---

## Comandos más usados

| Acción            | Comando                   |
| ----------------- | ------------------------- |
| Ver estado        | `git status`              |
| Agregar todo      | `git add .`               |
| Commit            | `git commit -m "mensaje"` |
| Subir cambios     | `git push`                |
| Descargar cambios | `git pull`                |
| Historial         | `git log --oneline`       |
| Ver ramas         | `git branch`              |

!!! abstract "Resumen"
Git se vuelve simple cuando lo piensas así:

```
`Editar → Add → Commit → Push`
```
