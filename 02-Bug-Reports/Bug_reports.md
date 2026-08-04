# 🐞 Bug Reports

Este documento contiene reportes de defectos simulados elaborados con fines demostrativos para un portfolio de QA Manual. Cada bug está basado en los casos de prueba y requisitos funcionales del proyecto "Sistema de Gestión de Turnos Médicos".

---

# BUG-001

## Información General

| Campo | Valor |
|--------|-------|
| **ID** | BUG-001 |
| **Título** | El sistema permite iniciar sesión con espacios al final del nombre de usuario |
| **Módulo** | Login |
| **Caso de prueba relacionado** | TC-LOGIN-004 |
| **Requisito relacionado** | RF-015 |
| **Prioridad** | Alta |
| **Severidad** | Media |
| **Estado** | Abierto |
| **Versión** | 1.0 |
| **Entorno** | Simulación basada en la documentación funcional |

## Descripción

Al intentar iniciar sesión ingresando un nombre de usuario con espacios en blanco al final, el sistema permite la autenticación en lugar de validar el formato del dato ingresado.

## Precondiciones

- Existe un usuario registrado en el sistema.
- El usuario conoce sus credenciales válidas.

## Pasos para reproducir

1. Acceder a la pantalla de Login.
2. Ingresar un nombre de usuario válido agregando un espacio al final.
3. Ingresar la contraseña correcta.
4. Presionar el botón **Ingresar**.

## Resultado esperado

El sistema debe validar el formato del nombre de usuario antes de autenticar al usuario. Según la especificación, debe rechazar el dato o eliminar automáticamente los espacios en blanco antes de procesar la autenticación.

## Resultado obtenido

El sistema permite iniciar sesión utilizando un nombre de usuario con espacios al final sin realizar ninguna validación.

## Impacto

La validación inconsistente del campo usuario puede generar comportamientos inesperados durante la autenticación y afectar la consistencia de los datos ingresados.

## Evidencia

No disponible. Reporte realizado como simulación para fines de portfolio.

---

# BUG-002

## Información General

| Campo | Valor |
|--------|-------|
| **ID** | BUG-002 |
| **Título** | El sistema permite reservar un turno ya ocupado |
| **Módulo** | Turnos |
| **Caso de prueba relacionado** | TC-TUR-010 |
| **Requisito relacionado** | RF-010 |
| **Prioridad** | Alta |
| **Severidad** | Alta |
| **Estado** | Abierto |
| **Versión** | 1.0 |
| **Entorno** | Simulación basada en la documentación funcional |

## Descripción

El sistema permite registrar una nueva reserva para un turno que ya fue asignado a otro paciente, generando una superposición de turnos.

## Precondiciones

- Existe un médico con disponibilidad configurada.
- Existe un turno previamente reservado para un paciente.
- Existe un segundo paciente registrado.

## Pasos para reproducir

1. Acceder al módulo **Turnos**.
2. Seleccionar un turno que ya se encuentra reservado.
3. Intentar asignarlo a otro paciente.
4. Confirmar la reserva.

## Resultado esperado

El sistema debe impedir la reserva e informar que el turno ya se encuentra ocupado.

## Resultado obtenido

El sistema registra la segunda reserva para el mismo médico, fecha y horario.

## Impacto

Se produce una superposición de turnos, afectando la agenda del profesional y pudiendo generar conflictos en la atención de pacientes.

## Evidencia

No disponible. Reporte realizado como simulación para fines de portfolio.

---

# BUG-003

## Información General

| Campo | Valor |
|--------|-------|
| **ID** | BUG-003 |
| **Título** | El sistema permite registrar un paciente con un correo electrónico en formato inválido |
| **Módulo** | Pacientes |
| **Caso de prueba relacionado** | TC-PAC-010 |
| **Requisito relacionado** | RF-002 |
| **Prioridad** | Media |
| **Severidad** | Media |
| **Estado** | Abierto |
| **Versión** | 1.0 |
| **Entorno** | Simulación basada en la documentación funcional |

## Descripción

El sistema permite registrar un paciente ingresando un correo electrónico con un formato inválido, sin realizar la validación correspondiente.

## Precondiciones

- El usuario inició sesión y posee permisos para gestionar pacientes.

## Pasos para reproducir

1. Acceder al módulo **Pacientes**.
2. Seleccionar **Nuevo Paciente**.
3. Completar todos los campos obligatorios.
4. Ingresar un correo electrónico con formato inválido (ejemplo: `lucasgmail.com`).
5. Presionar **Guardar**.

## Resultado esperado

El sistema debe validar el formato del correo electrónico y mostrar un mensaje indicando que el dato ingresado no es válido, impidiendo el registro del paciente.

## Resultado obtenido

El sistema registra correctamente al paciente a pesar de que el correo electrónico posee un formato inválido.

## Impacto

Se almacenan datos incorrectos en el sistema, lo que puede provocar errores en el envío de notificaciones o comunicaciones con el paciente.

## Evidencia

No disponible. Reporte realizado como simulación para fines de portfolio.

---

# BUG-004

## Información General

| Campo | Valor |
|--------|-------|
| **ID** | BUG-004 |
| **Título** | El sistema permite cancelar un turno con estado "Atendido" |
| **Módulo** | Turnos |
| **Caso de prueba relacionado** | TC-TUR-013 |
| **Requisito relacionado** | RF-014 |
| **Prioridad** | Alta |
| **Severidad** | Alta |
| **Estado** | Abierto |
| **Versión** | 1.0 |
| **Entorno** | Simulación basada en la documentación funcional |

## Descripción

El sistema permite cancelar un turno que ya fue marcado como **Atendido**, incumpliendo la lógica de negocio.

## Precondiciones

- Existe un turno con estado **Atendido**.

## Pasos para reproducir

1. Acceder al módulo **Turnos**.
2. Buscar un turno con estado **Atendido**.
3. Seleccionar la opción **Cancelar**.
4. Confirmar la operación.

## Resultado esperado

El sistema debe impedir la cancelación e informar que un turno atendido no puede ser cancelado.

## Resultado obtenido

El sistema cambia el estado del turno a **Cancelado**.

## Impacto

Se pierde la integridad del historial de atención y se altera el estado real del turno.

## Evidencia

No disponible. Reporte realizado como simulación para fines de portfolio.

---

# BUG-005

## Información General

| Campo | Valor |
|--------|-------|
| **ID** | BUG-005 |
| **Título** | El sistema no muestra un mensaje de confirmación al eliminar un paciente |
| **Módulo** | Pacientes |
| **Caso de prueba relacionado** | TC-PAC-015 |
| **Requisito relacionado** | RF-001 |
| **Prioridad** | Baja |
| **Severidad** | Baja |
| **Estado** | Abierto |
| **Versión** | 1.0 |
| **Entorno** | Simulación basada en la documentación funcional |

## Descripción

Al eliminar un paciente, el sistema realiza la operación correctamente, pero no informa al usuario mediante un mensaje de confirmación.

## Precondiciones

- Debe existir un paciente registrado.

## Pasos para reproducir

1. Acceder al módulo **Pacientes**.
2. Buscar un paciente existente.
3. Seleccionar **Eliminar**.
4. Confirmar la operación.

## Resultado esperado

El sistema elimina el paciente y muestra un mensaje confirmando que la operación fue realizada con éxito.

## Resultado obtenido

El paciente es eliminado, pero no se muestra ningún mensaje de confirmación.

## Impacto

El usuario no recibe retroalimentación sobre la operación realizada, lo que puede generar incertidumbre o provocar acciones repetidas.

## Evidencia

No disponible. Reporte realizado como simulación para fines de portfolio.