# 04. Colaborar en equipo sobre un mismo proyecto

## 1. Objetivo del bloque

Coordinar dos cambios en paralelo y actualizar una rama antes de integrarla.

## 2. Qué vas a lograr aquí

- Trabajarás en pareja o equipo de 3 sin compartir una misma rama.
- Distinguirás `fetch`, `pull` y `merge`.
- Integrarás cambios recientes de `dev` en tu rama.

## 3. Concepto

Dos personas pueden trabajar en el mismo repositorio si cada una usa una rama. Es como preparar secciones distintas de una presentación y reunirlas cuando están listas.

`git fetch` pregunta a GitHub qué cambió y actualiza las referencias remotas, pero no modifica tus archivos. `git pull` trae los cambios e integra la rama remota asociada en tu rama actual. `git merge otra-rama` combina explícitamente otra línea de trabajo con la rama donde estás.

Antes de integrar tu mejora, actualiza tu conocimiento del remoto y trae `dev` a tu rama. Así descubres diferencias temprano. Sincronizar seguido, usar ramas cortas y hacer commits pequeños reduce conflictos, aunque no los elimina.

No confundas “ver el trabajo de otra persona” con “editar su rama”. Cada integrante conserva su rama y el equipo coordina qué se integra primero.

## 4. Manos a la obra

1. Formen parejas o equipos de 3 y asignen roles A, B y, si aplica, C.
   - **Qué debes ver:** cada persona conoce su cambio y su turno al teclado.
2. La persona A cambia a `dev`:

```powershell
git switch dev
```

   - **Qué debes ver:** la terminal confirma `dev`.
3. La persona A actualiza `dev`:

```powershell
git pull --ff-only
```

   - **Qué debes ver:** `Already up to date` o archivos actualizados sin crear un merge.
4. La persona A crea su rama:

```powershell
git switch -c feature/banner-promocional
```

   - **Qué debes ver:** una nueva rama.
5. La persona B repite los pasos 2 y 3 en su equipo.
   - **Qué debes ver:** su rama `dev` local está actualizada.
6. La persona B crea su rama:

```powershell
git switch -c feature/mejora-footer
```

   - **Qué debes ver:** una rama distinta a la de A.
7. La persona A usa Copilot para agregar una franja promocional debajo del encabezado.
   - **Qué debes ver:** un bloque HTML y sus estilos sin JavaScript.
8. La persona B usa Copilot para mejorar el pie de página con navegación y texto de ayuda.
   - **Qué debes ver:** un pie semántico, legible y sin datos reales.
9. Cada persona revisa, guarda y crea un commit sólo con su mejora.
   - **Qué debes ver:** `git status` limpio después del commit.
10. Cada persona publica su rama:

```powershell
git push -u origin HEAD
```

   - **Qué debes ver:** ambas ramas en GitHub.
11. El instructor integra la rama de A a `dev` mediante el flujo indicado.
   - **Qué debes ver:** el commit de A aparece en `dev` en GitHub.
12. La persona B consulta cambios sin mezclarlos:

```powershell
git fetch origin
```

   - **Qué debes ver:** una actualización de `origin/dev`, si había cambios nuevos.
13. La persona B observa el historial:

```powershell
git log --oneline --all --graph --decorate -10
```

   - **Qué debes ver:** su rama y `origin/dev` en líneas identificables.
14. La persona B actualiza su `dev` local:

```powershell
git switch dev
git pull --ff-only
```

   - **Qué debes ver:** el cambio de A aparece en los archivos de `dev`.
15. La persona B regresa a su rama:

```powershell
git switch feature/mejora-footer
```

   - **Qué debes ver:** su mejora vuelve a ser la rama actual.
16. La persona B integra `dev`:

```powershell
git merge dev
```

   - **Qué debes ver:** una integración automática sin conflicto porque tocaron secciones distintas.
17. La persona B publica la actualización:

```powershell
git push
```

   - **Qué debes ver:** GitHub recibe la rama actualizada.

## 5. Prompt sugerido para Copilot

> **Prompt para Copilot — persona A**
>
> Agrega debajo de `.site-header` una franja semántica de promoción para Mercado Nube con el texto “Envío sin costo en compras participantes”. Incluye un enlace a `#productos`. Genera HTML y CSS puro, accesible y adaptable. No uses JavaScript ni marcas reales.

> **Prompt para Copilot — persona B**
>
> Mejora `.site-footer` con dos grupos de enlaces ficticios, un mensaje de ayuda y el aviso de proyecto educativo. Usa HTML semántico y CSS puro. No incluyas teléfonos, correos, redes ni datos reales.

## 6. Punto de control

La rama de B contiene su mejora y el cambio de A, `git status` está limpio y el historial muestra que ambas líneas se reunieron sin modificar directamente `main`.

## 7. Si algo falla

- **`pull --ff-only` es rechazado:** tu rama local y la remota se separaron. Detente y pide al mentor revisar el historial; no uses force push.
- **No aparece la rama de otra persona:** ejecuta `git fetch origin` y revisa el nombre exacto en GitHub.
- **Editaste en `dev`:** no hagas commit todavía; guarda el archivo, crea una rama con `git switch -c feature/nombre` y luego registra el cambio.

## 8. Para profundizar

Compara `origin/dev` con `dev`: la primera es tu referencia local del estado remoto; la segunda es tu rama local.
