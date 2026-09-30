# 07. Despliegue a producción y diagnóstico de fallas

## 1. Objetivo del bloque

Seguir un cambio desde `dev` hasta `main` y diagnosticar bloqueos mediante evidencia.

## 2. Qué vas a lograr aquí

- Identificarás las compuertas entre un PR y producción.
- Leerás estados y registros antes de intentar una solución.
- Resolverás escenarios frecuentes con una secuencia de diagnóstico.

## 3. Concepto

Después de integrar cambios en `dev`, el equipo valida el conjunto y propone un PR hacia `main`. Integrar en `main` puede iniciar un despliegue, pero **merge** y **despliegue** no son lo mismo: el merge cambia el repositorio; el workflow **Publicar Contoso Retail en GitHub Pages** lleva la carpeta `proyecto-base` al sitio público del equipo.

Las compuertas reducen riesgos:

- la revisión confirma que otra persona entendió el cambio;
- las validaciones automáticas comprueban reglas repetibles;
- la aprobación de ambiente autoriza el momento y destino;
- el despliegue publica y verifica la versión.

Una compuerta puede tardar porque está en cola, ejecutándose o esperando aprobación. Si falla, no repitas a ciegas. Lee el mensaje exacto, identifica la primera causa útil y determina si el problema está en tu rama, el PR, una prueba o la infraestructura.

Usa cuatro preguntas: ¿qué intenté?, ¿en qué rama?, ¿qué esperaba?, ¿qué mensaje exacto apareció?

## 4. Manos a la obra

1. La persona A abre un PR en el repositorio del equipo desde `dev` hacia `main`.
   - **Qué debes ver:** la base `main`, la comparación `dev` y el conjunto de cambios.
2. La persona B revisa el PR y abre **Checks**.
   - **Qué debes ver:** estados pendientes, correctos o fallidos.
3. Selecciona **Validar repositorio**.
   - **Qué debes ver:** comprobaciones de archivos, alcance tecnológico, marcadores de conflicto, marca y HTML.
4. Si una comprobación falla, localiza la primera línea que explica el error.
   - **Qué debes ver:** un archivo, una regla o un estado concreto; no sólo “Process completed”.
5. Cuando la validación esté verde, la persona B aprueba e integra el PR.
   - **Qué debes ver:** `dev` queda integrado en `main`.
6. Abre **Actions > Publicar Contoso Retail en GitHub Pages**.
   - **Qué debes ver:** un despliegue iniciado por el cambio en `main`.
7. Abre la URL indicada en el paso **Deploy to GitHub Pages**.
   - **Qué debes ver:** Contoso Retail publicado desde el repositorio del equipo.
8. Diagnostica el caso “push rechazado” con:

```powershell
git status
git branch --show-current
git fetch origin
```

   - **Qué debes ver:** rama, estado local y referencias remotas actualizadas.
9. Diagnostica el caso “cambios no aparecen” con:

```powershell
git log --oneline -5
git status
```

   - **Qué debes ver:** si existe el commit y si todavía hay cambios sin registrar.
10. Diagnostica el caso “conflicto sin resolver” con:

```powershell
git status
```

   - **Qué debes ver:** rutas sin integrar y la operación en curso.
11. Abre la [guía de diagnóstico](../recursos/guia-de-diagnostico.md) y elige el síntoma que te asignó el instructor.
   - **Qué debes ver:** causa probable, verificación y solución.
12. Explica a tu pareja el diagnóstico sin ejecutar una solución destructiva.
   - **Qué debes ver:** una secuencia basada en evidencia, no una lista de comandos al azar.

## 5. Prompt sugerido para Copilot

> **Prompt para Copilot**
>
> Analiza este mensaje de Git o GitHub: `[PEGA AQUÍ EL MENSAJE SIN CREDENCIALES]`. Explícalo en español simple. Separa: síntoma, causa probable, cómo verificarla y siguiente acción segura. No sugieras force push, borrar archivos ni `reset --hard`.

> **Prompt para Copilot**
>
> Explícame este registro de validación. Identifica la primera causa útil, distingue error principal de consecuencias y dime qué evidencia debo reunir antes de cambiar código. No inventes infraestructura.

## 6. Punto de control

Puedes señalar si un cambio está local, publicado, en revisión, integrado o desplegado, y puedes explicar una falla con síntoma, causa probable, verificación y acción segura.

## 7. Si algo falla

- **Pages devuelve 404:** abre el workflow, confirma que terminó en verde y espera uno o dos minutos antes de actualizar.
- **El workflow no inicia:** confirma que el PR realmente se integró en `main` y que Actions está habilitado en el repositorio.
- **La validación sigue pendiente:** verifica si está en cola o espera aprobación antes de volver a ejecutarla.
- **El registro contiene datos sensibles:** no lo pegues en Copilot; elimina tokens, nombres internos y datos personales antes de pedir ayuda.

## 8. Para profundizar

Investiga qué validación automática protege cada riesgo en tu organización y documenta quién es responsable cuando falla.
