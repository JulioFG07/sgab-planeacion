## Objetivo del sistema
El Sistema de Gestión Académica Básico (SGAB) tiene como objetivo permitir la administración centralizada de la información académica de una institución educativa, facilitando el registro de alumnos, materias, calificaciones y usuarios mediante una plataforma web accesible y segura.

## Usuarios principales

**Administradores:** responsables de gestionar los usuarios del sistema, configurar materias y mantener la integridad de la información.

**Profesores:** encargados de registrar calificaciones y consultar la información académica de los alumnos.

**Alumnos:** pueden visualizar sus calificaciones, materias inscritas y su historial académico.

## Problema que resuelve
Muchas instituciones educativas aún dependen de procesos manuales o sistemas dispersos para gestionar la información académica, lo que puede provocar errores, pérdida de datos y retrasos administrativos.

El SGAB busca reducir estos problemas mediante un sistema digital que mejore la organización, la disponibilidad de la información y la eficiencia operativa.

## Suposiciones iniciales

Para la planeación del proyecto se consideran las siguientes suposiciones:

- El sistema será una aplicación web accesible desde navegadores modernos.
- Los usuarios contarán con conexión a internet.
- La institución tendrá un número moderado de usuarios (menor a 5,000).
- Se utilizará una base de datos relacional para garantizar la integridad de los datos.
- El sistema requerirá autenticación para proteger la información académica.

## Diagrama de contexto

 El siguiente esquema representa las interacciones del SGAB con los actores externos:


       +-----------------------------------------+
       |           ENTIDADES EXTERNAS            |
       +-----------------------------------------+
                ^             ^             ^
                |             |             |
        (Gestiona datos) (Sube notas) (Consulta notas)
                |             |             |
                v             v             v
       +-----------------------------------------+
       |    SISTEMA DE GESTIÓN ACADÉMICA (SGAB)  |
       +-----------------------------------------+