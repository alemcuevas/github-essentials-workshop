# 01. Arranque — entorno listo y repositorio creado

## 1. Objetivo del bloque

Clonar el repositorio, reconocer sus espacios principales y comprobar que tu entorno está listo.

## 2. Qué vas a lograr aquí

- Tendrás una copia local conectada con GitHub.
- Identificarás el repositorio, el directorio de trabajo, el staging y el historial.
- Abrirás el sitio base y confirmarás tu rama actual.

## 3. Concepto

Un control de versiones funciona como el historial de un documento, pero está diseñado para equipos y proyectos completos. Permite saber qué cambió, quién lo hizo y cuándo, además de recuperar versiones anteriores.

**Git** es la herramienta que registra cambios en tu computadora. **GitHub** es el servicio donde el equipo aloja el repositorio, conversa sobre cambios y aplica reglas. Puedes usar Git sin GitHub, pero en este taller los usaremos juntos.

Un **repositorio** es la carpeta del proyecto más su historial. Dentro de tu copia local hay tres espacios:

- el **working directory** o directorio de trabajo, que es la mesa donde editas;
- el **staging area** o área de preparación, que es la caja donde eliges lo que incluirás;
- el **historial**, que contiene paquetes cerrados llamados commits.

Un repositorio personal pertenece a una cuenta. Uno de organización pertenece al equipo y puede tener permisos, revisiones y ramas protegidas. **Clonar** significa descargar una copia con su historial y dejarla conectada al repositorio remoto en GitHub.

## 4. Manos a la obra

1. Abre `[AJUSTAR: URL del repositorio del taller]` en GitHub.
   - **Qué debes ver:** la pestaña **Code**, los archivos del taller y el propietario del repositorio.
2. Selecciona **Code > Local > HTTPS**.
   - **Qué debes ver:** una dirección que termina en `.git`.
3. Copia la dirección HTTPS.
   - **Qué debes ver:** GitHub confirma que la dirección se copió.
4. Abre VS Code.
   - **Qué debes ver:** la ventana principal del editor.
5. Abre la paleta con `Ctrl+Shift+P`.
   - **Qué debes ver:** el buscador de comandos.
6. Ejecuta **Git: Clone**.
   - **Qué debes ver:** VS Code solicita la dirección del repositorio.
7. Pega la dirección y elige una carpeta local.
   - **Qué debes ver:** una notificación de clonación.
8. Selecciona **Open**.
   - **Qué debes ver:** `README.md`, `proyecto-base`, `modulos` y `recursos` en el explorador.
9. Abre **Terminal > New Terminal**.
   - **Qué debes ver:** la terminal ubicada en la carpeta del repositorio.
10. Ejecuta:

```powershell
git status
```

   - **Qué debes ver:** la rama `main` y un directorio de trabajo limpio.
11. Ejecuta:

```powershell
git remote -v
```

   - **Qué debes ver:** un remoto llamado `origin` con la dirección del repositorio.
12. Ejecuta:

```powershell
git log --oneline -3
```

   - **Qué debes ver:** hasta tres commits con identificador corto y mensaje.
13. Abre `proyecto-base/index.html` en tu navegador.
   - **Qué debes ver:** el sitio Mercado Nube con encabezado, banner y secciones incompletas.

## 5. Prompt sugerido para Copilot

> **Prompt para Copilot**
>
> Explícame la salida de `git status` línea por línea. Dime en qué rama estoy, si tengo cambios y qué significa cada estado. No ejecutes comandos.

## 6. Punto de control

Puedes avanzar si `git status` muestra `main`, no hay cambios pendientes, `origin` aparece en `git remote -v` y el sitio abre en el navegador.

## 7. Si algo falla

- **Git solicita iniciar sesión:** completa la autenticación en el navegador y repite **Git: Clone**. Nunca pegues tu contraseña en el chat.
- **`git status` dice que no es un repositorio:** abre en VS Code la carpeta clonada, no su carpeta superior.
- **El HTML abre como texto:** ábrelo desde el explorador de Windows con un navegador.

## 8. Para profundizar

Ejecuta `git log --oneline --graph --decorate --all` y pide a Copilot que explique cada símbolo del grafo.
