# Preparación previa del participante

Completa esta lista antes del taller. Si un punto falla, resuélvelo con soporte antes de iniciar para no perder tiempo durante la práctica.

## 1. Cuenta de GitHub

- [ ] Abre `https://github.com` e inicia sesión.
  - **Qué debes ver:** tu avatar en la esquina superior derecha.
  - **Captura descrita:** página de GitHub con el avatar visible; no incluyas correo, tokens ni datos privados.
- [ ] Confirma el correo de tu cuenta si GitHub muestra un aviso.
  - **Qué debes ver:** ya no aparece el aviso de verificación.
- [ ] Abre `[AJUSTAR: URL del repositorio del taller]`.
  - **Qué debes ver:** el nombre del repositorio y su pestaña **Code**.

## 2. Acceso a la organización y al repositorio

- [ ] Acepta la invitación a `[AJUSTAR: nombre de la organización]`.
  - **Qué debes ver:** la organización en la sección **Your organizations** de tu perfil.
- [ ] Confirma que puedes leer el repositorio del taller.
  - **Qué debes ver:** los archivos `README.md` y `proyecto-base`.
- [ ] Confirma con el instructor si trabajarás en un repositorio personal o en uno de la organización.
  - **Qué debes ver:** una indicación clara del repositorio que usarás.

Un repositorio personal pertenece a tu cuenta. Un repositorio de organización pertenece al equipo y puede tener reglas adicionales, como revisiones obligatorias o ramas protegidas.

## 3. GitHub Copilot

- [ ] Confirma que tu cuenta tiene acceso a GitHub Copilot.
  - **Qué debes ver:** Copilot aparece disponible en GitHub o en la sección de suscripción de tu cuenta.
- [ ] Instala o habilita la extensión **GitHub Copilot** en VS Code.
  - **Qué debes ver:** la extensión aparece como **Enabled**.
- [ ] Abre el panel de Chat de Copilot.
  - **Qué debes ver:** un campo donde puedes escribir una solicitud.
- [ ] Escribe el siguiente mensaje de prueba:

> **Prompt para Copilot**
>
> Explica en una frase la diferencia entre Git y GitHub para una persona que nunca los ha usado.

  - **Qué debes ver:** una respuesta de Copilot. No importa que las palabras exactas cambien.

## 4. VS Code y Git

- [ ] Abre VS Code.
  - **Qué debes ver:** la ventana principal del editor.
- [ ] Abre **Terminal > New Terminal**.
  - **Qué debes ver:** una terminal en la parte inferior.
- [ ] Ejecuta:

```powershell
git --version
```

  - **Qué debes ver:** una respuesta parecida a `git version 2.x.x`.
- [ ] Ejecuta:

```powershell
git config --global user.name
```

  - **Qué debes ver:** tu nombre. Si no aparece, solicita apoyo.
- [ ] Ejecuta:

```powershell
git config --global user.email
```

  - **Qué debes ver:** el correo asociado a tus commits. Puede ser el correo privado `noreply` de GitHub.

## 5. Extensión para Pull Requests

- [ ] Instala o habilita **GitHub Pull Requests** en VS Code.
  - **Qué debes ver:** la extensión aparece como **Enabled**.
- [ ] Inicia sesión en GitHub desde VS Code si aparece la solicitud.
  - **Qué debes ver:** tu cuenta conectada en el menú de cuentas.

## 6. Prueba de clonación

Haz esta prueba sólo cuando el instructor haya compartido el repositorio.

- [ ] En GitHub, abre el repositorio y selecciona **Code > Local > HTTPS**.
  - **Qué debes ver:** una dirección que termina en `.git`.
- [ ] Copia la dirección.
  - **Qué debes ver:** GitHub confirma que se copió.
- [ ] En VS Code, abre la paleta con `Ctrl+Shift+P`.
  - **Qué debes ver:** un cuadro de búsqueda de comandos.
- [ ] Ejecuta **Git: Clone**.
  - **Qué debes ver:** VS Code solicita la dirección del repositorio.
- [ ] Pega la dirección y selecciona una carpeta de trabajo.
  - **Qué debes ver:** comienza la descarga.
- [ ] Selecciona **Open** cuando VS Code pregunte si deseas abrir el repositorio.
  - **Qué debes ver:** los archivos del taller en el explorador.
- [ ] Abre una terminal y ejecuta:

```powershell
git status
```

  - **Qué debes ver:** `On branch main` y `working tree clean`, o sus equivalentes en español.

## 7. Vista previa del sitio

- [ ] Abre `proyecto-base/index.html` desde el explorador de archivos de Windows.
  - **Qué debes ver:** una página de Mercado Nube con encabezado, espacio de productos y pie de página.

No necesitas instalar un servidor. Después de cada cambio, guarda el archivo y actualiza el navegador.

## Criterio de “listo”

Estás listo cuando cumples todo lo siguiente:

- [ ] puedes entrar a GitHub;
- [ ] puedes abrir el repositorio asignado;
- [ ] Copilot responde en VS Code;
- [ ] `git --version` muestra una versión;
- [ ] `git status` funciona dentro del repositorio;
- [ ] puedes abrir `proyecto-base/index.html` en el navegador.

Si falta cualquiera de estos puntos, comparte con soporte el mensaje exacto que ves. Nunca compartas contraseñas, códigos de autenticación ni tokens.
