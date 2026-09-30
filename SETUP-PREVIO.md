# Preparación previa del participante

Completa esta lista antes del taller. Si un punto falla, resuélvelo con soporte antes de iniciar para no perder tiempo durante la práctica.

## 1. Cuenta de GitHub

- [ ] Abre `https://github.com` e inicia sesión.
  - **Qué debes ver:** tu avatar en la esquina superior derecha.
  - **Captura descrita:** página de GitHub con el avatar visible; no incluyas correo, tokens ni datos privados.
- [ ] Confirma el correo de tu cuenta si GitHub muestra un aviso.
  - **Qué debes ver:** ya no aparece el aviso de verificación.
- [ ] Abre `https://github.com/alemcuevas/github-essentials-workshop`.
  - **Qué debes ver:** el nombre del repositorio y su pestaña **Code**.

## 2. Pareja y acceso a la plantilla

- [ ] Confirma quién será tu compañero de equipo.
  - **Qué debes ver:** el nombre de las dos personas registrado por el instructor.
- [ ] Confirma que ambos pueden leer el repositorio de ejemplo.
  - **Qué debes ver:** los archivos `README.md` y `proyecto-base`.
- [ ] Acuerden quién será la persona propietaria del repositorio del equipo.
  - **Qué debes ver:** una persona responsable de seleccionar **Use this template** durante el bloque 1.
- [ ] Escriban el nombre que usarán para el repositorio.
  - **Qué debes ver:** un nombre como `contoso-retail-ana-luis`, en minúsculas y sin espacios.

El repositorio de ejemplo sólo contiene la plantilla y las instrucciones. Cada pareja creará su propio repositorio, agregará a ambas personas y hará ahí todos los ejercicios.

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

## 6. Preparación para clonar

La clonación real ocurrirá en el bloque 1, después de crear el repositorio del equipo.

- [ ] En VS Code, abre la paleta con `Ctrl+Shift+P`.
  - **Qué debes ver:** un cuadro de búsqueda de comandos.
- [ ] Escribe `Git: Clone` sin ejecutarlo.
  - **Qué debes ver:** el comando **Git: Clone** está disponible.
- [ ] Cierra la paleta con `Esc`.
- [ ] Crea una carpeta local vacía donde guardarás el repositorio del equipo.
  - **Qué debes ver:** conoces la ubicación que seleccionarás durante el taller.
- [ ] En una terminal fuera de cualquier repositorio, ejecuta:

```powershell
git --version
```

  - **Qué debes ver:** la versión de Git.

## 7. Vista previa del sitio

- [ ] Abre `proyecto-base/index.html` desde el explorador de archivos de Windows.
  - **Qué debes ver:** una página de Contoso Retail con encabezado, espacio de productos y pie de página.

No necesitas instalar un servidor. Después de cada cambio, guarda el archivo y actualiza el navegador.

## Criterio de “listo”

Estás listo cuando cumples todo lo siguiente:

- [ ] puedes entrar a GitHub;
- [ ] conoces a tu compañero y quién creará el repositorio;
- [ ] puedes abrir la plantilla del taller;
- [ ] Copilot responde en VS Code;
- [ ] `git --version` muestra una versión;
- [ ] el comando **Git: Clone** está disponible;
- [ ] puedes abrir `proyecto-base/index.html` en el navegador.

Si falta cualquiera de estos puntos, comparte con soporte el mensaje exacto que ves. Nunca compartas contraseñas, códigos de autenticación ni tokens.
