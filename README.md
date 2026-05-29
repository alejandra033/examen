# examen

## Arquitectura de pipeline enterprise

Este repositorio contiene una estructura monorepo diseñada para soportar workflows empresariales.

Estructura principal:
- `/frontend`
- `/backend`
- `/infrastructure`
- `/docs`

## Workflows implementados

- `.github/workflows/ci-enterprise.yml`
  - Detecta cambios en frontend, backend e infraestructura.
  - Ejecuta solo los pipelines necesarios.
  - Ignora cambios excluyendo documentación cuando procede.
- `.github/workflows/docs.yml`
  - Ejecuta validación de documentación en cambios a `/docs/**` y archivos Markdown.
- `.github/workflows/reusable/validate.yml`
  - Reusable workflow para validaciones comunes.
- `.github/workflows/reusable/build.yml`
  - Reusable workflow para compilación de componentes modificados.
- `.github/workflows/reusable/test.yml`
  - Reusable workflow para tests de componentes modificados.

## Comportamiento clave

- El pipeline principal se ejecuta solo para cambios de código en frontend, backend e infraestructura.
- Los cambios de documentación puros son manejados por un workflow separado.
- Los requisitos de detección de componentes modificados se implementan con `dorny/paths-filter`.
