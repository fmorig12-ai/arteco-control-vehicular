# ARTECO - Control Vehicular

## Descripción

Proyecto de infraestructura como código para el sistema de control vehicular ARTECO. Se utiliza Terraform para gestionar recursos de AWS y GitHub Actions para automatizar las ejecuciones.

## Tecnologías utilizadas

- AWS S3
- AWS IAM
- Terraform
- GitHub Actions
- OIDC para la autenticación entre GitHub y AWS

## Infraestructura

Se creó un bucket S3 de prueba mediante Terraform:

`arteco-control-demo-755909808380-48271`

El bucket cuenta con bloqueo de acceso público, cifrado del lado del servidor y control de versiones.

El estado de Terraform se almacena por separado en el bucket:

`arteco-tfstate-2026-48271`

Este último bucket debe conservarse durante las pruebas de despliegue y destrucción.

## Automatización

El workflow `ARTECO Terraform Apply Destroy` permite ejecutar operaciones manuales desde GitHub Actions.

1. Autenticación en AWS mediante OIDC.
2. Inicialización y validación de Terraform.
3. Planificación y despliegue mediante `apply`.
4. Eliminación de los recursos administrados mediante `destroy`.

## Ejecución

1. Entrar en la pestaña **Actions** del repositorio.
2. Seleccionar `ARTECO Terraform Apply Destroy`.
3. Pulsar **Run workflow**.
4. Seleccionar la operación `apply` o `destroy`.
5. Revisar los registros de ejecución y el resultado final.

## Arquitectura propuesta

El diseño funcional contempla procesamiento de placas, consulta de autorizaciones, registro de eventos y gestión de alertas. Los componentes adicionales de AWS deben verificarse en la infraestructura antes de considerarse desplegados.

## Evidencias

Las ejecuciones de GitHub Actions y la consola de AWS permiten verificar el despliegue, los recursos creados y la destrucción de los recursos de prueba.
