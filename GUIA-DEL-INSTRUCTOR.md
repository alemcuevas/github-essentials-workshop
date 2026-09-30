# Guía del instructor

Esta guía permite impartir el taller sin haber participado en su diseño. El objetivo no es enseñar sintaxis de HTML: es hacer visible el ciclo de vida de un cambio y dar a cada participante herramientas para diagnosticar bloqueos.

## Resultado esperado

Al terminar, cada equipo habrá llevado una mejora del sitio ficticio Mercado Nube por este recorrido:

`archivo local → staging → commit → push → Pull Request → revisión → dev → validación → main`

Los participantes deben poder explicar dónde está su cambio, quién puede verlo y cuál es la siguiente compuerta.

## Preparación del instructor

Completa estos puntos antes de abrir el salón:

- [ ] Crea `[AJUSTAR: repositorio o repositorios del taller]` a partir de este material.
- [ ] Confirma que todos pueden acceder a `[AJUSTAR: nombre de la organización]`.
- [ ] Crea las ramas `dev` y `main`.
- [ ] Configura protección en `dev` y `main`: Pull Request obligatorio y, si la plataforma lo permite, una aprobación.
- [ ] Impide el push directo a `main`.
- [ ] Prepara una validación automática simple o explica la validación existente en `[AJUSTAR: nombre de la validación]`.
- [ ] Define si cada pareja tendrá su repositorio o si compartirán uno.
- [ ] Asigna parejas o equipos de 3 antes del bloque 4.
- [ ] Identifica a los mentores de apoyo y asígnales una zona del salón.
- [ ] Prueba todo el recorrido con una cuenta sin permisos administrativos.
- [ ] Conserva una rama de respaldo por bloque: `respaldo/02`, `respaldo/03`, etcétera.

## Reglas de facilitación

1. Muestra un solo paso y espera a que la mayoría vea el resultado esperado.
2. Pide ejecutar `git status` antes y después de cada operación importante.
3. Pregunta “¿en qué rama estás?” antes de diagnosticar.
4. No resuelvas un error tomando el teclado de inmediato; pide al participante leer el mensaje.
5. Copilot puede explicar y proponer, pero el participante revisa, decide y ejecuta Git.
6. Usa lenguaje espacial: “local”, “GitHub”, “tu rama”, “rama compartida”.
7. Evita introducir comandos que no estén en el módulo salvo que sean necesarios para recuperar el ejercicio.

## Modelo mental que se repite

Usa la analogía de preparar un envío:

- **Working directory:** la mesa donde editas.
- **Staging area:** la caja donde eliges qué vas a enviar.
- **Commit:** el paquete cerrado, identificado y conservado en el historial local.
- **Push:** el transporte del paquete a GitHub.
- **Pull Request:** la solicitud para incorporar el paquete al trabajo compartido.
- **Revisión y validaciones:** las inspecciones antes de permitir la entrada.
- **Merge:** la incorporación autorizada.

Aclara que un commit no es “guardar”: el archivo ya puede estar guardado y todavía no formar parte de un commit.

## Guion por bloque

### Bloque 1 — Arranque (15 minutos)

**0:00–0:05 | Puntos clave**

- Git registra versiones; GitHub aloja repositorios y coordina personas.
- Un repositorio contiene archivos y su historial.
- Un repositorio personal pertenece a una cuenta; uno de organización pertenece al equipo y aplica reglas comunes.
- Clonar crea una copia local conectada con el repositorio remoto.

**Qué decir**

> Hoy no aprenderemos a escribir HTML de memoria. Copilot nos ayudará con el código; nosotros aprenderemos a reconocer dónde está un cambio y cómo moverlo con seguridad.

**0:05–0:15 | Demostración y práctica**

1. Muestra **Code > HTTPS** en GitHub.
2. Clona desde VS Code.
3. Abre la terminal.
4. Ejecuta `git status`, `git branch --show-current` y `git remote -v`.
5. Abre `proyecto-base/index.html` en el navegador.

**Qué debe verse:** rama `main`, árbol limpio y un remoto llamado `origin`.

**Pregunta frecuente:** “¿Clonar descarga sólo los archivos?”  
**Respuesta:** descarga los archivos, el historial y la conexión al remoto.

**Señal de alerta:** más de cinco personas siguen autenticándose al minuto 8.  
**Acción:** un mentor crea una mesa de soporte; el grupo continúa con una demostración compartida.

### Bloque 2 — Commit y push (30 minutos)

**0:15–0:23 | Puntos clave**

- Guardar cambia el archivo; `git add` elige; `git commit` registra; `git push` publica.
- Un mensaje explica intención, no sólo el nombre del archivo.
- Copilot genera el contenido, pero la persona revisa el diff, decide qué incluir y confirma la rama.

**Qué demostrar**

1. Pide a Copilot tarjetas de productos.
2. Guarda y actualiza el navegador.
3. Ejecuta `git status` y `git diff`.
4. Ejecuta `git add`, `git commit` y `git push`.
5. Muestra el commit en GitHub.

**Qué decir**

> Antes del push, el commit sólo existe en esta computadora. Después del push, el equipo puede verlo en GitHub, pero todavía no significa que esté en producción.

**Pregunta frecuente:** “¿Por qué no aparece mi cambio en GitHub si ya hice commit?”  
**Respuesta:** el commit es local hasta ejecutar `push`.

**Señal de alerta:** participantes ejecutan `git add .` sin revisar.  
**Acción:** detén 30 segundos y muestra `git status`; refuerza que staging es una selección.

### Bloque 3 — Ramas (30 minutos)

**0:45–0:53 | Puntos clave**

- Una rama es una línea de trabajo aislada.
- `feature` contiene una mejora breve; `dev` reúne cambios para validación; `main` representa lo aprobado para producción.
- Una rama protegida evita que una sola persona salte revisiones.

**Qué demostrar**

1. Intenta explicar, sin forzar, por qué un push directo a `main` sería rechazado.
2. Crea `feature/categorias`.
3. Genera categorías con Copilot.
4. Publica la rama con `git push -u origin feature/categorias`.

**Qué decir**

> La protección no desconfía de una persona; protege al equipo de errores, prisas y cambios sin contexto.

**Pregunta frecuente:** “¿Crear una rama duplica todo?”  
**Respuesta:** Git no crea otra carpeta completa; crea un apuntador a una línea del historial.

**Señal de alerta:** nombres como `prueba2-final-ahora-si`.  
**Acción:** comparte el patrón `feature/descripción-breve`.

### Receso (10 minutos)

Pide guardar cambios y ejecutar `git status`. Nadie debe irse con un merge a medias.

### Bloque 4 — Colaboración (30 minutos)

**1:25–1:33 | Puntos clave**

- `fetch` consulta cambios remotos sin mezclarlos.
- `pull` trae e integra la rama remota configurada.
- Actualizarse antes de integrar reduce sorpresas.

**Organización**

- Persona A agrega una promoción.
- Persona B agrega categorías o estilos.
- En equipos de 3, persona C revisa el historial y coordina el orden.

**Qué demostrar**

1. Ejecuta `git fetch`.
2. Muestra `git log --oneline --all --graph --decorate -10`.
3. Actualiza `dev` con `git pull`.
4. Regresa a la rama de trabajo e integra `dev` con `git merge dev`.

**Pregunta frecuente:** “¿`pull` y `fetch` son iguales?”  
**Respuesta:** `fetch` actualiza tu conocimiento del remoto; `pull` además integra en tu rama actual.

**Señal de alerta:** alguien edita en la rama de su compañero.  
**Acción:** pide `git branch --show-current` a todo el equipo.

### Bloque 5 — Conflictos (30 minutos)

**1:55–2:03 | Puntos clave**

- Un conflicto ocurre cuando Git no puede decidir entre cambios incompatibles.
- Los marcadores separan la versión actual y la versión entrante.
- Resolver significa elegir el resultado final, quitar marcadores, probar y cerrar con un commit.

**Preparación controlada**

1. Ambas personas parten de la misma `dev`.
2. Cada una crea una rama distinta.
3. Ambas cambian exactamente el texto del mismo encabezado del banner en `index.html`.
4. Integra primero la rama A a `dev`.
5. La persona B actualiza `dev` e intenta `git merge dev` desde su rama.

**Qué demostrar**

- `<<<<<<< HEAD`, `=======` y `>>>>>>> dev`.
- Las opciones del editor: aceptar actual, entrante o ambas.
- El resultado final debe tener una sola frase válida, no ambas por accidente.
- `git add` y `git commit` cierran la resolución.

**Pregunta frecuente:** “¿Copilot puede resolverlo?”  
**Respuesta:** puede explicar y proponer una combinación, pero el equipo decide cuál refleja el requisito.

**Señal de alerta:** alguien borra el archivo completo o todos los marcadores sin comprenderlos.  
**Acción:** usa la rama de respaldo y repite con dos líneas simples.

### Receso (10 minutos)

Confirma que ningún equipo tenga `unmerged paths` en `git status`.

### Bloque 6 — Pull Request (30 minutos)

**2:35–2:43 | Puntos clave**

- Un Pull Request propone integrar una rama y conserva la conversación.
- Una buena descripción explica qué, por qué, cómo validar y riesgos.
- Aprobar no es un gesto social: confirma que alguien revisó el cambio.

**Qué demostrar**

1. Abre un PR de `feature/...` hacia `dev`.
2. Revisa **Files changed**.
3. Agrega un comentario concreto.
4. La persona autora responde y, si aplica, publica un ajuste.
5. Una persona distinta aprueba.
6. Integra el PR.

**Pregunta frecuente:** “¿Necesito abrir otro PR si hago un ajuste?”  
**Respuesta:** no; los nuevos commits publicados en la misma rama aparecen en el PR abierto.

**Señal de alerta:** PR hacia `main` en vez de `dev`.  
**Acción:** cambia la rama base antes de revisar.

### Bloque 7 — Despliegue y diagnóstico (20 minutos)

**3:05–3:11 | Puntos clave**

- Integrar a `main` puede iniciar un flujo automatizado, pero merge y despliegue no son sinónimos.
- Cada compuerta reduce un riesgo: revisión, pruebas, aprobación del ambiente y despliegue.
- “Está tardando” puede significar que una validación sigue ejecutándose o espera aprobación.

**Qué demostrar**

1. Abre la pestaña **Checks** o `[AJUSTAR: panel de despliegue]`.
2. Muestra estados pendiente, correcto y fallido.
3. Abre un registro y localiza la primera causa útil.
4. Recorre tres tarjetas de diagnóstico del módulo.

**Pregunta frecuente:** “¿Dónde está producción?”  
**Respuesta:** en este taller es `[AJUSTAR: ambiente/URL de producción]`; en cada organización el destino y sus permisos cambian.

**Señal de alerta:** alguien vuelve a ejecutar todo sin leer el error.  
**Acción:** pide decir en voz alta síntoma, rama, operación y primera línea de error.

### Bloque 8 — Reto final (30 minutos)

**3:25–3:55 | Trabajo autónomo**

Cada equipo debe:

1. elegir una mejora;
2. crear una rama desde `dev`;
3. pedir el código a Copilot;
4. revisar y publicar commits pequeños;
5. actualizar la rama;
6. abrir un PR hacia `dev`;
7. revisar el PR de otro equipo;
8. resolver cualquier bloqueo;
9. explicar el recorrido del cambio.

No des instrucciones paso a paso. Los mentores sólo hacen preguntas de diagnóstico.

**Criterio de éxito**

- La rama tiene un nombre claro.
- No hay secretos ni archivos ajenos.
- El PR tiene descripción y validación.
- Otra persona revisó.
- El equipo puede señalar dónde está su cambio.

### Bloque 9 — Cierre (5 minutos)

**3:55–4:00**

- Pide a tres personas completar: “Antes pensaba que commit era…, ahora entiendo que…”.
- Repite la ruta completa del cambio.
- Señala los recursos de referencia.
- Propón practicar con una mejora pequeña por semana.

## Preguntas frecuentes generales

### “¿GitHub Copilot puede hacer todo el flujo?”

Puede sugerir código, mensajes y explicaciones. La persona sigue siendo responsable de revisar el cambio, elegir archivos, confirmar la rama, proteger información y aprobar integraciones.

### “¿Qué pasa si hice commit en la rama equivocada?”

Detén el push y consulta la guía de diagnóstico. Si ya publicaste, no reescribas un historial compartido sin coordinación. Durante el taller, llama a un mentor.

### “¿Por qué no trabajamos directo en main?”

Porque `main` representa una versión aprobada. Las ramas y PR agregan aislamiento, contexto, revisión y trazabilidad.

### “¿Un conflicto significa que alguien se equivocó?”

No. Significa que hubo cambios que Git no puede combinar automáticamente. Es una decisión de contenido, no un castigo.

### “¿Por qué una validación tarda?”

Puede estar esperando un agente disponible, ejecutando pruebas o esperando aprobación manual. Abre el detalle antes de repetirla.

## Cómo delegar dudas a mentores

Asigna un mentor por cada 10–12 participantes. Usa este protocolo:

1. El participante muestra `git status`.
2. Dice qué esperaba ver.
3. Lee el mensaje exacto.
4. El mentor clasifica: entorno, rama, sincronización, conflicto, PR o validación.
5. El mentor hace una pregunta antes de dar un comando.
6. Si el caso afecta permisos o infraestructura, escala al instructor y usa `[AJUSTAR: canal de soporte]`.

Los mentores no deben introducir `reset --hard`, force push ni comandos destructivos durante el taller.

## Señales de alerta del grupo

| Señal | Interpretación probable | Respuesta |
|---|---|---|
| Muchas terminales muestran rutas distintas | Abrieron la carpeta equivocada | Ejecutar `git status` y reabrir el repositorio |
| La mayoría copia sin leer | Ritmo demasiado rápido | Pausa y pide predecir el resultado del siguiente comando |
| Aparecen archivos inesperados en staging | Se usó `git add .` sin revisar | Mostrar `git status` y retirar sólo lo no deseado |
| PR dirigidos a distintas ramas | No se reforzó la estrategia | Dibujar `feature → dev → main` |
| Conflictos diferentes al planeado | Las ramas no partieron del mismo punto | Usar ramas de respaldo |
| Una pareja domina el teclado | No hay rotación | Cambiar de conductor cada 8 minutos |

## Si vas retrasado, recorta esto

Recorta en este orden y conserva siempre el conflicto, el PR y el reto:

1. **Bloque 2:** genera cuatro tarjetas en vez de seis; ahorra 4 minutos.
2. **Bloque 3:** explica la protección con una captura preparada; no hagas el intento de push; ahorra 3 minutos.
3. **Bloque 4:** omite la visualización avanzada del grafo; conserva `fetch`, `pull` y actualización; ahorra 4 minutos.
4. **Bloque 6:** usa un solo comentario de revisión por PR; ahorra 3 minutos.
5. **Bloque 7:** diagnostica dos casos en grupo y deja el resto como recurso; ahorra 5 minutos.

No recortes:

- la verificación inicial del entorno;
- el conflicto controlado;
- la revisión por otra persona;
- el reto final;
- el cierre con el modelo `feature → dev → main`.

Si el retraso supera 20 minutos, entrega una rama de respaldo al inicio del bloque siguiente. No aceleres leyendo comandos sin contexto.
