# Documentación de microservicios

> Estado: 🟡 En progreso | Última actualización: 2026-06-30
> Autor: Yerson Rubiano | Equipo: Oferta y Programa

Este documento define las reglas para registrar, documentar y mantener los microservicios del proyecto.

## Regla crítica

No crear carpetas en `09-microservices/services/` hasta que el microservicio exista en el repositorio de código o su creación haya sido aprobada formalmente por el equipo de arquitectura.

No crear microservicios ficticios únicamente para completar la estructura del repositorio.

**Requisito de aprobación:** Todo microservicio nuevo debe contar con una ADR registrada en `05-architecture/decisions/records/` o con una decisión documentada en `15-project-control/open-questions.md` con estado **RESUELTA** antes de crear su carpeta en `09-microservices/services/`. De lo contrario, el Pull Request podrá ser rechazado.

---

## Ubicación

Cada microservicio debe documentarse en:

```text
09-microservices/services/<nombre-del-servicio>/
```

El nombre de la carpeta debe coincidir exactamente con el nombre del repositorio del microservicio.

---

## Flujo

### 1. Verificar el catálogo

Abrir `09-microservices/service-catalog.md` y confirmar que el microservicio no exista previamente.

### 2. Copiar la plantilla

```bash
cp -r 09-microservices/_template/ 09-microservices/services/<nombre-del-servicio>/
```

Ejemplo (solo ilustrativo):

```bash
cp -r 09-microservices/_template/ 09-microservices/services/design-software-offer-program/
```

### 3. Completar el README del microservicio

El archivo `README.md` debe incluir como mínimo:

- Responsabilidad del microservicio.
- Bounded Context.
- Responsable (Owner).
- Repositorio de código.
- Dependencias.
- Enlaces al contrato API.
- Modelo de datos.
- Eventos publicados y consumidos.
- Runbook.

### 4. Registrar el microservicio

Agregar una fila en `09-microservices/service-catalog.md`:

```markdown
| <nombre-servicio> | <descripción> | <owner> | [Repositorio](<url>) | 🟡 |
```

### 5. Completar la documentación mínima

| Archivo | Contenido mínimo |
|---------|------------------|
| `README.md` | Responsabilidad, owner, dependencias y enlaces |
| `api-contract.md` | Endpoints, request, response y códigos de error |
| `data-model.md` | Modelo de datos del microservicio |
| `events.md` | Eventos publicados y consumidos |
| `runbook.md` | Despliegue, rollback, variables y troubleshooting |

Antes del primer merge del código del microservicio hacia `main`, al menos `README.md` y `api-contract.md` deben encontrarse en estado 🟡.

---

## Commits

Utilizar Conventional Commits.

Ejemplo:

```bash
git checkout dev
git pull origin dev
git checkout -b docs/register-offer-program-service

git add 09-microservices/services/<nombre-del-servicio>/
git add 09-microservices/service-catalog.md

git commit -m "docs(09-microservices): register offer program service"

git push -u origin docs/register-offer-program-service
```

Abrir Pull Request hacia `dev`.

Si se documentan varios microservicios, realizar un commit independiente por cada uno cuando sea posible.

---

## Contrato API

- `09-microservices/services/<servicio>/api-contract.md` describe el contrato funcional del microservicio.
- `07-api/contracts/openapi/` almacena las especificaciones OpenAPI oficiales.
- Cuando existan ambos documentos, mantener enlaces entre ellos para facilitar la trazabilidad.