# Guía del estudiante

Esta guía contiene el paso a paso completo para terminar el taller de GitHub. Puedes seguirla durante la sesión o usarla para retomar el ejercicio por tu cuenta.

Construirás **Mercado Nube**, una tienda ficticia hecha únicamente con HTML y CSS. GitHub Copilot te ayudará a generar código; tú controlarás el flujo de Git y GitHub.

## Resultado final

Al terminar podrás explicar y ejecutar este recorrido:

```text
archivo local
    ↓
staging
    ↓
commit local
    ↓
push a GitHub
    ↓
Pull Request
    ↓
revisión y validaciones
    ↓
dev
    ↓
main
    ↓
[AJUSTAR: ambiente de producción]
```

## Antes de comenzar

Completa [SETUP-PREVIO.md](./SETUP-PREVIO.md). Debes tener:

- una cuenta activa de GitHub;
- acceso a GitHub Copilot;
- VS Code;
- las extensiones **GitHub Copilot** y **GitHub Pull Requests**;
- Git disponible;
- acceso a `[AJUSTAR: URL del repositorio del taller]`.

No necesitas instalar npm, JavaScript, frameworks ni dependencias.

## Cómo leer los pasos

Cada bloque contiene:

- **Acción:** lo que debes hacer;
- **Comando:** lo que debes ejecutar en la terminal;
- **Resultado esperado:** lo que debe aparecer si todo salió bien;
- **Punto de control:** la condición que debes cumplir antes de avanzar.

Ejecuta los comandos desde la carpeta del repositorio. No pegues varios comandos si todavía no entiendes el resultado del primero.

## Cuatro preguntas para no perderte

Cuando algo no funcione, responde:

1. ¿En qué rama estoy?
2. ¿Tengo cambios sin registrar?
3. ¿Mi commit existe sólo localmente o ya está en GitHub?
4. ¿Qué mensaje exacto muestra Git o GitHub?

Usa estos comandos:

```powershell
git branch --show-current
git status
git log --oneline -5
git remote -v
```

## Reglas de seguridad

- No subas contraseñas, tokens, llaves privadas ni datos personales.
- Revisa siempre el código que propone Copilot.
- No uses `git push --force`.
- No uses `git reset --hard` para intentar salir rápido de un problema.
- No trabajes directamente sobre `main`.
- Antes de cada commit, ejecuta `git status` y `git diff`.

---

# Bloque 1. Clonar y reconocer el entorno

## Meta

Tener una copia local del repositorio y reconocer dónde estás trabajando.

## Paso a paso

1. Abre `[AJUSTAR: URL del repositorio del taller]` en GitHub.
   - **Resultado esperado:** ves la pestaña **Code** y los archivos del taller.
2. Selecciona **Code > Local > HTTPS**.
   - **Resultado esperado:** aparece una dirección terminada en `.git`.
3. Copia esa dirección.
   - **Resultado esperado:** GitHub confirma que se copió.
4. Abre VS Code.
5. Presiona `Ctrl+Shift+P`.
6. Ejecuta **Git: Clone**.
7. Pega la dirección del repositorio.
8. Elige una carpeta local.
9. Selecciona **Open** cuando VS Code lo solicite.
   - **Resultado esperado:** ves `README.md`, `proyecto-base`, `modulos` y `recursos`.
10. Abre **Terminal > New Terminal**.
11. Confirma el estado:

```powershell
git status
```

- **Resultado esperado:** estás en `main` y no hay cambios pendientes.

12. Confirma la conexión:

```powershell
git remote -v
```

- **Resultado esperado:** aparece `origin` con la dirección de GitHub.

13. Consulta el historial:

```powershell
git log --oneline -3
```

- **Resultado esperado:** aparecen hasta tres commits.

14. Abre `proyecto-base/index.html` desde el explorador de Windows.
   - **Resultado esperado:** ves Mercado Nube en el navegador.

## Qué acabas de comprobar

- **Git** registra cambios en tu computadora.
- **GitHub** aloja el repositorio y coordina al equipo.
- El **working directory** es donde editas.
- El **staging area** contiene lo que incluirás en el siguiente commit.
- El **historial** contiene commits anteriores.
- `origin` es el nombre habitual del repositorio remoto.

## Punto de control

No avances hasta que `git status` funcione, `origin` aparezca y el sitio abra.

---

# Bloque 2. Generar, revisar, hacer commit y publicar

## Meta

Agregar productos con Copilot y comprender `add → commit → push`.

## Paso a paso

1. Abre `proyecto-base/index.html`.
2. Localiza `<div class="product-grid">`.
3. Abre el Chat de Copilot.
4. Envía:

> En `proyecto-base/index.html`, genera dentro de `.product-grid` seis tarjetas semánticas para una tienda ficticia llamada Mercado Nube. Incluye productos genéricos de electrónica, hogar, despensa, ropa y juguetes. Cada tarjeta debe tener imagen con URL pública de marcador, texto alternativo útil, nombre, precio ficticio en pesos mexicanos y un enlace con apariencia de botón. No uses JavaScript, marcas reales ni estilos en línea.

5. Revisa la propuesta antes de aplicarla.
   - **Resultado esperado:** seis elementos `article` sin marcas ni datos reales.
6. Aplica las tarjetas dentro de `.product-grid`.
7. Pide a Copilot:

> Genera CSS para `.product-card` y sus elementos usando las variables existentes. Mantén CSS puro, Grid adaptable, foco visible y contraste legible. No cambies las reglas existentes.

8. Agrega la propuesta al final de `proyecto-base/styles.css`.
9. Guarda ambos archivos.
10. Actualiza el navegador.
    - **Resultado esperado:** ves seis tarjetas organizadas en cuadrícula.
11. Revisa qué cambió:

```powershell
git status
git diff
```

- **Resultado esperado:** sólo aparecen `index.html` y `styles.css`.

12. Prepara los archivos:

```powershell
git add proyecto-base/index.html proyecto-base/styles.css
```

13. Comprueba el staging:

```powershell
git status
git diff --staged
```

- **Resultado esperado:** los dos archivos aparecen en **Changes to be committed**.

14. Crea el commit:

```powershell
git commit -m "Agrega productos destacados a la tienda"
```

- **Resultado esperado:** Git muestra un identificador corto y un resumen.

15. Publica:

```powershell
git push
```

- **Resultado esperado:** el commit llega a GitHub o recibes un rechazo por rama protegida.

## Si `main` está protegida

No fuerces el push. Crea una rama desde el commit actual:

```powershell
git switch -c feature/catalogo-inicial
git push -u origin HEAD
```

Tu trabajo queda publicado en la rama feature y podrá entrar mediante Pull Request.

## Punto de control

El sitio muestra productos, el commit existe y `git status` está limpio.

---

# Bloque 3. Trabajar con ramas

## Meta

Agregar categorías en una rama de corta duración.

## Modelo de ramas

```text
feature/categorias → dev → main → producción
```

- `feature/...`: una mejora concreta.
- `dev`: conjunto de mejoras listo para validación.
- `main`: versión aprobada.

## Paso a paso

1. Confirma tu estado:

```powershell
git status
git branch --show-current
```

2. Si todavía estás en `main`, crea tu rama:

```powershell
git switch -c feature/categorias
```

3. Si ya creaste `feature/catalogo-inicial`, puedes continuar ahí o usar el nombre indicado por el instructor.
4. Confirma:

```powershell
git branch --show-current
```

- **Resultado esperado:** aparece `feature/...`.

5. Abre la sección `#categorias` en `index.html`.
6. Pide a Copilot:

> Reemplaza el texto provisional de la sección `#categorias` por una lista semántica de cinco categorías: Electrónica, Hogar, Despensa, Ropa y Juguetes. Cada categoría debe incluir un emoji decorativo oculto para lectores de pantalla, nombre y texto breve. Usa enlaces internos, HTML puro y clases con nombres claros. No uses JavaScript.

7. Pide los estilos:

> Crea estilos adaptables para la lista de categorías usando CSS Grid y las variables ya definidas. Conserva la apariencia de Mercado Nube y agrega estados `hover` y `focus-visible`.

8. Guarda y actualiza el navegador.
   - **Resultado esperado:** aparecen cinco categorías.
9. Revisa:

```powershell
git status
git diff
```

10. Registra:

```powershell
git add proyecto-base/index.html proyecto-base/styles.css
git commit -m "Agrega navegación por categorías"
```

11. Publica la rama:

```powershell
git push -u origin HEAD
```

- **Resultado esperado:** GitHub muestra la nueva rama.

## Punto de control

Estás en una rama `feature/...`, la rama aparece en GitHub y `git status` está limpio.

---

# Bloque 4. Colaborar sin sobrescribir trabajo

## Meta

Crear dos mejoras en paralelo e integrar el trabajo reciente de `dev`.

## Roles

- **Persona A:** banner promocional.
- **Persona B:** mejora del pie de página.
- **Persona C, si existe:** revisa historial y coordina el orden.

## Preparar la rama de la persona A

```powershell
git switch dev
git pull --ff-only
git switch -c feature/banner-promocional
```

Pide a Copilot:

> Agrega debajo de `.site-header` una franja semántica de promoción para Mercado Nube con el texto “Envío sin costo en compras participantes”. Incluye un enlace a `#productos`. Genera HTML y CSS puro, accesible y adaptable. No uses JavaScript ni marcas reales.

Revisa, prueba y publica:

```powershell
git status
git diff
git add proyecto-base/index.html proyecto-base/styles.css
git commit -m "Agrega banner promocional"
git push -u origin HEAD
```

## Preparar la rama de la persona B

```powershell
git switch dev
git pull --ff-only
git switch -c feature/mejora-footer
```

Pide a Copilot:

> Mejora `.site-footer` con dos grupos de enlaces ficticios, un mensaje de ayuda y el aviso de proyecto educativo. Usa HTML semántico y CSS puro. No incluyas teléfonos, correos, redes ni datos reales.

Revisa, prueba y publica:

```powershell
git status
git diff
git add proyecto-base/index.html proyecto-base/styles.css
git commit -m "Mejora información del pie de página"
git push -u origin HEAD
```

## Actualizar la rama de B después de integrar A

Cuando el instructor confirme que el cambio de A llegó a `dev`, la persona B ejecuta:

```powershell
git fetch origin
git log --oneline --all --graph --decorate -10
git switch dev
git pull --ff-only
git switch feature/mejora-footer
git merge dev
git push
```

- **Resultado esperado:** la rama de B contiene el banner de A y su nuevo pie de página.

## Diferencias importantes

- `fetch` consulta cambios sin modificar tus archivos.
- `pull` trae e integra la rama remota asociada.
- `merge dev` integra `dev` en tu rama actual.

## Punto de control

La rama de B contiene las dos mejoras y no hay cambios pendientes.

---

# Bloque 5. Provocar y resolver un conflicto

## Meta

Crear un conflicto real sobre el mismo encabezado y resolverlo de forma controlada.

## Preparación de A

```powershell
git switch dev
git pull --ff-only
git switch -c feature/mensaje-banner-a
```

Pide a Copilot:

> Propón una frase de máximo ocho palabras para el encabezado principal de una tienda ficticia. Debe comunicar soluciones para el hogar, sin mencionar marcas ni promociones.

Reemplaza únicamente el texto dentro de `<h1 id="hero-title">`, guarda y publica:

```powershell
git add proyecto-base/index.html
git commit -m "Actualiza mensaje principal del banner"
git push -u origin HEAD
```

## Preparación de B

La persona B parte de la misma versión de `dev`:

```powershell
git switch dev
git pull --ff-only
git switch -c feature/mensaje-banner-b
```

Pide a Copilot:

> Propón una frase de máximo ocho palabras para el encabezado principal de una tienda ficticia. Debe comunicar variedad de productos, sin mencionar marcas ni promociones.

Reemplaza la misma línea y publica:

```powershell
git add proyecto-base/index.html
git commit -m "Actualiza mensaje principal del banner"
git push -u origin HEAD
```

## Provocar el conflicto

1. El instructor integra primero la rama A a `dev`.
2. La persona B actualiza `dev`:

```powershell
git fetch origin
git switch dev
git pull --ff-only
```

3. La persona B regresa a su rama:

```powershell
git switch feature/mensaje-banner-b
```

4. Integra `dev`:

```powershell
git merge dev
```

- **Resultado esperado:** aparece `CONFLICT (content)`.

## Leer el conflicto

Abre `index.html`. Verás algo parecido a:

```text
<<<<<<< HEAD
versión de tu rama
=======
versión que entra desde dev
>>>>>>> dev
```

## Resolver el conflicto

1. Lee las dos frases.
2. Acuerda con tu pareja una frase final.
3. Conserva sólo el contenido acordado.
4. Elimina `<<<<<<<`, `=======` y `>>>>>>>`.
5. Guarda.
6. Busca `<<<<<<<` en todo el archivo.
   - **Resultado esperado:** cero coincidencias.
7. Actualiza el navegador.
   - **Resultado esperado:** el sitio funciona y muestra una sola frase.
8. Marca la resolución:

```powershell
git add proyecto-base/index.html
git status
```

- **Resultado esperado:** ya no hay rutas sin integrar.

9. Cierra el merge:

```powershell
git commit -m "Resuelve mensaje del banner con cambios de dev"
git push
```

## Punto de control

No quedan marcadores, el sitio funciona, `git status` está limpio y la resolución está en GitHub.

---

# Bloque 6. Abrir y revisar un Pull Request

## Meta

Integrar una rama feature en `dev` mediante revisión.

## Abrir el Pull Request

1. Confirma tu rama:

```powershell
git branch --show-current
git status
git push
```

2. Abre el repositorio en GitHub.
3. Selecciona **Pull requests > New pull request**.
4. Configura:
   - **base:** `dev`;
   - **compare:** tu rama `feature/...`.
5. Revisa **Commits**.
6. Revisa **Files changed**.
   - **Resultado esperado:** sólo aparecen los cambios del ejercicio.
7. Escribe un título orientado al resultado.
8. Pide a Copilot:

> Redacta una descripción breve de Pull Request en español de México con estas secciones: “Qué cambia”, “Por qué”, “Cómo lo validé” y “Riesgos”. El cambio mejora el banner de una tienda ficticia y resolvió un conflicto con `dev`. No inventes pruebas ni aprobaciones; usa casillas para que yo complete lo que sí verifiqué.

9. Ajusta el texto para reflejar sólo lo que hiciste.
10. Selecciona **Create pull request**.
11. Solicita revisión a tu pareja.

## Revisar el PR de otra persona

1. Abre **Files changed**.
2. Comprueba:
   - que el destino sea `dev`;
   - que no haya secretos;
   - que no existan archivos inesperados;
   - que el HTML sea semántico;
   - que el sitio conserve su apariencia.
3. Selecciona una línea y deja un comentario específico.
4. Si todo está correcto, selecciona **Review changes > Approve**.

## Responder una revisión

1. Lee el comentario completo.
2. Explica qué entendiste.
3. Si requiere ajuste, cambia el archivo en tu rama.
4. Prueba el sitio.
5. Publica:

```powershell
git add proyecto-base/index.html proyecto-base/styles.css
git commit -m "Ajusta mejora según revisión"
git push
```

- **Resultado esperado:** el commit aparece en el mismo PR.

6. Responde el comentario.
7. Espera aprobación y validaciones.
8. Completa el merge cuando GitHub lo permita.
9. Actualiza tu copia:

```powershell
git switch dev
git pull --ff-only
```

## Punto de control

El PR apunta a `dev`, contiene descripción, tiene revisión y aparece como **Merged**.

---

# Bloque 7. Seguir el despliegue y diagnosticar

## Meta

Identificar en qué compuerta está un cambio y explicar una falla con evidencia.

## Recorrido

1. Abre el PR preparado de `dev` hacia `main`.
2. Confirma:
   - **base:** `main`;
   - **compare:** `dev`.
3. Abre **Checks**.
4. Identifica el estado:
   - pendiente;
   - correcto;
   - fallido;
   - esperando aprobación.
5. Abre una validación.
6. Si falló, busca la primera línea que explica la causa.
7. Abre `[AJUSTAR: panel del ambiente]`.
8. Identifica la versión desplegada.

## Diagnóstico mínimo

Ejecuta:

```powershell
git status
git branch --show-current
git fetch origin
git log --oneline -5
```

Clasifica el problema:

| Síntoma | Revisión inicial |
|---|---|
| Push rechazado | Confirma rama y si el remoto avanzó |
| Rama protegida | Publica una feature y abre PR |
| Conflicto | Abre `git status` y resuelve marcadores |
| PR bloqueado | Revisa aprobación, conflictos y checks |
| Cambio no aparece | Revisa guardado, commit, push y rama |
| Commit en rama equivocada | Detente y confirma si ya fue publicado |

Consulta [recursos/guia-de-diagnostico.md](./recursos/guia-de-diagnostico.md) para el árbol completo.

## Prompt seguro para errores

> Analiza este mensaje de Git o GitHub: `[PEGA AQUÍ EL MENSAJE SIN CREDENCIALES]`. Explícalo en español simple. Separa: síntoma, causa probable, cómo verificarla y siguiente acción segura. No sugieras force push, borrar archivos ni `reset --hard`.

## Punto de control

Puedes explicar si el cambio está local, publicado, en revisión, integrado o desplegado, y sabes qué compuerta lo detiene.

---

# Bloque 8. Reto final

## Meta

Completar todo el flujo sin instrucciones del instructor.

## Roles

- **Conductor:** usa el teclado.
- **Navegante:** anticipa el siguiente paso.
- **Revisor:** revisa diff y Pull Request.

Cambien de rol durante el ejercicio.

## Elegir una mejora

Seleccionen una:

- distintivos de oferta;
- sección de beneficios;
- guía de compra;
- mejora para pantallas pequeñas.

La mejora debe usar sólo HTML y CSS y completarse en menos de 20 minutos.

## Flujo completo

1. Actualicen `dev`:

```powershell
git switch dev
git pull --ff-only
```

2. Creen una rama:

```powershell
git switch -c feature/nombre-breve
```

3. Pidan a Copilot el HTML y CSS.
4. Revisen la propuesta.
5. Guarden y prueben en el navegador.
6. Revisen:

```powershell
git status
git diff
```

7. Preparen y registren:

```powershell
git add proyecto-base/index.html proyecto-base/styles.css
git diff --staged
git commit -m "Agrega [resultado concreto]"
```

8. Publiquen:

```powershell
git push -u origin HEAD
```

9. Consulten cambios recientes:

```powershell
git fetch origin
```

10. Actualicen la rama:

```powershell
git merge origin/dev
```

11. Si aparece un conflicto:
    - lean ambas versiones;
    - decidan el resultado;
    - eliminen marcadores;
    - prueben;
    - ejecuten `git add`;
    - creen el commit.
12. Publiquen:

```powershell
git push
```

13. Abran un PR hacia `dev`.
14. Incluyan:
    - qué cambia;
    - por qué;
    - cómo lo validaron;
    - riesgos conocidos.
15. Soliciten revisión a otro equipo.
16. Revisen el PR de otro equipo.
17. Respondan comentarios.
18. Comprueben checks.
19. Completen el merge cuando las reglas lo permitan.
20. Expliquen el recorrido de su cambio en 60 segundos.

## Criterios de éxito

- La rama tiene un nombre claro.
- El cambio cumple un solo propósito.
- No hay secretos ni archivos inesperados.
- El sitio funciona.
- El PR apunta a `dev`.
- Otra persona revisó.
- El equipo puede señalar dónde está el cambio.

---

# Cierre y práctica posterior

## Lo que debes poder explicar

- Guardar un archivo no crea un commit.
- `git add` selecciona.
- `git commit` registra localmente.
- `git push` publica.
- Una rama aísla una mejora.
- `fetch` consulta; `pull` consulta e integra.
- Un conflicto requiere una decisión.
- Un Pull Request conserva revisión y contexto.
- Un merge a `main` no garantiza por sí solo que el despliegue terminó.
- Copilot propone; tú revisas y decides.

## Ruta de práctica

Durante las siguientes cuatro semanas:

1. Semana 1: crea una rama y un commit pequeño.
2. Semana 2: abre un PR con descripción completa.
3. Semana 3: revisa un PR de otra persona.
4. Semana 4: practica diagnosticar un push rechazado o un conflicto.

## Referencias

- [Módulos detallados](./modulos/)
- [Glosario](./recursos/glosario.md)
- [Comandos Git](./recursos/comandos-git.md)
- [Guía de diagnóstico](./recursos/guia-de-diagnostico.md)
- [Prompts para Copilot](./recursos/prompts-para-copilot.md)

## Checklist final

- [ ] Cloné el repositorio.
- [ ] Identifiqué mi rama.
- [ ] Generé código con Copilot y lo revisé.
- [ ] Usé `git add`, `commit` y `push`.
- [ ] Creé y publiqué una rama feature.
- [ ] Actualicé mi rama con cambios de `dev`.
- [ ] Resolví un conflicto real.
- [ ] Abrí un Pull Request hacia `dev`.
- [ ] Revisé el cambio de otra persona.
- [ ] Interpreté una validación.
- [ ] Completé el reto final.
- [ ] Puedo explicar el recorrido hasta producción.
