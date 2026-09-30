# Referencia rápida de comandos Git

Ejecuta los comandos dentro de la carpeta del repositorio. Antes de una operación importante, usa `git status`.

| Comando | Qué hace en español simple | Cuándo lo usas | Equivalente en VS Code o GitHub |
|---|---|---|---|
| `git --version` | Muestra si Git está disponible y su versión | Al preparar el entorno | No aplica |
| `git clone URL` | Descarga el repositorio y conecta `origin` | La primera vez que trabajas con el proyecto | Paleta: **Git: Clone** |
| `git status` | Muestra rama, cambios y operaciones pendientes | Antes y después de cada paso importante | Vista **Source Control** |
| `git branch --show-current` | Muestra sólo la rama actual | Antes de editar, commit o push | Nombre de rama en la barra inferior |
| `git remote -v` | Muestra los repositorios remotos configurados | Para confirmar a qué GitHub estás conectado | **Git: Show Git Output** ofrece contexto, pero no un equivalente exacto |
| `git diff` | Muestra cambios guardados que todavía no están en staging | Antes de preparar archivos | Source Control: seleccionar un archivo |
| `git diff --staged` | Muestra lo que entrará al próximo commit | Después de `add` y antes de `commit` | Sección **Staged Changes** |
| `git add archivo` | Prepara un archivo para el siguiente commit | Cuando revisaste y elegiste el cambio | Botón `+` junto al archivo |
| `git add archivo1 archivo2` | Prepara sólo los archivos indicados | Para mantener commits enfocados | Botón `+` en cada archivo |
| `git restore --staged archivo` | Retira un archivo de staging sin borrar su edición | Si preparaste algo por error | Botón `-` en **Staged Changes** |
| `git commit -m "mensaje"` | Registra los cambios preparados en el historial local | Cuando el cambio es coherente y está revisado | Campo de mensaje y botón **Commit** |
| `git log --oneline -5` | Muestra los últimos cinco commits en formato breve | Para confirmar historial y mensajes | Vista **Graph** o historial del archivo |
| `git log --oneline --all --graph --decorate -10` | Dibuja las ramas y sus commits recientes | Para entender cómo se relacionan | Vista **Graph** |
| `git fetch origin` | Consulta cambios de GitHub sin mezclarlos | Antes de comparar o actualizar | **Git: Fetch** |
| `git pull --ff-only` | Trae cambios sólo si puede avanzar sin crear un merge inesperado | Para actualizar una rama compartida | **Git: Pull**; la interfaz puede no aplicar `--ff-only` |
| `git push` | Publica commits en la rama remota asociada | Después de commits locales | **Sync Changes** o **Push** |
| `git push -u origin HEAD` | Publica la rama actual y configura seguimiento | La primera vez que publicas una rama | **Publish Branch** |
| `git switch nombre` | Cambia a una rama existente | Para moverte entre `dev` y una rama feature | Clic en el nombre de rama y seleccionar |
| `git switch -c feature/tu-nombre-apellido-descripcion` | Crea una rama personal y cambia a ella | Al iniciar una mejora desde una base actualizada | **Git: Create Branch** |
| `git branch -vv` | Muestra ramas locales y sus ramas remotas asociadas | Para diagnosticar seguimiento | No hay equivalente exacto |
| `git merge dev` | Integra `dev` en la rama actual | Para actualizar tu feature antes del PR | **Git: Merge Branch** |
| `git merge origin/dev` | Integra tu referencia más reciente de `dev` remoto | Después de `fetch`, sin cambiar de rama | **Git: Merge Branch** y elegir `origin/dev` |
| `git merge --abort` | Cancela un merge con conflicto y vuelve al estado anterior | Sólo si decides no resolver todavía y no hiciste otros cambios | Paleta: **Git: Abort Merge** |

## Secuencias frecuentes

### Iniciar una mejora

```powershell
git switch dev
git pull --ff-only
git switch -c feature/tu-nombre-apellido-descripcion
```

### Revisar y registrar

```powershell
git status
git diff
git add proyecto-base/index.html proyecto-base/styles.css
git diff --staged
git commit -m "Describe el resultado"
```

### Publicar por primera vez

```powershell
git push -u origin HEAD
```

### Actualizar antes de un Pull Request

```powershell
git fetch origin
git merge origin/dev
git push
```

## Comandos que no usamos como atajo

- Evita `git push --force`: puede sobrescribir trabajo remoto.
- Evita `git reset --hard`: puede eliminar cambios locales.
- Evita `git add .` sin revisar: puede incluir archivos ajenos o sensibles.
- No copies comandos de internet sin entender qué rama y qué archivos afectan.
