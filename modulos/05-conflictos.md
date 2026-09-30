# 05. Conflictos: por qué ocurren y cómo resolverlos

## 1. Objetivo del bloque

Provocar un conflicto controlado, leerlo y resolverlo con una decisión consciente.

## 2. Qué vas a lograr aquí

- Crearás dos cambios incompatibles sobre la misma línea.
- Interpretarás los marcadores de conflicto.
- Resolverás, probarás y publicarás el resultado final.

## 3. Concepto

Git combina automáticamente cambios que ocurren en partes distintas. Aparece un **conflicto** cuando dos ramas cambian de manera incompatible la misma zona y Git no puede saber cuál intención es correcta.

Un conflicto no significa que Git se rompió ni que una persona trabajó mal. Significa que hace falta una decisión humana. En el archivo verás:

```text
<<<<<<< HEAD
tu versión actual
=======
la versión que está entrando
>>>>>>> dev
```

`HEAD` señala la rama donde estás. La sección después de `=======` proviene de la rama que intentas integrar. Resolver no consiste en borrar símbolos al azar: debes decidir el contenido final, retirar todos los marcadores, verificar el sitio, preparar el archivo con `git add` y crear el commit que cierra la integración.

Copilot puede explicar las versiones o proponer una combinación. Tú y tu equipo determinan cuál cumple el objetivo. Para evitar conflictos innecesarios: hagan commits pequeños, mantengan ramas cortas, repartan zonas del archivo y sincronicen seguido.

## 4. Manos a la obra

1. La persona A cambia a `dev` y la actualiza:

```powershell
git switch dev
git pull --ff-only
```

   - **Qué debes ver:** `dev` está actualizada y limpia.
2. La persona A crea:

```powershell
git switch -c feature/nombre-a-apellido-mensaje-banner
```

   - **Qué debes ver:** una rama como `feature/ana-lopez-mensaje-banner`.
3. La persona B parte también de `dev` actualizada en su copia y crea:

```powershell
git switch -c feature/nombre-b-apellido-mensaje-banner
```

   - **Qué debes ver:** una rama como `feature/luis-perez-mensaje-banner`.
4. Ambas personas localizan el mismo `<h1 id="hero-title">` en `proyecto-base/index.html`.
   - **Qué debes ver:** la frase actual del banner.
5. La persona A pide a Copilot una frase breve orientada al hogar y reemplaza únicamente el contenido del `h1`.
   - **Qué debes ver:** una sola línea modificada.
6. La persona B pide a Copilot una frase distinta orientada a variedad y reemplaza la misma línea.
   - **Qué debes ver:** una sola línea modificada, diferente a la de A.
7. Cada persona guarda, prepara y crea su commit:

```powershell
git add proyecto-base/index.html
git commit -m "Actualiza mensaje principal del banner"
git push -u origin HEAD
```

   - **Qué debes ver:** las dos ramas publicadas con frases diferentes.
8. La persona A abre un PR; la persona B lo revisa e integra primero la rama de A a `dev`.
   - **Qué debes ver:** la frase de A aparece en `dev`.
9. La persona B consulta y actualiza `dev`:

```powershell
git fetch origin
git switch dev
git pull --ff-only
```

   - **Qué debes ver:** `dev` contiene la frase de A.
10. La persona B regresa a su rama:

```powershell
git switch feature/nombre-b-apellido-mensaje-banner
```

   - **Qué debes ver:** el `h1` vuelve a mostrar la frase de B. Usa el nombre real de su rama.
11. La persona B intenta integrar `dev`:

```powershell
git merge dev
```

   - **Qué debes ver:** `CONFLICT (content)` y el nombre de `index.html`.
12. Ejecuta:

```powershell
git status
```

   - **Qué debes ver:** `both modified` o `unmerged paths`.
13. Abre `index.html` y localiza `<<<<<<< HEAD`, `=======` y `>>>>>>> dev`.
   - **Qué debes ver:** las frases de A y B separadas por marcadores.
14. Lee ambas propuestas con tu pareja y acuerden una sola frase final.
   - **Qué debes ver:** una decisión expresada en voz alta antes de editar.
15. Usa los controles de VS Code o edita la zona para conservar sólo la frase acordada.
   - **Qué debes ver:** HTML válido, un solo `h1` y ningún marcador.
16. Busca `<<<<<<<` en el archivo.
   - **Qué debes ver:** cero resultados.
17. Guarda y actualiza el navegador.
   - **Qué debes ver:** el banner muestra la frase acordada y el resto del sitio conserva su formato.
18. Marca el conflicto como resuelto:

```powershell
git add proyecto-base/index.html
```

   - **Qué debes ver:** `git status` ya no muestra rutas sin integrar.
19. Cierra la integración:

```powershell
git commit -m "Resuelve mensaje del banner con cambios de dev"
```

   - **Qué debes ver:** un commit de merge.
20. Publica:

```powershell
git push
```

   - **Qué debes ver:** la rama de B incluye la resolución en GitHub.

## 5. Prompt sugerido para Copilot

> **Prompt para Copilot — persona A**
>
> Propón una frase de máximo ocho palabras para el encabezado principal de una tienda ficticia. Debe comunicar soluciones para el hogar, sin mencionar marcas ni promociones.

> **Prompt para Copilot — persona B**
>
> Propón una frase de máximo ocho palabras para el encabezado principal de una tienda ficticia. Debe comunicar variedad de productos, sin mencionar marcas ni promociones.

> **Prompt para Copilot — durante el conflicto**
>
> Explícame estos marcadores de conflicto sin modificar el archivo. Identifica la versión de mi rama y la versión de `dev`, y propón una frase que combine ambas intenciones en máximo ocho palabras.

## 6. Punto de control

`git status` está limpio, no existe ningún marcador de conflicto, el sitio abre correctamente y la rama publicada contiene un commit de resolución.

## 7. Si algo falla

- **No aparece el conflicto:** confirma que ambas ramas cambiaron exactamente el mismo contenido y que A ya fue integrada a `dev`.
- **El sitio muestra `<<<<<<< HEAD`:** los marcadores siguen en el archivo; vuelve a resolverlos antes de hacer commit.
- **Git dice que hay un merge en curso:** ejecuta `git status`, resuelve todos los archivos indicados y después usa `git add` y `git commit`.

## 8. Para profundizar

Durante un conflicto, `git diff --ours` y `git diff --theirs` ayudan a inspeccionar lados, pero no sustituyen la decisión de contenido.
