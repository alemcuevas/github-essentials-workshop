# 07. Despliegue a producción y diagnóstico de fallas

## 1. Objetivo del bloque

Seguir un cambio desde `dev` hasta `main` y diagnosticar bloqueos mediante evidencia.

## 2. Qué vas a lograr aquí

- Identificarás las compuertas entre un PR y producción.
- Leerás estados y registros antes de intentar una solución.
- Resolverás escenarios frecuentes con una secuencia de diagnóstico.

## 3. Concepto

Después de integrar cambios en `dev`, el equipo valida el conjunto y propone un PR hacia `main`. Integrar en `main` puede iniciar un despliegue, pero **merge** y **despliegue** no son lo mismo: el merge cambia el repositorio; un proceso posterior lleva esa versión a `[AJUSTAR: ambiente de producción]`.

Las compuertas reducen riesgos:

- la revisión confirma que otra persona entendió el cambio;
- las validaciones automáticas comprueban reglas repetibles;
- la aprobación de ambiente autoriza el momento y destino;
- el despliegue publica y verifica la versión.

Una compuerta puede tardar porque está en cola, ejecutándose o esperando aprobación. Si falla, no repitas a ciegas. Lee el mensaje exacto, identifica la primera causa útil y determina si el problema está en tu rama, el PR, una prueba o la infraestructura.

Usa cuatro preguntas: ¿qué intenté?, ¿en qué rama?, ¿qué esperaba?, ¿qué mensaje exacto apareció?

## 4. Manos a la obra

1. Abre el PR de integración de `dev` hacia `main` preparado por el instructor.
   - **Qué debes ver:** la base `main`, la comparación `dev` y el conjunto de cambios.
2. Abre la sección de validaciones o **Checks**.
   - **Qué debes ver:** estados pendientes, correctos o fallidos.
3. Selecciona una validación.
   - **Qué debes ver:** pasos con marcas y registros.
4. Localiza la primera línea que explica un error, si existe.
   - **Qué debes ver:** un archivo, una regla o un estado concreto; no sólo “Process completed”.
5. Identifica la compuerta pendiente en `[AJUSTAR: flujo de aprobación]`.
   - **Qué debes ver:** quién o qué debe actuar antes de continuar.
6. Abre `[AJUSTAR: panel o URL del ambiente]`.
   - **Qué debes ver:** el estado del despliegue y la versión publicada, si tu organización lo permite.
7. Diagnostica el caso “push rechazado” con:

```powershell
git status
git branch --show-current
git fetch origin
```

   - **Qué debes ver:** rama, estado local y referencias remotas actualizadas.
8. Diagnostica el caso “cambios no aparecen” con:

```powershell
git log --oneline -5
git status
```

   - **Qué debes ver:** si existe el commit y si todavía hay cambios sin registrar.
9. Diagnostica el caso “conflicto sin resolver” con:

```powershell
git status
```

   - **Qué debes ver:** rutas sin integrar y la operación en curso.
10. Abre la [guía de diagnóstico](../recursos/guia-de-diagnostico.md) y elige el síntoma que te asignó el instructor.
   - **Qué debes ver:** causa probable, verificación y solución.
11. Explica a tu pareja el diagnóstico sin ejecutar una solución destructiva.
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

- **No tienes acceso al panel:** usa la demostración del instructor y el marcador `[AJUSTAR: responsable del ambiente]`; no solicites credenciales ajenas.
- **La validación sigue pendiente:** verifica si está en cola o espera aprobación antes de volver a ejecutarla.
- **El registro contiene datos sensibles:** no lo pegues en Copilot; elimina tokens, nombres internos y datos personales antes de pedir ayuda.

## 8. Para profundizar

Investiga qué validación automática protege cada riesgo en tu organización y documenta quién es responsable cuando falla.
