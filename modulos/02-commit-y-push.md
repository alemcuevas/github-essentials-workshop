# 02. Construir, versionar y publicar: commit y push

## 1. Objetivo del bloque

Agregar productos con Copilot y publicar el primer cambio mediante staging, commit y push.

## 2. Qué vas a lograr aquí

- Crearás tarjetas de producto sin escribir HTML a mano.
- Revisarás y agruparás un cambio en un commit descriptivo.
- Publicarás el commit y lo localizarás en GitHub.

## 3. Concepto

Piensa en un envío. Guardar un archivo deja el contenido sobre tu mesa. `git add` coloca los archivos elegidos en una caja llamada **staging**. `git commit` cierra la caja, registra su contenido y le pone una etiqueta. `git push` transporta los commits desde tu computadora hasta GitHub.

Un **commit** no es una copia completa ni equivale a guardar. Es un punto identificable del historial que contiene un conjunto coherente de cambios y se conecta con el commit anterior. Su mensaje debe explicar la intención: “Agrega productos destacados” ayuda más que “cambios”.

`git pull` hace el recorrido contrario para la rama actual: trae e integra lo publicado por otras personas. Hoy usarás `push`; más adelante practicarás `pull`.

Copilot puede generar HTML, explicar diferencias y sugerir un mensaje. Tu responsabilidad es revisar el resultado, comprobar que no incluye información sensible, elegir qué archivos entran al commit y confirmar que estás en la rama correcta.

## 4. Manos a la obra

1. Abre `proyecto-base/index.html` en VS Code.
   - **Qué debes ver:** un contenedor `<div class="product-grid">` vacío.
2. La persona A crea una rama que incluya su nombre:

```powershell
git switch -c feature/nombre-apellido-catalogo
```

   - **Qué debes ver:** una rama como `feature/ana-lopez-catalogo`. Sustituye el ejemplo por tu nombre real, en minúsculas y sin acentos.
3. La persona A abre el Chat de Copilot mientras la persona B revisa cada propuesta.
   - **Qué debes ver:** el campo para escribir una solicitud.
4. Usa el prompt de este módulo y aplica la propuesta dentro de `product-grid`.
   - **Qué debes ver:** seis elementos `<article class="product-card">` con imagen, nombre, precio y enlace o botón.
5. Revisa que los productos y las imágenes sean genéricos y no incluyan marcas reales.
   - **Qué debes ver:** productos como audífonos, lámpara, mochila o juego de mesa con textos ficticios.
6. Pide a Copilot los estilos de las clases nuevas y aplícalos al final de `proyecto-base/styles.css`.
   - **Qué debes ver:** reglas para tarjeta, imagen, precio y acción.
7. Guarda ambos archivos.
   - **Qué debes ver:** desaparece el punto de cambios sin guardar en las pestañas.
8. Actualiza el navegador.
   - **Qué debes ver:** una cuadrícula de seis tarjetas legibles.
9. Ejecuta:

```powershell
git status
```

   - **Qué debes ver:** `index.html` y `styles.css` aparecen como modificados y todavía no preparados.
10. Ejecuta:

```powershell
git diff
```

   - **Qué debes ver:** líneas agregadas con `+`; revisa que no haya datos o archivos inesperados.
11. Prepara sólo los dos archivos:

```powershell
git add proyecto-base/index.html proyecto-base/styles.css
```

   - **Qué debes ver:** el comando termina sin error.
12. Ejecuta:

```powershell
git status
```

   - **Qué debes ver:** ambos archivos aparecen bajo **Changes to be committed**.
13. Crea el commit:

```powershell
git commit -m "Agrega productos destacados a la tienda"
```

   - **Qué debes ver:** un identificador corto y un resumen de líneas modificadas.
14. Publica por primera vez la rama personal:

```powershell
git push -u origin HEAD
```

   - **Qué debes ver:** GitHub recibe una rama como `feature/ana-lopez-catalogo`.
15. Abre la rama en el repositorio del equipo y selecciona su historial.
   - **Qué debes ver:** el mensaje `Agrega productos destacados a la tienda`.

## 5. Prompt sugerido para Copilot

> **Prompt para Copilot**
>
> En `proyecto-base/index.html`, genera dentro de `.product-grid` seis tarjetas semánticas para una tienda ficticia llamada Contoso Retail. Incluye productos genéricos de electrónica, hogar, despensa, ropa y juguetes. Usa las imágenes locales de `proyecto-base/assets`, repitiendo una cuando sea necesario. Cada tarjeta debe tener texto alternativo útil, nombre, precio ficticio en pesos mexicanos y un enlace con apariencia de botón. No uses JavaScript, marcas reales, URLs externas ni estilos en línea.

> **Prompt para Copilot**
>
> Genera CSS para `.product-card` y sus elementos usando las variables existentes. Mantén CSS puro, Grid adaptable, foco visible y contraste legible. No cambies las reglas existentes.

## 6. Punto de control

El sitio muestra seis tarjetas, `git status` está limpio y el commit aparece en GitHub dentro de una rama `feature/nombre-apellido-catalogo`.

## 7. Si algo falla

- **`nothing to commit`:** confirma que guardaste los archivos y ejecuta `git status`.
- **La rama no contiene tu nombre:** no crees otra sin revisar; pide al mentor ayudarte a renombrarla antes de continuar.
- **Las tarjetas no tienen estilo:** verifica que `index.html` enlaza `styles.css` y que las clases generadas coinciden exactamente.

## 8. Para profundizar

Compara `git diff` con `git diff --staged`: el primero muestra cambios no preparados y el segundo muestra el contenido del próximo commit.
