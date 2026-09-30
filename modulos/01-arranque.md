# 01. Arranque — equipo listo y repositorio creado

## 1. Objetivo del bloque

Crear el repositorio de la pareja desde la plantilla, compartirlo, clonarlo y comprobar que el entorno está listo.

## 2. Qué vas a lograr aquí

- Tendrán un repositorio exclusivo para las dos personas del equipo.
- Ambas personas tendrán una copia local conectada con GitHub.
- Identificarás el repositorio, el directorio de trabajo, el staging y el historial.
- Abrirás el sitio base y confirmarás tu rama actual.

## 3. Concepto

Un control de versiones funciona como el historial de un documento, pero está diseñado para equipos y proyectos completos. Permite saber qué cambió, quién lo hizo y cuándo, además de recuperar versiones anteriores.

**Git** es la herramienta que registra cambios en tu computadora. **GitHub** es el servicio donde el equipo aloja el repositorio, conversa sobre cambios y aplica reglas. Puedes usar Git sin GitHub, pero en este taller los usaremos juntos.

Un **repositorio** es la carpeta del proyecto más su historial. Dentro de tu copia local hay tres espacios:

- el **working directory** o directorio de trabajo, que es la mesa donde editas;
- el **staging area** o área de preparación, que es la caja donde eliges lo que incluirás;
- el **historial**, que contiene paquetes cerrados llamados commits.

El repositorio central del taller es una **plantilla**: sirve para crear copias independientes con la misma estructura. Cada pareja tendrá su propio repositorio, propiedad de una persona y compartido con la otra como colaboradora. Así pueden provocar conflictos y revisar Pull Requests sin interferir con los otros 19 equipos.

**Clonar** significa descargar una copia con su historial y dejarla conectada al repositorio remoto del equipo en GitHub.

## 4. Manos a la obra

1. Formen la pareja indicada por el instructor y definan quién será la persona A y quién la persona B.
   - **Qué debes ver:** dos roles claros; la persona A creará el repositorio.
2. La persona A abre `https://github.com/alemcuevas/github-essentials-workshop`.
   - **Qué debes ver:** el repositorio de ejemplo y el botón **Use this template**.
3. La persona A selecciona **Use this template > Create a new repository**.
   - **Qué debes ver:** el formulario para crear un repositorio desde la plantilla.
4. La persona A escribe un nombre como `contoso-retail-ana-luis`, elige visibilidad pública y crea el repositorio.
   - **Qué debes ver:** un repositorio nuevo bajo la cuenta de la persona A con los archivos del taller.
5. La persona A abre **Settings > Collaborators > Add people** e invita a la persona B.
   - **Qué debes ver:** la invitación aparece como pendiente.
6. La persona B acepta la invitación desde GitHub o su correo.
   - **Qué debes ver:** la persona B aparece como colaboradora del repositorio del equipo.
7. La persona A selecciona **Code > Local > HTTPS** en el repositorio del equipo.
   - **Qué debes ver:** una dirección del repositorio del equipo que termina en `.git`.
8. Ambas personas clonan esa dirección mediante `Ctrl+Shift+P` y **Git: Clone**.
   - **Qué debes ver:** VS Code descarga el mismo repositorio en cada computadora.
9. Ambas personas seleccionan **Open**.
   - **Qué debes ver:** `README.md`, `proyecto-base`, `modulos` y `recursos` en el explorador.
10. Ambas personas abren **Terminal > New Terminal**.
   - **Qué debes ver:** la terminal ubicada en la carpeta del repositorio.
11. Ambas personas ejecutan:

```powershell
git status
```

   - **Qué debes ver:** la rama `main` y un directorio de trabajo limpio.
12. Ambas personas ejecutan:

```powershell
git remote -v
```

   - **Qué debes ver:** `origin` apunta al repositorio del equipo, no al repositorio de ejemplo.
13. La persona A crea y publica la rama compartida:

```powershell
git switch -c dev
git push -u origin dev
git switch main
```

   - **Qué debes ver:** `dev` aparece en GitHub y la persona A regresa a `main`.
14. La persona B ejecuta:

```powershell
git fetch origin
git switch dev
git switch main
```

   - **Qué debes ver:** la persona B puede cambiar a `dev` y regresar a `main`.
15. Ambas personas ejecutan:

```powershell
git log --oneline -3
```

   - **Qué debes ver:** hasta tres commits con identificador corto y mensaje.
16. Ambas personas abren `proyecto-base/index.html` en su navegador.
   - **Qué debes ver:** el sitio Contoso Retail con encabezado, banner y secciones incompletas.

## 5. Prompt sugerido para Copilot

> **Prompt para Copilot**
>
> Explícame la salida de `git status` línea por línea. Dime en qué rama estoy, si tengo cambios y qué significa cada estado. No ejecutes comandos.

## 6. Punto de control

Pueden avanzar si ambos están en `main`, `origin` apunta al repositorio de la pareja, `dev` existe en GitHub y el sitio abre.

## 7. Si algo falla

- **La persona B no puede hacer push:** confirma que aceptó la invitación y aparece en **Settings > Collaborators**.
- **`origin` apunta a `github-essentials-workshop`:** clonaste la plantilla en vez del repositorio del equipo; vuelve a clonar la URL correcta.
- **`git status` dice que no es un repositorio:** abre en VS Code la carpeta clonada, no su carpeta superior.

## 8. Para profundizar

Ejecuta `git log --oneline --graph --decorate --all` y pide a Copilot que explique cada símbolo del grafo.
