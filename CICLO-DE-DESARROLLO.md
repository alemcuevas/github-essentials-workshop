# Ciclo de desarrollo usando GitHub

Esta guía explica cómo una idea se convierte en un cambio publicado. Está pensada para personas técnicas y no técnicas que necesitan colaborar, entender el estado del trabajo y tomar decisiones con la misma información.

## El ciclo completo

```text
Necesidad
   ↓
Definición del resultado
   ↓
Rama de trabajo
   ↓
Cambios y commits
   ↓
Push a GitHub
   ↓
Pull Request
   ↓
Revisión y validaciones
   ↓
Integración en dev
   ↓
Validación conjunta
   ↓
Pull Request hacia main
   ↓
Despliegue
   ↓
Producción y retroalimentación
```

El ciclo no termina al escribir código ni al hacer `push`. Un cambio se considera completo cuando fue revisado, validado, integrado, desplegado y comprobado en el ambiente correcto.

## Dos perspectivas del mismo trabajo

| Momento | Para una persona no técnica | Para una persona técnica |
|---|---|---|
| Necesidad | Existe un problema, oportunidad o resultado esperado | Se recibe un requisito que debe convertirse en un cambio verificable |
| Planeación | Se acuerda qué debe cambiar y qué queda fuera | Se identifica alcance, archivos, riesgos y dependencias |
| Rama | El trabajo se separa para no afectar la versión estable | Se crea `feature/nombre-apellido-descripcion` desde `dev` |
| Desarrollo | Se prepara una propuesta de solución | Se modifican archivos y se prueba localmente |
| Commit | Se guarda un avance con una explicación | Se registran cambios seleccionados con un mensaje descriptivo |
| Push | El avance queda disponible para el equipo | Los commits locales se publican en GitHub |
| Pull Request | Se solicita incorporar el cambio | Se compara la rama feature con `dev` |
| Revisión | Otra persona comprueba que el resultado sea correcto | Se revisan diff, semántica, seguridad, calidad y pruebas |
| Validación | Se confirma que el cambio cumple reglas acordadas | GitHub Actions ejecuta checks automáticos |
| Integración | El cambio aprobado se suma al trabajo compartido | El PR se integra en `dev` |
| Liberación | Se autoriza llevar el conjunto aprobado a producción | Se abre un PR de `dev` hacia `main` |
| Despliegue | La nueva versión queda disponible | Un workflow publica `main` en GitHub Pages |
| Seguimiento | Se confirma que el resultado resuelve la necesidad | Se revisa el sitio, los registros y posibles errores |

## 1. Identificar la necesidad

Todo cambio comienza con una razón, no con un archivo.

### Perspectiva no técnica

Describe:

- qué problema existe;
- quién lo experimenta;
- qué resultado debería observarse;
- qué tan urgente es;
- qué no debe cambiar.

Ejemplo:

> Las personas visitantes no identifican rápidamente las categorías. Necesitamos mostrar cinco categorías antes del pie de página sin cambiar la navegación principal.

### Perspectiva técnica

Convierte la necesidad en criterios comprobables:

- existen cinco categorías;
- cada categoría tiene nombre y descripción;
- la sección funciona en pantallas pequeñas;
- sólo se modifican HTML y CSS;
- no se agregan datos sensibles ni dependencias.

## 2. Definir el alcance

El **alcance** establece qué incluye el cambio y dónde termina.

Un cambio pequeño:

- se entiende con rapidez;
- produce un diff corto;
- es más fácil de revisar;
- reduce conflictos;
- puede revertirse con menor riesgo.

Antes de empezar, completa:

```text
Resultado esperado:
Archivos probables:
Validación:
Fuera de alcance:
```

## 3. Actualizar la rama compartida

`dev` representa el trabajo que el equipo está preparando y validando en conjunto.

```powershell
git switch dev
git pull --ff-only
```

### Qué significa

- **No técnico:** comienzas desde la versión más reciente del equipo.
- **Técnico:** actualizas `dev` antes de crear una rama para evitar trabajar sobre una base antigua.

## 4. Crear una rama personal

Cada mejora vive en una rama independiente.

```powershell
git switch -c feature/nombre-apellido-descripcion
```

Ejemplo:

```powershell
git switch -c feature/ana-lopez-categorias
```

### Qué significa

- **No técnico:** la propuesta se prepara sin cambiar todavía la versión compartida.
- **Técnico:** Git crea una línea de historial desde el commit actual de `dev`.

La rama debe incluir:

1. `feature`;
2. nombre y apellido de quien la crea;
3. propósito breve.

## 5. Crear y revisar el cambio

GitHub Copilot puede proponer HTML, CSS, textos, mensajes y explicaciones. La persona sigue siendo responsable de:

- dar contexto suficiente;
- indicar restricciones;
- leer la propuesta;
- comprobar que resuelva la necesidad;
- rechazar contenido innecesario;
- proteger información sensible.

Antes de registrar el cambio:

```powershell
git status
git diff
```

### Qué significa

- **No técnico:** revisas exactamente qué cambió antes de compartirlo.
- **Técnico:** inspeccionas archivos modificados y líneas agregadas o eliminadas.

## 6. Preparar y registrar commits

Primero eliges los archivos:

```powershell
git add proyecto-base/index.html proyecto-base/styles.css
```

Después revisas lo preparado:

```powershell
git diff --staged
```

Finalmente registras el avance:

```powershell
git commit -m "Agrega navegación por categorías"
```

### Qué significa

- **No técnico:** un commit es un punto del historial con una explicación.
- **Técnico:** Git crea un registro inmutable conectado con el commit anterior.

Un buen commit:

- cumple un solo propósito;
- puede explicarse en una frase;
- no incluye archivos accidentales;
- usa un mensaje orientado al resultado.

## 7. Publicar la rama

```powershell
git push -u origin HEAD
```

### Qué significa

- **No técnico:** el equipo ya puede ver la propuesta en GitHub.
- **Técnico:** se publica la rama actual y se configura su relación con la rama remota.

Un `push` no significa:

- que el cambio esté aprobado;
- que esté en `dev`;
- que esté en `main`;
- que ya esté en producción.

## 8. Abrir un Pull Request

El Pull Request presenta la propuesta y reúne toda la evidencia para decidir si puede integrarse.

Debe indicar:

- qué cambia;
- por qué cambia;
- cómo se validó;
- qué riesgos o pendientes existen;
- quién debe revisarlo.

### Qué significa

- **No técnico:** es una solicitud formal para incorporar una propuesta.
- **Técnico:** compara commits y archivos de la rama feature contra la rama base.

Para una mejora normal:

```text
feature/nombre-apellido-descripcion → dev
```

Para publicar:

```text
dev → main
```

## 9. Revisar el cambio

La persona revisora no sólo busca errores de sintaxis. También comprueba:

- que el resultado corresponda con la necesidad;
- que el alcance sea correcto;
- que no desaparezca comportamiento existente;
- que no existan datos sensibles;
- que el código pueda mantenerse;
- que las instrucciones de validación sean reproducibles.

Un comentario útil contiene:

```text
Observación:
Impacto:
Pregunta o ajuste solicitado:
Cómo verificarlo:
```

Ejemplo:

> La nueva tarjeta no tiene texto alternativo. Una persona que usa lector de pantalla no podrá identificar el producto. Agrega una descripción breve y verifica que la imagen tenga el atributo `alt`.

## 10. Esperar validaciones automáticas

Los checks reducen errores repetibles. En este taller, `Validar repositorio` comprueba:

- archivos requeridos;
- alcance HTML y CSS;
- ausencia de JavaScript y npm;
- ausencia de marcadores de conflicto;
- uso de Contoso Retail;
- análisis del HTML;
- enlaces relativos.

### Estados comunes

| Estado | Significado | Acción |
|---|---|---|
| Pending | La validación espera o está ejecutándose | Esperar y abrir el detalle |
| Success | La comprobación terminó correctamente | Continuar con la revisión |
| Failure | Una regla no se cumplió | Leer la primera causa útil y corregir |
| Skipped | El paso no aplicaba o una condición no se cumplió | Revisar la configuración antes de asumir éxito |

No repitas una validación sin leer primero su registro.

## 11. Integrar en dev

Cuando la revisión, aprobación y checks están completos, el Pull Request puede integrarse.

### Qué significa

- **No técnico:** la propuesta se incorpora a la versión de trabajo del equipo.
- **Técnico:** los commits de la rama feature pasan al historial de `dev`.

Después de integrar:

```powershell
git switch dev
git pull --ff-only
```

Todos los integrantes deben actualizar su copia antes de comenzar otra mejora.

## 12. Resolver conflictos

Un conflicto aparece cuando Git no puede decidir cómo combinar cambios.

```text
<<<<<<< HEAD
versión de la rama actual
=======
versión que intenta entrar
>>>>>>> dev
```

Resolver significa:

1. entender ambas intenciones;
2. acordar el resultado correcto;
3. conservar el contenido final;
4. eliminar marcadores;
5. probar;
6. ejecutar `git add`;
7. crear el commit de resolución;
8. publicar nuevamente.

Un conflicto no indica que una persona hizo mal su trabajo. Indica que hace falta una decisión de contenido.

## 13. Promover dev hacia main

Cuando el conjunto de cambios en `dev` está listo, se abre otro Pull Request:

```text
dev → main
```

Este PR responde preguntas de liberación:

- ¿qué cambios incluye?
- ¿todas las validaciones están verdes?
- ¿hay riesgos conocidos?
- ¿es el momento correcto para publicar?
- ¿existe una forma de recuperación?

`main` representa la versión aprobada para producción.

## 14. Desplegar

Después de integrar en `main`, GitHub Actions ejecuta el workflow de Pages.

### Qué significa

- **No técnico:** la versión aprobada se publica en una dirección web.
- **Técnico:** el workflow carga `proyecto-base` y crea un despliegue asociado al commit de `main`.

El merge y el despliegue son eventos distintos. El merge puede terminar correctamente y el despliegue fallar después.

## 15. Verificar producción

El trabajo no termina cuando el workflow aparece en verde.

Comprueba:

- que la URL abre;
- que la versión esperada está visible;
- que navegación, productos y categorías funcionan;
- que el sitio se adapta a una pantalla pequeña;
- que no hay contenido inesperado.

La evidencia puede ser:

- URL publicada;
- identificador del commit;
- ejecución de Actions;
- captura autorizada;
- checklist de prueba.

## 16. Recibir retroalimentación

Después de publicar pueden aparecer:

- nuevas necesidades;
- errores no detectados;
- comentarios de personas usuarias;
- oportunidades de mejora.

Cada nueva necesidad vuelve al inicio del ciclo. No se modifica producción directamente: se crea otra rama y se repite el flujo.

## ¿Dónde está mi cambio?

| Situación | Ubicación |
|---|---|
| Editaste y guardaste | Directorio de trabajo local |
| Ejecutaste `git add` | Staging local |
| Hiciste commit | Historial local |
| Hiciste push | Rama personal en GitHub |
| Abriste un PR | Propuesta en revisión |
| Integraste hacia `dev` | Versión compartida de validación |
| Integraste hacia `main` | Versión aprobada |
| Terminó Pages | Sitio publicado |

## Responsabilidades

### Persona autora

- mantiene pequeño el alcance;
- revisa lo generado por Copilot;
- escribe commits y PR claros;
- responde comentarios;
- corrige validaciones;
- prueba después de integrar.

### Persona revisora

- entiende la necesidad;
- revisa el diff;
- hace comentarios concretos;
- verifica evidencia;
- aprueba sólo cuando se cumplen los criterios.

### Persona propietaria del repositorio

- administra colaboradores;
- configura protecciones;
- activa GitHub Pages;
- evita omitir reglas sin una razón documentada.

### Instructora o mentor

- ayuda a leer evidencia;
- pregunta antes de ejecutar comandos;
- evita tomar el teclado como primera respuesta;
- escala problemas de permisos o infraestructura.

## Reglas que protegen el ciclo

- No trabajar directamente en `main`.
- Crear ramas desde `dev` actualizada.
- Incluir nombre, apellido y propósito en la rama.
- Hacer commits pequeños.
- Revisar el diff antes del commit.
- Nunca subir secretos.
- Solicitar revisión a otra persona.
- Esperar checks verdes.
- Resolver conversaciones.
- Verificar el despliegue.

## Resumen para perfiles no técnicos

GitHub permite responder cinco preguntas:

1. **¿Qué se propone?** Revisa el Pull Request.
2. **¿Quién lo preparó?** Revisa la rama y los commits.
3. **¿Qué cambió?** Revisa el diff.
4. **¿Quién lo validó?** Revisa aprobaciones y checks.
5. **¿Qué está publicado?** Revisa `main`, Actions y la URL del ambiente.

No necesitas escribir código para participar en la definición, revisión del resultado, validación de criterios o decisión de liberación.

## Resumen para perfiles técnicos

```powershell
git switch dev
git pull --ff-only
git switch -c feature/tu-nombre-apellido-descripcion

# Editar y probar

git status
git diff
git add archivo1 archivo2
git diff --staged
git commit -m "Describe el resultado"
git push -u origin HEAD

# Abrir PR feature → dev
# Revisar, esperar checks e integrar

git switch dev
git pull --ff-only

# Abrir PR dev → main
# Verificar el despliegue
```

Consulta [GLOSARIO.md](./GLOSARIO.md) cuando aparezca un término nuevo y [CONTRIBUTING.md](./CONTRIBUTING.md) para las reglas de colaboración.
