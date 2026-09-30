# 03. Ramas de trabajo: feature, dev y main

## 1. Objetivo del bloque

Crear y publicar una rama de corta duración para desarrollar la sección de categorías sin trabajar directamente en `main`.

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

Una rama debe tener un propósito claro y una vida corta. `feature/categorias` comunica mejor que `rama-ale-2`.

## 4. Manos a la obra

1. Ejecuta:

```powershell
git status
```

   - **Qué debes ver:** la rama actual y si tu directorio está limpio.
2. Si el commit del bloque anterior quedó sólo en `main` local, crea la rama desde ese punto:

```powershell
git switch -c feature/catalogo-inicial
```

   - **Qué debes ver:** `Switched to a new branch`.
3. Si el commit anterior ya llegó a GitHub, actualiza primero las referencias:

```powershell
git fetch origin
```

   - **Qué debes ver:** el comando termina sin error; no modifica tus archivos.
4. Crea o cambia a la rama de trabajo cuando todavía no exista:

```powershell
git switch -c feature/categorias
```

   - **Qué debes ver:** tu terminal confirma la nueva rama. Usa `feature/catalogo-inicial` si ya la creaste en el paso 2.
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
12. Publica y conecta la rama:

```powershell
git push -u origin HEAD
```

   - **Qué debes ver:** GitHub recibe la rama y Git configura su seguimiento.
13. Abre la lista de ramas en GitHub.
   - **Qué debes ver:** tu rama `feature/...` además de `dev` y `main`.

## 5. Prompt sugerido para Copilot

> **Prompt para Copilot**
>
> Reemplaza el texto provisional de la sección `#categorias` por una lista semántica de cinco categorías: Electrónica, Hogar, Despensa, Ropa y Juguetes. Cada categoría debe incluir un emoji decorativo oculto para lectores de pantalla, nombre y texto breve. Usa enlaces internos, HTML puro y clases con nombres claros. No uses JavaScript.

> **Prompt para Copilot**
>
> Crea estilos adaptables para la lista de categorías usando CSS Grid y las variables ya definidas. Conserva la apariencia de Mercado Nube y agrega estados `hover` y `focus-visible`.

## 6. Punto de control

`git branch --show-current` muestra una rama `feature/...`, `git status` está limpio, la sección de categorías funciona y la rama aparece en GitHub.

## 7. Si algo falla

- **La rama ya existe:** ejecuta `git switch nombre-de-la-rama` en vez de `git switch -c`.
- **Publicaste una rama con otro nombre:** no la fuerces ni la borres durante el ejercicio; informa al instructor y usa ese nombre de forma consistente.
- **El push pide upstream:** ejecuta `git push -u origin HEAD`.

## 8. Para profundizar

Ejecuta `git branch -vv` para ver qué rama remota sigue cada rama local y pide a Copilot que explique la salida.
