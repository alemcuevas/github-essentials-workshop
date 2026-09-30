# Prompts útiles para GitHub Copilot

Antes de enviar un error o código a Copilot, elimina credenciales, datos personales y nombres internos. Revisa siempre la respuesta antes de aplicarla.

## Generar contenido del sitio

> En `proyecto-base/index.html`, crea `[DESCRIBE LA SECCIÓN]` para Contoso Retail, una tienda ficticia. Usa HTML semántico, contenido genérico y clases descriptivas. No uses JavaScript, frameworks, estilos en línea, marcas reales ni datos de contacto.

> Genera cuatro tarjetas de productos ficticios con nombre, precio en pesos mexicanos, una imagen local de `proyecto-base/assets` y texto alternativo útil. Incluye productos de categorías distintas. No uses marcas reales ni URLs externas.

> Agrega una sección de categorías con enlaces internos a Electrónica, Hogar, Despensa, Ropa y Juguetes. Usa una lista semántica y conserva los encabezados existentes.

## Mejorar estilos

> Genera CSS puro para `[NOMBRE DE CLASE]` usando las variables existentes en `:root`. Debe ser adaptable, conservar contraste legible y tener foco visible. No cambies selectores ajenos.

> Revisa estos estilos para pantallas menores a 640 px. Propón el cambio mínimo para evitar desbordamiento y mantener elementos táctiles claros. No uses dependencias.

> Mejora la jerarquía visual de `[SECCIÓN]` sin cambiar el HTML. Reutiliza colores, radio y sombra existentes. Explica cada selector nuevo en una lista separada, no con comentarios innecesarios dentro del CSS.

## Explicar un error

> Analiza este mensaje: `[PEGA EL MENSAJE SIN CREDENCIALES]`. Explícalo en español simple. Separa síntoma, causa probable, cómo verificar y siguiente acción segura. No sugieras force push, borrar archivos ni `reset --hard`.

> Tengo este resultado de `git status`: `[PEGA LA SALIDA]`. Dime en qué estado está el repositorio, si hay una operación en curso y cuál es el siguiente paso más seguro. No ejecutes comandos.

> Este check de GitHub falló: `[PEGA SÓLO LAS LÍNEAS RELEVANTES]`. Identifica la primera causa útil y distingue los errores secundarios. No inventes detalles de infraestructura.

## Explicar un cambio que no entiendo

> Explica este diff para una persona que comienza con Git. Resume intención, archivos afectados, comportamiento antes y después, y posibles riesgos. Señala cualquier dato sensible. No modifiques el código.

> Copilot propuso este HTML y CSS: `[PEGA EL FRAGMENTO]`. Explica qué hace cada bloque, cómo se adapta a pantallas pequeñas y qué debo probar antes de aceptarlo.

> Compara estas dos versiones y dime qué comportamiento cambia. No elijas por mí; presenta ventajas, riesgos y una verificación observable.

## Ayudar a resolver un conflicto

> Explica estos marcadores de conflicto: `[PEGA SÓLO EL FRAGMENTO SIN DATOS SENSIBLES]`. Identifica mi versión (`HEAD`) y la versión entrante. Propón un resultado final que conserve ambas intenciones, pero no modifiques el archivo.

> Revisa mi resolución de conflicto. Confirma que no queden marcadores, que el HTML siga siendo válido y que no se haya duplicado contenido. Señala cambios concretos; no reescribas todo.

> Crea una lista de verificación para probar el sitio después de resolver este conflicto en `[SECCIÓN]`. Incluye revisión visual, `git status` y búsqueda de marcadores.

## Escribir el mensaje de commit

> Sugiere tres mensajes de commit breves, en modo imperativo y orientados al resultado, para este diff: `[RESUMEN DEL CAMBIO]`. No uses “cambios”, “update” ni nombres de personas.

> Convierte esta descripción en un mensaje de commit de máximo 60 caracteres: `[DESCRIPCIÓN]`. Debe explicar qué resultado agrega, no qué archivo edité.

> Revisa este mensaje de commit: `[MENSAJE]`. Dime si es específico y si corresponde a un solo propósito. Propón una alternativa sólo si hace falta.

## Escribir la descripción del Pull Request

> Redacta una descripción de Pull Request con “Qué cambia”, “Por qué”, “Cómo lo validé” y “Riesgos”. Usa esta información: `[DATOS REALES DEL CAMBIO]`. No inventes pruebas, aprobaciones ni resultados; deja casillas para lo pendiente.

> Resume estos commits como un título de PR orientado al resultado y tres viñetas: `[LISTA DE COMMITS]`. La base es `dev`. No afirmes que llegó a producción.

> Crea pasos manuales para validar este PR: `[DESCRIPCIÓN]`. Cada paso debe ser una sola acción y debe indicar qué se espera ver.

## Pedir una revisión

> Revisa este diff como revisor de Pull Request. Busca únicamente problemas verificables de alcance, HTML semántico, accesibilidad, CSS adaptable o datos sensibles. Para cada hallazgo indica archivo, efecto y forma de comprobarlo.

> Ayúdame a responder este comentario de revisión: `[COMENTARIO]`. La respuesta debe confirmar lo que entendí, indicar si haré el ajuste y explicar cómo lo validaré. No uses tono defensivo.

## Límites que conviene agregar

Incluye uno o más de estos límites cuando correspondan:

- “No ejecutes comandos.”
- “No modifiques archivos fuera de `proyecto-base`.”
- “No uses JavaScript, npm, frameworks ni dependencias.”
- “No inventes resultados de pruebas.”
- “No incluyas marcas, credenciales, datos personales ni rutas internas.”
- “Propón el cambio mínimo y explica cómo verificarlo.”
