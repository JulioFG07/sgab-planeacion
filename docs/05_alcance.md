Este documento establece los límites funcionales del Sistema de Gestión Académica Básico (SGAB) para asegurar una entrega en los tiempos estimados.

## Funcionalidades Incluidas
* **Gestión de Usuarios:** Registro, edición y baja de alumnos, profesores y administradores.

* **Administración Académica:** Creación de materias y asignación de docentes.

* **Control de Calificaciones:** Módulo para que los docentes ingresen notas y los alumnos las consulten.

* **Seguridad:** Autenticación por medio de usuario y contraseña.

## Funcionalidades Excluidas
* **Pagos:** No se procesarán pagos de colegiaturas o inscripciones.

* **Videoconferencias:** El sistema no incluye herramientas de clases virtuales en vivo.

* **App Móvil Nativa:** El alcance se limita exclusivamente a una plataforma web responsiva.

## Suposiciones
* La institución educativa proporcionará la lista inicial de alumnos y materias en formato digital.

* El servidor de despliegue soporta tecnologías modernas de bases de datos relacionales.

## Ejemplo de Scope Creep
A mitad del desarrollo, el cliente solicita que el sistema envíe notificaciones automáticas por WhatsApp a los padres cada vez que un alumno reprueba.

**Impacto:** Esto requeriría integrar una API externa, aumentar el tiempo de desarrollo en 10 horas adicionales y elevar los costos de mantenimiento, poniendo en riesgo la fecha de entrega original.