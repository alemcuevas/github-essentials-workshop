# Glosario del taller

Esta referencia reúne palabras técnicas y términos de trabajo que aparecerán durante el taller. Cada definición usa lenguaje simple y explica el término sin depender de otra definición.

## Git y control de versiones

- **Branch o rama:** línea de trabajo identificada que permite cambiar el proyecto sin alterar de inmediato otras líneas.
- **Checkout:** acción histórica para cambiar de rama o recuperar archivos; en este taller usamos `git switch` para cambiar de rama.
- **Clonar:** descargar un repositorio con sus archivos, historial y conexión a GitHub.
- **Commit:** registro identificado de un conjunto de cambios, su autor, fecha y mensaje.
- **Conflicto:** situación en la que Git necesita una decisión humana para combinar cambios incompatibles.
- **Control de versiones:** sistema que conserva la evolución de los archivos y permite comparar o recuperar estados anteriores.
- **Dev:** rama compartida donde el equipo reúne y prueba mejoras antes de proponerlas a `main`.
- **Diff:** comparación que muestra líneas agregadas, eliminadas o modificadas.
- **Directorio de trabajo o working directory:** conjunto de archivos locales que puedes abrir y editar.
- **Fetch:** operación que consulta y descarga referencias de GitHub sin modificar tus archivos actuales.
- **Feature branch o rama de funcionalidad:** rama de corta duración dedicada a una mejora concreta.
- **Git:** herramienta que registra versiones, ramas y cambios principalmente en tu computadora.
- **HEAD:** referencia que señala el commit y, normalmente, la rama donde estás trabajando.
- **Historial:** secuencia de commits que muestra cómo evolucionó el repositorio.
- **Local:** copia o acción que existe en tu computadora y todavía puede no estar en GitHub.
- **Main:** rama que representa la versión aprobada para el flujo de producción del taller.
- **Merge o integración:** operación que incorpora los cambios de una rama en otra.
- **Origin:** nombre convencional de la conexión al repositorio de GitHub que clonaste.
- **Pull:** operación que trae cambios de la rama remota asociada y los integra en la rama actual.
- **Push:** operación que publica commits locales en GitHub.
- **Rama base:** rama que recibirá los cambios de un Pull Request.
- **Rama protegida:** rama con reglas que bloquean acciones hasta cumplir revisiones o validaciones.
- **Remoto:** repositorio alojado fuera de tu computadora, como el que está en GitHub.
- **Repositorio:** carpeta de proyecto administrada por Git junto con el historial de sus cambios.
- **Staging area o área de preparación:** espacio donde eliges exactamente qué cambios entrarán al siguiente commit.
- **Status:** resumen de la rama actual, cambios pendientes, cambios preparados y operaciones en curso.
- **Upstream:** rama remota asociada a una rama local para que `push` y `pull` conozcan su destino.

## GitHub y colaboración

- **Actions:** servicio de GitHub que ejecuta tareas automáticas definidas por el repositorio.
- **Aprobación:** confirmación de una persona revisora de que un Pull Request puede integrarse.
- **Check o validación:** comprobación automática o manual que informa si un cambio cumple una regla.
- **Colaborador:** persona autorizada para leer o modificar un repositorio.
- **Comentario de revisión:** observación colocada en un Pull Request para pedir, explicar o confirmar un ajuste.
- **Conversación resuelta:** comentario de revisión que ya recibió una respuesta o solución aceptada.
- **GitHub:** servicio para alojar repositorios Git, colaborar, revisar y automatizar trabajo.
- **GitHub Pages:** servicio que publica un sitio web estático directamente desde un repositorio.
- **Issue:** elemento de GitHub para registrar una tarea, idea, pregunta o problema.
- **Permiso de escritura:** autorización para publicar ramas y cambios en un repositorio.
- **Persona autora:** integrante que creó la rama o propuso el Pull Request.
- **Persona propietaria:** cuenta responsable del repositorio y de sus opciones de configuración.
- **Persona revisora:** integrante que examina el cambio, hace comentarios y decide si lo aprueba.
- **Pull Request o PR:** solicitud que presenta los cambios de una rama para conversar, validar e integrar.
- **Repositorio de ejemplo:** repositorio completo que muestra el resultado esperado del taller.
- **Repositorio de equipo:** repositorio independiente donde una pareja realiza sus ejercicios.
- **Repositorio plantilla o template:** repositorio utilizado como punto de partida para crear otros con los mismos archivos.
- **Regla de protección:** condición configurada en GitHub para controlar cómo se modifica una rama.
- **Visibilidad privada:** configuración que limita el acceso a personas autorizadas.
- **Visibilidad pública:** configuración que permite a cualquier persona ver el repositorio.
- **Workflow o flujo automatizado:** archivo que indica a GitHub Actions qué tarea ejecutar y cuándo hacerlo.

## Despliegue y ambientes

- **Ambiente:** destino con configuración propia donde se publica o verifica una aplicación.
- **Build o construcción:** proceso automático que prepara y comprueba una versión antes de publicarla.
- **Compuerta:** condición que debe cumplirse antes de avanzar, como una aprobación o un check verde.
- **Deploy o despliegue:** proceso que publica una versión de la aplicación en un ambiente.
- **Producción:** ambiente que representa la versión disponible para las personas usuarias.
- **Registro o log:** lista cronológica de mensajes producidos por un comando, validación o despliegue.
- **Versión desplegada:** estado específico del proyecto que está publicado en un ambiente.

## Herramientas y archivos del proyecto

- **Archivo:** unidad de contenido guardada con un nombre, como `index.html`.
- **Carpeta:** contenedor usado para organizar archivos y otras carpetas.
- **CSS:** lenguaje que define colores, espacios, tamaños y distribución visual de una página.
- **Editor:** aplicación usada para leer y modificar archivos; en el taller se usa VS Code.
- **HTML:** lenguaje que describe la estructura y el contenido de una página web.
- **HTML semántico:** uso de etiquetas que expresan la función del contenido, como `header`, `nav` o `article`.
- **Navegador:** aplicación que interpreta HTML y CSS para mostrar el sitio.
- **Recurso local:** imagen u otro archivo guardado dentro del repositorio, sin depender de un servicio externo.
- **Terminal:** espacio donde escribes comandos de texto para interactuar con Git y el sistema.
- **URL:** dirección que identifica una página o recurso en la web.
- **VS Code:** editor utilizado durante el taller para trabajar con archivos, Git y Copilot.

## GitHub Copilot y solicitudes

- **Contexto:** información que ayuda a Copilot a entender el archivo, objetivo y restricciones de una tarea.
- **GitHub Copilot:** asistente de IA que propone código, texto y explicaciones dentro de las herramientas de desarrollo.
- **Prompt o solicitud:** instrucción escrita que indica a Copilot qué resultado necesitas y qué límites debe respetar.
- **Propuesta:** respuesta generada por Copilot que debes revisar antes de aceptar.
- **Restricción:** condición que una solución debe respetar, como no utilizar JavaScript.

## Diseño y calidad

- **Accesibilidad:** práctica de crear contenido que pueda ser utilizado por personas con distintas capacidades y herramientas de apoyo.
- **Adaptable o responsive:** diseño que reorganiza su contenido para funcionar en pantallas de distintos tamaños.
- **Alcance:** límite de lo que una tarea o cambio debe incluir.
- **Criterio de éxito:** condición observable utilizada para decidir si una actividad quedó correctamente terminada.
- **Datos sensibles:** información que no debe publicarse, como contraseñas, tokens, llaves o datos personales.
- **Evidencia:** salida, captura, diff o resultado visible que demuestra lo ocurrido.
- **Mensaje descriptivo:** texto que explica la intención de un commit o Pull Request de forma específica.
- **Prueba manual:** comprobación realizada por una persona, por ejemplo abrir el sitio y revisar una sección.
- **Resultado esperado:** señal concreta que indica qué debes ver después de ejecutar un paso.
- **Secreto:** credencial utilizada para acceder a un sistema y que nunca debe guardarse directamente en el repositorio.

## Trabajo durante el taller

- **Bloque:** segmento de la agenda con un objetivo, explicación breve y práctica.
- **Bloqueo:** situación que impide continuar hasta resolver una causa concreta.
- **Conductor:** integrante que utiliza el teclado durante una parte del ejercicio.
- **Diagnóstico:** proceso de observar síntomas y evidencia para encontrar la causa de un problema.
- **Equipo o pareja:** dos participantes que comparten un repositorio y revisan mutuamente su trabajo.
- **Mentor:** persona de apoyo que ayuda a diagnosticar sin hacer todo el ejercicio por el participante.
- **Navegante:** integrante que lee las instrucciones, anticipa el siguiente paso y revisa lo que hace el conductor.
- **Punto de control:** verificación que debe completarse antes de avanzar al siguiente bloque.
- **Recuperación:** procedimiento para volver a un estado conocido cuando una persona se atrasa o se bloquea.
- **Sincronizar:** actualizar una copia para que incluya cambios recientes del repositorio compartido.
