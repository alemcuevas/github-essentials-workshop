# 08. Reto final en equipo, sin acompañamiento

## 1. Objetivo del bloque

Completar de manera autónoma el ciclo de una mejora desde `dev` hasta un Pull Request revisado.

## 2. Qué vas a lograr aquí

- Planearás y publicarás una mejora pequeña con Copilot.
- Coordinarás commits, actualización, revisión y diagnóstico.
- Explicarás el recorrido del cambio y la responsabilidad de cada persona.

## 3. Concepto

Este reto reúne todo el taller. Imagina una línea de producción: una idea entra en una rama aislada, se convierte en commits revisables, se publica, se actualiza con el trabajo común y pasa por revisión antes de entrar a `dev`.

La meta no es crear la tienda más grande. La meta es demostrar control: saber en qué rama estás, revisar lo generado por Copilot, mantener pequeño el cambio, no subir información sensible y usar evidencia cuando algo falla.

Trabajen en parejas o equipos de 3. Rótense como **conductor**, quien usa el teclado; **navegante**, quien lee el módulo y anticipa el siguiente paso; y **revisor**, quien comprueba el diff y el PR. Si son dos, alternen conductor y navegante; ambos revisan.

## 4. Manos a la obra

1. Elijan una mejora: distintivos de oferta, sección de beneficios, guía de compra o mejora adaptable.
   - **Qué debes ver:** una mejora que cabe en 20 minutos y no requiere JavaScript.
2. Escriban en una frase el resultado esperado.
   - **Qué debes ver:** un criterio observable, por ejemplo “Tres beneficios aparecen antes del pie”.
3. Cambien a `dev`:

```powershell
git switch dev
```

   - **Qué debes ver:** `dev` es la rama actual.
4. Actualicen:

```powershell
git pull --ff-only
```

   - **Qué debes ver:** `dev` coincide con GitHub.
5. Creen una rama con nombre descriptivo:

```powershell
git switch -c feature/nombre-breve
```

   - **Qué debes ver:** una nueva rama `feature/...`.
6. Pidan a Copilot el HTML y CSS de la mejora.
   - **Qué debes ver:** una propuesta sin JavaScript, dependencias, marcas ni datos reales.
7. Revisen el código antes de aceptarlo.
   - **Qué debes ver:** HTML semántico, clases claras y CSS compatible con las variables existentes.
8. Guarden y prueben en el navegador.
   - **Qué debes ver:** el resultado esperado sin romper encabezado, productos, categorías ni pie.
9. Ejecuten:

```powershell
git status
git diff
```

   - **Qué debes ver:** sólo los archivos y líneas de su mejora.
10. Creen un primer commit coherente:

```powershell
git add proyecto-base/index.html proyecto-base/styles.css
git commit -m "Agrega [descripción breve del resultado]"
```

   - **Qué debes ver:** un commit con intención clara.
11. Publiquen:

```powershell
git push -u origin HEAD
```

   - **Qué debes ver:** la rama en GitHub.
12. Consulten cambios recientes:

```powershell
git fetch origin
```

   - **Qué debes ver:** referencias remotas actualizadas.
13. Integren la versión reciente de `dev` en su rama si cambió:

```powershell
git merge origin/dev
```

   - **Qué debes ver:** integración automática o un conflicto que deben resolver con el método aprendido.
14. Prueben nuevamente y publiquen cualquier resolución:

```powershell
git push
```

   - **Qué debes ver:** rama actualizada y sitio funcional.
15. Abran un PR desde su rama hacia `dev`.
   - **Qué debes ver:** título, descripción, pasos de validación y cambios esperados.
16. Soliciten revisión a otro equipo.
   - **Qué debes ver:** una persona revisora asignada.
17. Revisen el PR que recibieron y dejen un comentario útil o una aprobación justificada.
   - **Qué debes ver:** evidencia de revisión humana.
18. Respondan comentarios y publiquen un ajuste si se solicita.
   - **Qué debes ver:** conversación resuelta y, si aplica, un commit adicional.
19. Comprueben validaciones y completen el merge cuando las reglas lo permitan.
   - **Qué debes ver:** PR integrado a `dev` o bloqueo explicado con evidencia.
20. Expliquen al instructor el recorrido de su cambio en 60 segundos.
   - **Qué debes ver:** el equipo distingue local, commit, GitHub, PR, `dev`, `main` y despliegue.

## 5. Prompt sugerido para Copilot

> **Prompt para Copilot**
>
> Implementa una sección de tres beneficios para Mercado Nube: compra sencilla, variedad y atención clara. Usa HTML semántico y CSS puro compatible con las variables existentes. Debe ser adaptable, accesible y verse bien sin imágenes. No uses JavaScript, dependencias, marcas reales ni datos de contacto.

> **Prompt para Copilot**
>
> Revisa el diff de mi mejora como si fueras revisor de Pull Request. Señala únicamente problemas verificables de HTML semántico, accesibilidad, CSS adaptable o alcance inesperado. No reescribas todo ni inventes requisitos.

## 6. Punto de control

El equipo tiene un PR integrado o un bloqueo correctamente diagnosticado; el cambio fue revisado por otra persona, no contiene datos sensibles y todos pueden explicar dónde está cada versión.

## 7. Si algo falla

- **El equipo pierde tiempo eligiendo mejora:** usa la sección de tres beneficios del prompt sugerido.
- **El diff incluye trabajo ajeno:** confirma la base de la rama y pide al mentor revisar el historial antes de abrir el PR.
- **Una validación o protección bloquea el merge:** documenta el estado, la causa y el responsable; diagnosticar correctamente también cumple esa parte del reto.

## 8. Para profundizar

Propón una validación automática que proteja una regla concreta del proyecto y explica qué riesgo reduciría antes de implementarla.
