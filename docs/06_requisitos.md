En esta fase, se definen las capacidades y comportamientos que el sistema debe cumplir para evitar la improvisación y reducir riesgos durante el desarrollo.

## Requisitos Funcionales (RF):
| RF | Descripción 
| :--- | :--- |
| RF-01 | el sistema debe permitir el registro de nuevos alumnos con nombre, CURP y fecha de nacimiento. |
| RF-02 | El sistema debe permitir la creación, edición y eliminación de materias. |
| RF-03 | El sistema debe permitir a los docentes capturar calificaciones por materia y alumno. |
| RF-04 | El sistema debe permitir la consulta del historial académico completo de un alumno. |
| RF-05 | El sistema debe generar reportes de actas de calificación finales por grupo. |
| RF-06 | El sistema debe permitir la asignación de docentes a materias especificas. |
| RF-07 | El sistema debe permitir gestionar el estado de los alumnos (activo/baja) en el semestre vigente. |
| RF-08 | El sistema debe permitir la gestión de cuentas del usuario y sus permisos. |

## Requisitos No Funcionales (RNF)
| RNF | Requisito Medible y Verificable | Justificación Técnica 
| :--- | :--- | :--- |
| RNF-01 | Requerir usuario y contraseña para todo accesos. | **Seguridad:** Protege datos sensibles y evita accesos no autorizados. |
| RNF-02 | Responder a consultas en menos de 2 segundos. | **Rendimiento:** Garantiza una experiencia de usuario fluida y eficiente. |
| RNF-03 | Control de acceso basado en roles (Admin, Docente, Alumno). | **Seguridad:** Asegura que cada usuario acceda solo a lo que le corresponde. |
| RNF-04 | Validar que las calificaciones estén entre 0 y 10, permitiendo únicamente incrementos de 0.5 | **Integridad:** Evita errores humanos y datos inconsistentes en la base de datos. |
| RNF-05 | Registrar una bitácora de auditoría de cambios en notas. | **Trazabilidad:** Permite identificar quién y cuándo modificó una calificación. |
| RNF-06 | Almacenamiento persistente en base de datos relacional. | **Confiabilidad:** Los datos no se pierden al cerrar el sistema. |
| RNF-07 | Interfaz responsiva para móviles y escritorio. | **Usabilidad:** Facilita el acceso desde diversos dispositivos. |
| RNF-08 | Disponibilidad del sistema del 99% en periodo escolar. | **Calidad:** Asegura que el servicio esté activo cuando se necesita. |
| RNF-09 | Cifrado de datos mediante protocolo HTTPS. | **Seguridad:** Protege información durante el tránsito por la red. |
| RNF-10 | Soporte de hasta 100 usuarios concurrentes. | **Escalabilidad:** El sistema no debe degradarse bajo carga normal. |

## Diseño Conceptual 
```text
    +---------------------------------------+
    |                                       |
    |   +-------------------------------+   |
    |   |      Gestión de Usuarios      |   |
    |   +-------------------------------+   |
    |                   ^                   |
    |                   |                   |
    |   +-------------------------------+   |
    |   |       Registrar Alumnos       | <------- [ Administrativo ]
    |   +-------------------------------+   |           (Actor)
    |                   ^                   |
    |                   |                   |
    |   +-------------------------------+   |
    |   |      Configurar Materias      |   |
    |   +-------------------------------+   |
    |                                       |
    |   +-------------------------------+   |
    |   |    Capturar Calificaciones    | <------- [    Docente     ]
    |   +-------------------------------+   |           (Actor)
    |                                       |
    |   +-------------------------------+   |
    |   |     Consultar Historial       |   |
    |   +-------------------------------+   |
    |                                       |
    +---------------------------------------+
```
## Mapa de módulos
Estructura lógica del sistema SGAB:
* **Módulo de Usuarios:** Gestión de perfiles y permisos.
* **Módulo de Alumnos:** Expedientes e inscripciones.
* **Módulo de Materias:** Catálogo de asignaturas y créditos.
* **Módulo de Calificaciones:** Registro y edición de notas.
* **Módulo de Reportes:** Generación de documentos y estadísticas.