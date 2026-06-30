## Rama destino

- [ ] `dev` — integración de cambios de desarrollo (destino normal para feature/, docs/, chore/ y fix/)
- [ ] `qa` — validación funcional y pruebas de calidad (solo desde `dev`)
- [ ] `staging` — preproducción (solo desde `qa`)
- [ ] `main` — producción (solo desde `staging` o `hotfix/*` aprobado)

---

## Tipo de cambio

- [ ] Nueva documentación
- [ ] Actualización de documentación
- [ ] Configuración del repositorio (`chore`)
- [ ] Corrección menor
- [ ] Reorganización / archivo movido
- [ ] Diagrama o recurso gráfico

---

## Secciones afectadas

<!-- Ejemplo:
00-governance
04-requirements
09-microservices
-->

---

## Definition of Ready

Ver criterios completos en [00-governance/definition-of-ready.md](../00-governance/definition-of-ready.md)

- [ ] Tiene título, estado, fecha y responsable.
- [ ] Explica claramente el propósito.
- [ ] Cumple el alcance definido para la sección.
- [ ] Está enlazado desde el README correspondiente.
- [ ] No contiene información sensible.

---

## Checklist obligatorio

- [ ] El documento tiene estado y fecha de actualización.
- [ ] Está registrado en el README de su sección.
- [ ] Los commits siguen Conventional Commits.
- [ ] Si documenta varios microservicios, cada uno tiene su propio commit.
- [ ] No contiene credenciales ni información sensible.
- [ ] Todos los enlaces funcionan.
- [ ] Los diagramas incluyen archivo editable (.wsd) y exportación (.svg).
- [ ] Si aplica, el ADR fue registrado.
- [ ] Si aplica, el microservicio fue registrado en el catálogo.
- [ ] Se actualizó el CHANGELOG.md cuando corresponde.

---

## Definition of Done

Ver criterios completos en [00-governance/definition-of-done.md](../00-governance/definition-of-done.md)

- [ ] Aprobado por al menos un revisor.
- [ ] El documento queda en estado 🟢 cuando corresponde.
- [ ] Los enlaces funcionan correctamente en la rama destino.

---

## Notas para revisores

<!-- Riesgos, observaciones o información adicional -->