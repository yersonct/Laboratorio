# Seguridad documental

> Estado: 🟡 En progreso | Última actualización: 2026-06-30
> Autor: Yerson Rubiano | Equipo: Oferta y Programa

## Contexto

Este documento establece las reglas para proteger la información del proyecto y prevenir la publicación de datos sensibles dentro del repositorio. Todos los ejemplos, diagramas y documentos deben utilizar información ficticia o anonimizada.

## No publicar

- Credenciales, contraseñas, tokens o llaves privadas.
- Certificados, archivos `.env`, `.pem`, `.key`, `.p12` o `.pfx`.
- Datos personales reales de aprendices, instructores, administradores o usuarios.
- Correos electrónicos reales, teléfonos, números de documento o identificadores personales.
- Capturas de pantalla con sesiones abiertas o información operativa real.
- URLs internas privadas, direcciones IP, nombres de host o rutas de red sensibles.
- Procedimientos que permitan eludir controles de seguridad.

## Usar en ejemplos

| Caso | Valor seguro |
|------|--------------|
| Correo | `usuario@example.com` |
| Token | `TOKEN_DE_EJEMPLO` |
| URL | `https://example.com/api` |
| Servicio | `sena-horarios-service` |
| Documento | `1234567890` (aclarando que es un dato ficticio) |

## Antes de subir capturas

- Verificar que no existan nombres de personas reales.
- Ocultar correos electrónicos, documentos, tokens y sesiones activas.
- Confirmar que la captura aporte valor a la documentación.
- Guardar la imagen en `assets/images/` y referenciarla desde el documento correspondiente.

## Si se detecta una fuga

1. No realizar nuevos commits que contengan el dato sensible.
2. Informar inmediatamente al responsable del repositorio y al equipo de arquitectura o seguridad.
3. Revocar o rotar la credencial comprometida, si aplica.
4. Crear un Pull Request reemplazando la información sensible por un ejemplo seguro.
5. Evaluar la limpieza del historial del repositorio si la información quedó versionada.

## Contacto de seguridad

En caso de detectar una posible exposición de información sensible, contactar al responsable del repositorio y seguir el procedimiento definido por el equipo.

| Rol | Responsable |
|-----|-------------|
| Responsable del repositorio | **Por definir** |
| Equipo de arquitectura | **Por definir** |

> **Nota:** Una vez el instructor o el equipo definan los responsables oficiales, actualizar esta sección con los usuarios o canales correspondientes.

## Checklist

- [ ] No hay credenciales ni tokens.
- [ ] No hay datos personales reales.
- [ ] No hay URLs internas privadas.
- [ ] No hay capturas con sesiones o información real.
- [ ] Todos los ejemplos utilizan datos ficticios.