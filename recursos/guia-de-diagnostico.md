# Guía de diagnóstico

Usa este orden antes de cambiar algo:

1. Copia el mensaje exacto sin incluir credenciales.
2. Ejecuta `git status`.
3. Ejecuta `git branch --show-current`.
4. Describe qué esperabas.
5. Elige el síntoma de este árbol.

No uses force push ni `reset --hard` como primera respuesta.

## Árbol de decisión rápido

```text
¿Qué falló?
├─ No puedo hacer push
│  ├─ Dice "protected branch" → usa una rama feature y abre un PR
│  └─ Dice "rejected" o "fetch first" → consulta el remoto y actualiza
├─ Git muestra "unmerged paths" → termina o cancela el conflicto
├─ El PR no permite merge
│  ├─ Falta aprobación → solicita revisión
│  ├─ Hay conflicto → actualiza la rama y resuelve
│  └─ Falló un check → abre el registro
├─ No veo mis cambios
│  ├─ Siguen sin commit → revisa status y diff
│  ├─ Commit sólo local → haz push
│  └─ Estoy en otra rama → cambia a la rama correcta
└─ Hice commit en otra rama → detente y clasifica si ya publicaste
```

## Push rechazado porque el remoto avanzó

**Síntoma:** aparece `rejected`, `non-fast-forward` o `fetch first`.

**Causa probable:** GitHub tiene commits que tu rama local todavía no incorpora.

**Cómo verificar:**

```powershell
git status
git branch --show-current
git fetch origin
git log --oneline --all --graph --decorate -10
```

**Cómo resolver:**

1. Confirma que estás en tu rama feature.
2. Integra la rama base reciente con `git merge origin/dev`.
3. Resuelve conflictos si aparecen.
4. Prueba el sitio.
5. Ejecuta `git push`.

No uses `git push --force` para evitar la actualización.

## Push bloqueado por rama protegida

**Síntoma:** GitHub menciona `protected branch`, `repository rule` o que los cambios deben hacerse mediante Pull Request.

**Causa probable:** intentaste publicar directamente en `main` o `dev`.

**Cómo verificar:**

```powershell
git branch --show-current
git status
```

**Cómo resolver si todavía no publicaste el commit:**

```powershell
git switch -c feature/tu-nombre-apellido-descripcion
git push -u origin HEAD
```

Después abre un PR hacia la rama indicada. Si ya publicaste o hay varios commits ajenos, pide apoyo antes de moverlos.

## Conflicto sin resolver

**Síntoma:** `git status` muestra `unmerged paths`, `both modified` o un merge en curso.

**Causa probable:** dos ramas cambiaron la misma zona y Git espera una decisión.

**Cómo verificar:**

```powershell
git status
```

Busca en los archivos indicados:

```text
<<<<<<<
=======
>>>>>>>
```

**Cómo resolver:**

1. Lee ambas versiones.
2. Decide el contenido final con el equipo.
3. Elimina todos los marcadores.
4. Guarda y prueba.
5. Ejecuta `git add archivo`.
6. Confirma con `git status` que no hay rutas sin integrar.
7. Ejecuta `git commit`.

Si no quieres continuar el intento y todavía no registraste la resolución, `git merge --abort` cancela el merge.

## Pull Request bloqueado

**Síntoma:** el botón de merge está deshabilitado.

**Causa probable:** falta una aprobación, existe un conflicto, falló una validación o una regla exige otro destino.

**Cómo verificar:**

1. Lee el mensaje junto al botón de merge.
2. Abre **Reviewers** y confirma aprobaciones.
3. Abre **Checks** y localiza estados fallidos o pendientes.
4. Confirma que la base sea `dev` para una feature.
5. Revisa si GitHub muestra **This branch has conflicts**.

**Cómo resolver:**

- Falta aprobación: solicita revisión a una persona autorizada.
- Hay conflicto: integra `origin/dev` en tu rama, resuelve y publica.
- Falló un check: abre el registro, corrige la primera causa útil y publica el ajuste.
- Base incorrecta: edita el PR y elige la rama indicada.
- Espera de ambiente: contacta a `[AJUSTAR: responsable de aprobación]`.

## Cambios que no aparecen

**Síntoma:** el navegador, GitHub o el PR no muestra tu modificación.

**Causa probable:** archivo sin guardar, cambio sin commit, commit sin push, rama equivocada o navegador sin actualizar.

**Cómo verificar:**

```powershell
git status
git branch --show-current
git log --oneline -5
```

**Cómo resolver:**

1. Guarda el archivo.
2. Actualiza el navegador.
3. Si `status` muestra cambios, revísalos y crea el commit.
4. Si el commit aparece en `log` pero no en GitHub, ejecuta `git push`.
5. Si el PR usa otra rama, publica en la rama correcta del PR.

## Commit en la rama equivocada

**Síntoma:** `git log` muestra tu commit en `main`, `dev` o una feature que no correspondía.

**Causa probable:** no confirmaste la rama antes de hacer commit.

**Cómo verificar:**

```powershell
git branch --show-current
git status
git log --oneline -5
```

**Cómo resolver si es el último commit y no se ha publicado:**

1. Pide a un mentor confirmar que el commit no está en GitHub.
2. Crea una rama desde ese punto:

```powershell
git switch -c feature/tu-nombre-apellido-descripcion
```

3. Publica la nueva rama:

```powershell
git push -u origin HEAD
```

4. Pide al mentor recuperar la rama original sin borrar trabajo.

**Si el commit ya se publicó:** no reescribas el historial compartido. Informa al equipo; la solución puede ser un PR de reversión o mover el cambio con una estrategia acordada.

## Rama equivocada al editar, todavía sin commit

**Síntoma:** `git status` muestra cambios, pero estás en `dev` o `main`.

**Cómo verificar:**

```powershell
git branch --show-current
git status
```

**Cómo resolver:**

```powershell
git switch -c feature/tu-nombre-apellido-descripcion
```

Los cambios del directorio normalmente permanecen al crear la rama. Si Git bloquea el cambio de rama, no fuerces la operación; pide apoyo para guardar el trabajo de forma segura.

## Validación fallida

**Síntoma:** un check aparece en rojo.

**Causa probable:** el contenido no cumple una regla o la infraestructura tuvo un problema.

**Cómo verificar:**

1. Abre el check.
2. Localiza el primer paso fallido.
3. Lee desde la primera línea de error, no sólo la última.
4. Clasifica si menciona tu archivo o `[AJUSTAR: infraestructura]`.

**Cómo resolver:**

- Si señala tu archivo, corrige en la misma rama, prueba, crea commit y push.
- Si señala permisos, servicio no disponible o agente, escala a `[AJUSTAR: equipo responsable]`.
- Si sigue pendiente, confirma si está en cola o espera aprobación; no lo reinicies repetidamente.

## Información útil al pedir ayuda

Comparte:

- comando o clic que ejecutaste;
- salida de `git status`;
- rama actual;
- mensaje exacto sin credenciales;
- resultado esperado.

No compartas:

- contraseñas;
- tokens;
- llaves privadas;
- datos personales;
- direcciones internas que no estén autorizadas.
