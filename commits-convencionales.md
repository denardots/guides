# Guía de Commits Convencionales

Para que nuestro commits tengan un mejor significado y sean mas comprensibles tanto para las máquinas como para las personas, se recomienda utilizar las "_Reglas de Commits Convencionales_".

Estas reglas nos ayudan a mantener un orden y una estructura en nuestros commits, lo que facilita la lectura y comprensión de los mismos. Tal como lo indica su [página oficial](https://www.conventionalcommits.org/en/v1.0.0-beta.4 "Página oficial")

## Estructura de un Commit convencional

```git
  <tipo de cambio> [scope, opcional]: <descripción del cambio>

  [cuerpo del mensaje, opcional]

  [footer(scope específico), opcional]
```

## Scope

El scope va entre () y es opcional, y sirve para especificar el alcance del commit. Hace referencia al paquete afectado. Ejm: ui, backend, frontend, api, etc.

## Tipos de Commits

* `feat`: Nueva funcionalidad
* `fix`: Corrección de bug
* `docs`: Cambios en la documentación
* `refactor`: Refactorización de código
* `test`: Nuevos tests o cambios en los tests existentes
* `drop`: Eliminar una funcionalidad o característica
