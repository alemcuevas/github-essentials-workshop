# 03. Ramas de trabajo: feature, dev y main

## 1. Objetivo del bloque

Comprender la rama personal creada en el bloque anterior, agregar categorías e integrarla a `dev`.

## 2. Qué vas a lograr aquí

- Entenderás el recorrido `feature → dev → main`.
- Crearás, cambiarás y publicarás una rama.
- Agregarás categorías con Copilot sin afectar la versión aprobada.

## 3. Concepto

Una **rama** es como una copia de trabajo lógica donde puedes avanzar sin alterar la versión que usa el resto. No duplica manualmente todo el proyecto; Git conserva una línea del historial con un nombre.

Usaremos tres escalones:

- `feature/...` contiene una mejora específica y vive poco tiempo;
- `dev` reúne mejoras para probarlas juntas;
- `main` representa lo aprobado para llegar a producción.

El recorrido es `feature → dev → main`. Nunca trabajamos directo sobre `main` porque saltaríamos el aislamiento, la revisión y las validaciones. Una **rama protegida** es una regla de GitHub que bloquea acciones como el push directo y obliga a usar Pull Requests. Ese rechazo es una protección, no una falla del sistema.

Una rama debe tener un propósito claro, una vida corta y una persona responsable. Usaremos `feature/nombre-apellido-descripcion`, por ejemplo `feature/ana-lopez-catalogo`.

## 4. Manos a la obra

1. Ejecuta:

```powershell
git status
```

   - **Qué debes ver:** la rama actual y si tu directorio está limpio.
2. Confirma que la rama contiene tu nombre y el propósito `catalogo`:

```powershell
git branch --show-current
```

   - **Qué debes ver:** un nombre como `feature/ana-lopez-catalogo`.
3. Cambia temporalmente a `main`:

```powershell
git switch main
```

   - **Qué debes ver:** el catálogo todavía no está en `main`; sólo existe en la rama personal.
4. Regresa a tu rama usando su nombre real:

```powershell
git switch feature/nombre-apellido-catalogo
```

   - **Qué debes ver:** vuelven los productos del bloque 2.
5. Confirma la rama:

```powershell
git branch --show-current
```

   - **Qué debes ver:** el nombre de tu rama `feature/...`.
6. Abre `proyecto-base/index.html`.
   - **Qué debes ver:** la sección `#categorias` todavía contiene un texto provisional.
7. Usa el prompt de este módulo y aplica la propuesta de Copilot dentro de `#categorias`.
   - **Qué debes ver:** cinco enlaces o tarjetas de categoría.
8. Pide a Copilot estilos para las clases nuevas y aplícalos en `styles.css`.
   - **Qué debes ver:** reglas compatibles con las variables existentes.
9. Guarda y actualiza el navegador.
   - **Qué debes ver:** categorías de electrónica, hogar, despensa, ropa y juguetes.
10. Revisa:

```powershell
git diff
```

   - **Qué debes ver:** sólo los cambios de categorías y sus estilos.
11. Prepara y registra los archivos:

```powershell
git add proyecto-base/index.html proyecto-base/styles.css
git commit -m "Agrega navegación por categorías"
```

   - **Qué debes ver:** un nuevo commit en tu rama.
12. Publica el nuevo commit:

```powershell
git push
```

   - **Qué debes ver:** GitHub actualiza tu rama personal.
13. Abre un Pull Request desde tu rama hacia `dev`; el instructor sólo mostrará los clics y explicará la revisión con detalle en el bloque 6.
   - **Qué debes ver:** la base es `dev` y la comparación es tu rama.
14. La persona B revisa que el PR sólo contenga productos y categorías, y selecciona **Merge pull request**.
   - **Qué debes ver:** el cambio queda integrado a `dev`.
15. Ambas personas actualizan `dev`:

```powershell
git switch dev
git pull --ff-only
```

   - **Qué debes ver:** productos y categorías aparecen en `dev` en las dos computadoras.

## 5. Prompt sugerido para Copilot

> **Prompt para Copilot**
>
> Reemplaza el texto provisional de la sección `#categorias` por una lista semántica de cinco categorías: Electrónica, Hogar, Despensa, Ropa y Juguetes. Cada categoría debe incluir un emoji decorativo oculto para lectores de pantalla, nombre y texto breve. Usa enlaces internos, HTML puro y clases con nombres claros. No uses JavaScript.

> **Prompt para Copilot**
>
> Crea estilos adaptables para la lista de categorías usando CSS Grid y las variables ya definidas. Conserva la apariencia de Contoso Retail y agrega estados `hover` y `focus-visible`.

## 6. Punto de control

El primer cambio está integrado en `dev`, ambas personas lo ven y la rama de origen identifica a su autor.

## 7. Si algo falla

- **Escribiste literalmente `nombre-apellido`:** detente y pide apoyo para renombrar la rama antes de abrir el PR.
- **El PR apunta a `main`:** edítalo y cambia la base a `dev` antes de integrarlo.
- **El push pide upstream:** ejecuta `git push -u origin HEAD`.

## 8. Para profundizar

Ejecuta `git branch -vv` para ver qué rama remota sigue cada rama local y pide a Copilot que explique la salida.
