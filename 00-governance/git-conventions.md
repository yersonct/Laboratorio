# Convenciones de Git
> Estado: 🟡 En progreso | Última actualización: 2026-06-30
> Autor: Yerson Rubiano | Equipo: Oferta y Programa

Este repositorio usa ramas protegidas, Pull Requests y Conventional Commits para mantener trazabilidad documental.

## Ramas protegidas

`dev`, `qa`, `staging` y `main` representan ramas protegidas y no se trabajan directamente.

| Rama | Propósito | Regla |
|------|-----------|-------|
| `dev` | Integración de trabajo en desarrollo | Recibe PRs desde ramas hijas (`docs/*`, `chore/*`, `fix/*`, `feat/*`) |
| `qa` | Validación funcional y técnica | Recibe PRs únicamente desde `dev` |
| `staging` | Preproducción | Recibe PRs únicamente desde `qa` |
| `main` | Producción / documentación estable | Recibe PRs únicamente desde `staging` o `fix/*` en caso de hotfix |

## Ramas documentales

| Tipo de rama | Cuándo usarla | Ejemplo | Tipo de commit |
|--------------|---------------|---------|----------------|
| `docs` | Crear o actualizar documentación | `docs/update-governance-docs` | `docs` |
| `chore` | Configuración y mantenimiento | `chore/setup-governance` | `chore` |
| `fix` | Corrección de documentación | `fix/documentation-links` | `fix` |
| `feat` | Nueva funcionalidad documental (si aplica) | `feat/service-catalog` | `docs` |

El tipo de rama describe intención. El tipo del commit sigue Conventional Commits.

## Ramas por historia de usuario

## Flujo de ramas

| Caso | Rama origen | Rama destino | Ejemplo |
|------|-------------|--------------|---------|
| Nueva documentación | `docs/*` | `dev` | `docs/update-governance-docs` |
| Configuración del repositorio | `chore/*` | `dev` | `chore/setup-governance` |
| Corrección documental | `fix/*` | `dev` | `fix/documentation-links` |
| Promoción a QA | `dev` | `qa` | Pull Request `dev → qa` |
| Promoción a Staging | `qa` | `staging` | Pull Request `qa → staging` |
| Promoción a Producción | `staging` | `main` | Pull Request `staging → main` |

Las ramas temporales (`docs/*`, `chore/*`, `fix/*` y `feat/*`) siempre se crean desde `dev`. Una vez aprobados los cambios mediante Pull Request, la rama temporal debe eliminarse tanto del repositorio remoto como del entorno local.

---

## Flujo hacia dev

```bash
git checkout dev
git pull origin dev
git checkout -b docs/update-governance-docs

git add .
git commit -m "docs(00-governance): update governance documentation"
git push -u origin docs/update-governance-docs
```

Abrir Pull Request de `docs/update-governance-docs` hacia `dev`.

---

## Flujo hacia qa

Una vez aprobado el Pull Request en `dev`, promover los cambios mediante un nuevo Pull Request:

```text
Origen:  dev
Destino: qa
```

No se crean ramas temporales para esta promoción.

---

## Flujo hacia staging

Una vez validados los cambios en `qa`, promoverlos hacia `staging` mediante Pull Request:

```text
Origen:  qa
Destino: staging
```

---

## Flujo hacia main

Una vez aprobados los cambios en `staging`, promoverlos hacia `main` mediante Pull Request:

```text
Origen:  staging
Destino: main
```

---

## Conventional Commits

Formato obligatorio:

```text
<type>(NN-section): short description in English
```

Tipos permitidos:

| Tipo | Uso |
|------|-----|
| `docs` | Crear o actualizar documentación |
| `fix` | Corregir contenido incorrecto |
| `chore` | Configuración, metadatos, reorganización o renombrado |
| `refactor` | Reestructurar documentación sin cambiar su significado |

No usar `style`, `test`, `perf`, `build` ni `ci` para este repositorio documental.

Ejemplos:

```bash
docs(04-requirements): add scheduling user stories
docs(09-microservices): register offer service
fix(01-context): clarify project scope
chore(00-governance): update repository configuration
refactor(08-uml): reorganize sequence diagrams
```

---

## Reglas de commits

- La descripción del commit debe escribirse en inglés.
- El contenido de los documentos puede escribirse en español.
- Los commits deben ser pequeños, claros y trazables.
- Realizar un commit por cada cambio lógico.
- No mezclar cambios de varias secciones sin una justificación clara.

---

## Hotfix en main

Cuando se detecta un error crítico en `main` que no puede esperar el flujo normal:

| Caso | Rama base | Formato | Ejemplo |
|------|-----------|---------|---------|
| Corrección urgente | `main` | `fix/<descripcion>` | `fix/broken-api-contract` |

Flujo:

```bash
git checkout main
git pull origin main
git checkout -b fix/broken-api-contract

git add .
git commit -m "fix(07-api): correct broken endpoint reference"
git push -u origin fix/broken-api-contract
```

Abrir Pull Request de `fix/broken-api-contract` hacia `main`.

Una vez aprobado el hotfix, sincronizar el cambio hacia las demás ramas protegidas mediante Pull Request o `cherry-pick`, según la estrategia del equipo:

```text
main → staging
staging → qa
qa → dev
```