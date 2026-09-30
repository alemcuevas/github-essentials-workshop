# 06. Pull Request, revisión y aprobación del cambio

## 1. Objetivo del bloque

Proponer una integración hacia `dev`, recibir revisión y completar el merge con trazabilidad.

## 2. Qué vas a lograr aquí

- Abrirás un Pull Request con contexto y pasos de validación.
- Revisarás cambios de otra persona y responderás comentarios.
- Aprobarás e integrarás una mejora sin push directo.

## 3. Concepto

Un **Pull Request**, o PR, es una solicitud para integrar una rama en otra. No es sólo un botón de merge: reúne la diferencia entre ramas, el motivo del cambio, comentarios, aprobaciones y resultados automáticos.

Una buena descripción responde: ¿qué cambia?, ¿por qué?, ¿cómo lo verificaste? y ¿qué riesgo queda? En **Files changed** se revisa el contenido real. Un comentario útil señala una línea y explica el efecto esperado; “está mal” no da una acción clara.

Las revisiones humanas verifican intención, claridad y experiencia. Las automáticas pueden revisar formato, seguridad o construcción. Si agregas commits a la rama publicada, el mismo PR se actualiza; no necesitas abrir otro.

La persona autora responde comentarios, ajusta si es necesario y vuelve a publicar. Otra persona aprueba. La rama protegida puede impedir el merge mientras falte una aprobación, haya conflicto o una validación falle.

## 4. Manos a la obra

1. Confirma que estás en tu rama de trabajo:

```powershell
git branch --show-current
```

   - **Qué debes ver:** `feature/mensaje-banner-b` o la rama indicada por el instructor.
2. Confirma que todo está publicado:

```powershell
git status
git push
```

   - **Qué debes ver:** directorio limpio y `Everything up-to-date`.
3. Abre el repositorio en GitHub.
   - **Qué debes ver:** un aviso para comparar tu rama o la pestaña **Pull requests**.
4. Selecciona **New pull request**.
   - **Qué debes ver:** selectores de rama base y rama de comparación.
5. Elige `dev` como base y tu rama `feature/...` como compare.
   - **Qué debes ver:** una flecha de `feature/...` hacia `dev`.
6. Revisa la lista de commits y **Files changed**.
   - **Qué debes ver:** sólo la mejora esperada y la resolución, sin secretos ni archivos ajenos.
7. Escribe un título orientado al resultado.
   - **Qué debes ver:** un título como `Mejora el mensaje principal de la tienda`.
8. Usa el prompt de este módulo para redactar la descripción y ajústala con lo que realmente hiciste.
   - **Qué debes ver:** secciones de cambio, motivo, validación y riesgos.
9. Selecciona **Create pull request**.
   - **Qué debes ver:** el PR abierto con estado de revisión.
10. Solicita revisión a tu pareja.
   - **Qué debes ver:** su usuario aparece como reviewer.
11. Cambien de rol y abre **Files changed** del PR de tu pareja.
   - **Qué debes ver:** líneas agregadas y eliminadas.
12. Deja un comentario específico sobre una línea.
   - **Qué debes ver:** el comentario incluye una observación y una acción o pregunta verificable.
13. Regresa a tu PR y responde el comentario.
   - **Qué debes ver:** una respuesta que confirma el cambio o explica por qué se conserva.
14. Si el comentario requiere ajuste, modifica el archivo en tu rama local.
   - **Qué debes ver:** sólo el ajuste solicitado.
15. Registra y publica el ajuste:

```powershell
git add proyecto-base/index.html proyecto-base/styles.css
git commit -m "Ajusta mejora según revisión"
git push
```

   - **Qué debes ver:** el nuevo commit aparece automáticamente en el mismo PR.
16. La persona revisora vuelve a comprobar **Files changed** y selecciona **Review changes > Approve**.
   - **Qué debes ver:** una aprobación en el PR.
17. Confirma que las validaciones estén correctas.
   - **Qué debes ver:** indicadores verdes o el estado definido en `[AJUSTAR: validación del repositorio]`.
18. Selecciona el método de merge indicado por el instructor.
   - **Qué debes ver:** GitHub confirma que el PR se integró a `dev`.
19. Actualiza tu `dev` local:

```powershell
git switch dev
git pull --ff-only
```

   - **Qué debes ver:** tu mejora está presente en `dev`.

## 5. Prompt sugerido para Copilot

> **Prompt para Copilot**
>
> Redacta una descripción breve de Pull Request en español de México con estas secciones: “Qué cambia”, “Por qué”, “Cómo lo validé” y “Riesgos”. El cambio mejora el banner de una tienda ficticia y resolvió un conflicto con `dev`. No inventes pruebas ni aprobaciones; usa casillas para que yo complete lo que sí verifiqué.

> **Prompt para Copilot**
>
> Explícame este comentario de revisión en lenguaje simple. Dime qué resultado solicita, qué archivo podría cambiar y cómo verificarlo. No modifiques código.

## 6. Punto de control

El PR muestra base `dev`, descripción completa, revisión de otra persona, validaciones correctas y estado **Merged**. Tu `dev` local contiene el cambio.

## 7. Si algo falla

- **El PR apunta a `main`:** usa **Edit** y cambia la base a `dev` antes de solicitar aprobación.
- **El merge está bloqueado:** abre el mensaje de GitHub y determina si falta aprobación, validación o resolución de conflicto.
- **El ajuste no aparece en el PR:** confirma que hiciste push a la misma rama usada como compare.

## 8. Para profundizar

Compara merge commit, squash y rebase en la documentación de tu organización; cada estrategia conserva el historial de forma distinta.
