# Cómo trabajar en el repositorio del equipo

Este repositorio se usa en parejas. El repositorio central `github-essentials-workshop` es únicamente la plantilla y el ejemplo del instructor.

## Preparación

1. Una persona crea el repositorio del equipo mediante **Use this template**.
2. Invita a su compañero desde **Settings > Collaborators**.
3. Ambos clonan el repositorio del equipo.
4. Crean y publican `dev`.
5. Conservan `main` para el despliegue y `dev` para integrar mejoras.

## Nombres de ramas

Usa:

```text
feature/nombre-apellido-descripcion
```

Ejemplos:

```text
feature/ana-lopez-catalogo
feature/luis-perez-footer
```

Reglas:

- usa minúsculas;
- elimina acentos;
- reemplaza espacios por guiones;
- incluye el nombre de la persona que crea la rama;
- termina con una descripción breve de la mejora.

## Flujo

1. Actualiza `dev`.
2. Crea una rama personal desde `dev`.
3. Pide el código a Copilot.
4. Revisa y prueba el resultado.
5. Crea commits pequeños y descriptivos.
6. Publica la rama.
7. Abre un Pull Request hacia `dev`.
8. Solicita revisión a tu compañero.
9. Responde comentarios y espera validaciones.
10. Integra el Pull Request.

El paso de `dev` a `main` ocurre mediante otro Pull Request y publica el sitio en GitHub Pages.

## Antes de publicar

Comprueba:

- que no haya contraseñas, tokens ni datos personales;
- que no se agreguen JavaScript, npm, frameworks o dependencias;
- que no queden marcadores de conflicto;
- que `proyecto-base/index.html` abra correctamente;
- que el diff sólo contenga el propósito de la rama.

No uses force push ni `git reset --hard` para resolver un bloqueo del taller.
