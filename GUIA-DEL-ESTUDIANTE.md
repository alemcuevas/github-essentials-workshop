# Guía del estudiante

Esta guía contiene el paso a paso completo para terminar el taller de GitHub. Puedes seguirla durante la sesión o usarla para retomar el ejercicio por tu cuenta.

Construirás **Contoso Retail**, una tienda ficticia hecha únicamente con HTML y CSS. GitHub Copilot te ayudará a generar código; tú controlarás el flujo de Git y GitHub.

Trabajarás siempre con la misma pareja. Este repositorio es una plantilla y un ejemplo: una persona creará un repositorio nuevo para el equipo, invitará a su compañero y ambos harán ahí todos los ejercicios.

Tus ramas seguirán este formato:

```text
feature/nombre-apellido-descripcion
```

Por ejemplo, Ana López usaría `feature/ana-lopez-catalogo`. Escribe en minúsculas, elimina acentos y reemplaza espacios por guiones.

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
GitHub Pages del equipo
```

## Antes de comenzar

Completa [SETUP-PREVIO.md](./SETUP-PREVIO.md). Debes tener:

- una cuenta activa de GitHub;
- acceso a GitHub Copilot;
- VS Code;
- las extensiones **GitHub Copilot** y **GitHub Pull Requests**;
- Git disponible;
- acceso a `https://github.com/alemcuevas/github-essentials-workshop`;
- una pareja asignada y un acuerdo sobre quién creará el repositorio.

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

Crear el repositorio de la pareja desde la plantilla, compartirlo y clonarlo en ambas computadoras.

## Paso a paso

1. Confirmen quién será la persona A y quién será la persona B.
   - **Resultado esperado:** la persona A creará el repositorio.
2. La persona A abre `https://github.com/alemcuevas/github-essentials-workshop`.
   - **Resultado esperado:** aparece el botón **Use this template**.
3. La persona A selecciona **Use this template > Create a new repository**.
4. Escribe un nombre como `contoso-retail-ana-luis`.
5. Selecciona visibilidad pública.
6. Crea el repositorio.
   - **Resultado esperado:** aparece un repositorio nuevo en la cuenta de la persona A.
7. La persona A abre **Settings > Collaborators > Add people**.
8. Invita a la persona B.
9. La persona B acepta la invitación.
   - **Resultado esperado:** ambas personas tienen acceso de escritura.
10. En el repositorio del equipo, seleccionen **Code > Local > HTTPS**.
11. Copien la dirección.
12. En ambas computadoras, abran VS Code y presionen `Ctrl+Shift+P`.
13. Ejecuten **Git: Clone**.
14. Peguen la dirección del repositorio del equipo.
15. Elijan una carpeta local.
16. Seleccionen **Open** cuando VS Code lo solicite.
   - **Resultado esperado:** ves `README.md`, `proyecto-base`, `modulos` y `recursos`.
17. Ambas personas abren **Terminal > New Terminal**.
18. Confirmen el estado:

```powershell
git status
```

- **Resultado esperado:** estás en `main` y no hay cambios pendientes.

19. Confirmen la conexión:

```powershell
git remote -v
```

- **Resultado esperado:** `origin` apunta al repositorio del equipo, no a `github-essentials-workshop`.

20. La persona A crea y publica `dev`:

```powershell
git switch -c dev
git push -u origin dev
git switch main
```

- **Resultado esperado:** `main` y `dev` aparecen en GitHub.

21. La persona B actualiza sus referencias:

```powershell
git fetch origin
git switch dev
git switch main
```

- **Resultado esperado:** también puede cambiar entre `main` y `dev`.

22. Consulten el historial:

```powershell
git log --oneline -3
```

- **Resultado esperado:** aparecen hasta tres commits.

23. Abran `proyecto-base/index.html` desde el explorador de Windows.
   - **Resultado esperado:** ves Contoso Retail en el navegador.

## Qué acabas de comprobar

- **Git** registra cambios en tu computadora.
- **GitHub** aloja el repositorio y coordina al equipo.
- El **working directory** es donde editas.
- El **staging area** contiene lo que incluirás en el siguiente commit.
- El **historial** contiene commits anteriores.
- `origin` es el nombre habitual del repositorio remoto.

## Punto de control

No avancen hasta que ambos puedan acceder al repositorio, `origin` apunte al equipo, `dev` exista y el sitio abra.

---

# Bloque 2. Generar, revisar, hacer commit y publicar

## Meta

Agregar productos con Copilot y comprender `add → commit → push`.

## Paso a paso

1. Abre `proyecto-base/index.html`.
2. Localiza `<div class="product-grid">`.
3. La persona A crea una rama con su nombre:

```powershell
git switch -c feature/nombre-apellido-catalogo
```

- **Resultado esperado:** una rama como `feature/ana-lopez-catalogo`. Sustituye el ejemplo por tu nombre real.

4. La persona A abre el Chat de Copilot y la persona B revisa las propuestas.
5. Envía:

> En `proyecto-base/index.html`, genera dentro de `.product-grid` seis tarjetas semánticas para una tienda ficticia llamada Contoso Retail. Incluye productos genéricos de electrónica, hogar, despensa, ropa y juguetes. Usa las imágenes locales de `proyecto-base/assets`, repitiendo una cuando sea necesario. Cada tarjeta debe tener texto alternativo útil, nombre, precio ficticio en pesos mexicanos y un enlace con apariencia de botón. No uses JavaScript, marcas reales, URLs externas ni estilos en línea.

6. Revisa la propuesta antes de aplicarla.
   - **Resultado esperado:** seis elementos `article` sin marcas ni datos reales.
7. Aplica las tarjetas dentro de `.product-grid`.
8. Pide a Copilot:

> Genera CSS para `.product-card` y sus elementos usando las variables existentes. Mantén CSS puro, Grid adaptable, foco visible y contraste legible. No cambies las reglas existentes.

9. Agrega la propuesta al final de `proyecto-base/styles.css`.
10. Guarda ambos archivos.
11. Actualiza el navegador.
    - **Resultado esperado:** ves seis tarjetas organizadas en cuadrícula.
12. Revisa qué cambió:

```powershell
git status
git diff
```

- **Resultado esperado:** sólo aparecen `index.html` y `styles.css`.

13. Prepara los archivos:

```powershell
git add proyecto-base/index.html proyecto-base/styles.css
```

14. Comprueba el staging:

```powershell
git status
git diff --staged
```

- **Resultado esperado:** los dos archivos aparecen en **Changes to be committed**.

15. Crea el commit:

```powershell
git commit -m "Agrega productos destacados a la tienda"
```

- **Resultado esperado:** Git muestra un identificador corto y un resumen.

16. Publica la rama:

```powershell
git push -u origin HEAD
```

- **Resultado esperado:** el commit aparece en GitHub dentro de una rama con el nombre de la persona A.

## Punto de control

El sitio muestra productos, el commit está publicado en `feature/nombre-apellido-catalogo` y `git status` está limpio.

---

# Bloque 3. Trabajar con ramas

## Meta

Comprender la rama personal, agregar categorías e integrar el catálogo a `dev`.

## Modelo de ramas

```text
feature/nombre-apellido-catalogo → dev → main → producción
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

2. Confirma que la rama contiene el nombre de la persona A:

```powershell
git branch --show-current
```

- **Resultado esperado:** algo como `feature/ana-lopez-catalogo`.

3. Cambia a `main` para comprobar que el trabajo está aislado:

```powershell
git switch main
```

- **Resultado esperado:** los productos todavía no están en `main`.

4. Regresa a la rama personal usando el nombre real creado en el bloque 2:

```powershell
git switch feature/nombre-apellido-catalogo
```

- **Resultado esperado:** vuelven los productos.

5. Abre la sección `#categorias` en `index.html`.
6. Pide a Copilot:

> Reemplaza el texto provisional de la sección `#categorias` por una lista semántica de cinco categorías: Electrónica, Hogar, Despensa, Ropa y Juguetes. Cada categoría debe incluir un emoji decorativo oculto para lectores de pantalla, nombre y texto breve. Usa enlaces internos, HTML puro y clases con nombres claros. No uses JavaScript.

7. Pide los estilos:

> Crea estilos adaptables para la lista de categorías usando CSS Grid y las variables ya definidas. Conserva la apariencia de Contoso Retail y agrega estados `hover` y `focus-visible`.

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

11. Publica el nuevo commit:

```powershell
git push
```

- **Resultado esperado:** GitHub actualiza la rama.

12. Abre un Pull Request desde la rama personal hacia `dev`.
13. La persona B revisa que sólo contenga productos y categorías.
14. La persona B integra el PR.
15. Ambas personas actualizan `dev`:

```powershell
git switch dev
git pull --ff-only
```

- **Resultado esperado:** ambos ven el catálogo completo en `dev`.

## Punto de control

El catálogo está integrado en `dev`, ambas copias están actualizadas y la rama identifica a su autor.

---

# Bloque 4. Colaborar sin sobrescribir trabajo

## Meta

Crear dos mejoras en paralelo e integrar el trabajo reciente de `dev`.

## Roles

- **Persona A:** banner promocional.
- **Persona B:** mejora del pie de página.
## Preparar la rama de la persona A

```powershell
git switch dev
git pull --ff-only
git switch -c feature/nombre-a-apellido-banner
```

Sustituye el marcador por el nombre real de A, por ejemplo `feature/ana-lopez-banner`.

Pide a Copilot:

> Agrega debajo de `.site-header` una franja semántica de promoción para Contoso Retail con el texto “Envío sin costo en compras participantes”. Incluye un enlace a `#productos`. Genera HTML y CSS puro, accesible y adaptable. No uses JavaScript ni marcas reales.

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
git switch -c feature/nombre-b-apellido-footer
```

Sustituye el marcador por el nombre real de B, por ejemplo `feature/luis-perez-footer`.

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

La persona A abre un PR hacia `dev`; la persona B lo revisa e integra. Después, la persona B ejecuta:

```powershell
git fetch origin
git log --oneline --all --graph --decorate -10
git switch dev
git pull --ff-only
git switch feature/nombre-b-apellido-footer
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
git switch -c feature/nombre-a-apellido-mensaje-banner
```

Usa el nombre real de A, por ejemplo `feature/ana-lopez-mensaje-banner`.

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
git switch -c feature/nombre-b-apellido-mensaje-banner
```

Usa el nombre real de B, por ejemplo `feature/luis-perez-mensaje-banner`.

Pide a Copilot:

> Propón una frase de máximo ocho palabras para el encabezado principal de una tienda ficticia. Debe comunicar variedad de productos, sin mencionar marcas ni promociones.

Reemplaza la misma línea y publica:

```powershell
git add proyecto-base/index.html
git commit -m "Actualiza mensaje principal del banner"
git push -u origin HEAD
```

## Provocar el conflicto

1. La persona A abre un PR y la persona B integra primero la rama A a `dev`.
2. La persona B actualiza `dev`:

```powershell
git fetch origin
git switch dev
git pull --ff-only
```

3. La persona B regresa a su rama:

```powershell
git switch feature/nombre-b-apellido-mensaje-banner
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

1. La persona propietaria abre **Settings > Pages**.
2. En **Build and deployment > Source**, selecciona **GitHub Actions**.
   - **Resultado esperado:** Pages queda habilitado.
3. La persona A abre un PR desde `dev` hacia `main` en el repositorio del equipo.
4. Confirma:
   - **base:** `main`;
   - **compare:** `dev`.
5. La persona B abre **Checks**.
6. Identifica el estado:
   - pendiente;
   - correcto;
   - fallido;
   - esperando aprobación.
7. Abre **Validar repositorio**.
8. Si falló, busca la primera línea que explica la causa.
9. Cuando esté en verde, la persona B aprueba e integra el PR.
10. Abre **Actions > Publicar Contoso Retail en GitHub Pages**.
11. Espera a que termine en verde.
12. Abre la URL mostrada por el despliegue.
    - **Resultado esperado:** Contoso Retail está publicado desde el repositorio del equipo.

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
git switch -c feature/tu-nombre-apellido-descripcion
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
15. Soliciten revisión a su compañero.
16. Revisen el PR de su compañero.
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
