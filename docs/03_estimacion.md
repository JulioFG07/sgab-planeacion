La siguiente estimación se basa en un análisis preliminar de los requerimientos del Sistema de Gestión Académica Básico (SGAB).

## Suposiciones de la estimación
* Se considera un equipo de desarrollo con conocimientos previos en tecnologías web.

* La infraestructura de base de datos ya está pre-configurada.

* No se incluyen tiempos de despliegue (deployment) ni capacitación a usuarios finales.

## Descomposición Funcional
El sistema se ha dividido en los siguientes módulos principales para su análisis:

1. **Módulo de Autenticación:** Gestión de inicio de sesión y perfiles de usuario.

2. **Gestión de Alumnos y Materias:** Operaciones CRUD (Crear, Leer, Actualizar, Borrar) para la base de datos académica.

3. **Carga de Calificaciones:** Interfaz para que los docentes registren y editen notas.

4. **Generación de Reportes:** Consultas de historial académico y actas.

## Estimación de Esfuerzo
A continuación, se presenta la tabla de esfuerzo estimado en horas/persona (h/p):
| Módulo | Estimación (h/p) | Nivel de Incertidumbre |
| :--- | :--- | :--- |
| Configuración de Base de Datos | 8h | Bajo |
| Módulo de Autenticación | 12h | Medio |
| Gestión de Alumnos y Materias | 20h | Bajo |
| Registro de Calificaciones | 15h | Medio |
| Visualización de Reportes | 10h | Alto |
| **Total Estimado** | **65h** | |

## Notas sobre la incertidumbre
El nivel de incertidumbre es **Alto** en el módulo de reportes debido a que los formatos de salida aún no han sido definidos por el cliente. Por el contrario, los módulos de gestión (CRUD) tienen incertidumbre **Baja** por ser funcionalidades estándar en este tipo de sistemas.