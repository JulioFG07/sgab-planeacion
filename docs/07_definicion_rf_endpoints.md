# Definición RF → Endpoints

## 1. Módulo de Autenticación (RF-08, RNF-01, RNF-03)

## RF-08: Gestión de cuentas y permisos

### Endpoints

| **Método** | **Endpoint** | **Descripción** |
| :--- | :--- | :--- |
| POST | `/auth/login` | Iniciar sesión |
| POST | `/auth/register` | Crear cuenta (solo Admin) |
| GET | `/users` | Listar usuarios |
| PATCH | `/users/:id/role` | Cambiar rol |
| DELETE | `/users/:id` | Desactivar usuario |


### Reglas de negocio

-   Usuario y contraseña obligatorios\
-   Control de acceso basado en roles (Admin, Docente, Alumno)\
-   Contraseñas cifradas\
-   Eliminación lógica (`status = inactive`)


# 2. Módulo Alumnos (RF-01, RF-04, RF-07)


## RF-01: Registrar alumnos

POST /students

### Request DTO

``` json
{
  "nombre": "Juan Pérez",
  "curp": "PEPJ900101HDFXXX01",
  "fechaNacimiento": "2000-01-01"
}
```

### Reglas

-   CURP única\
-   Campos obligatorios\
-   Status inicial = active

Respuesta: 201 Created


## RF-04: Consultar historial académico

GET /students/:id/history

### Response DTO

``` json
{
  "studentId": 1,
  "materias": [
    {
      "nombre": "Matemáticas I",
      "calificacion": 8.5
    }
  ]
}
```

### Reglas

-   El alumno debe existir\
-   Solo el alumno o el administrador pueden consultar\
-   Si no existe → 404 Not Found


## RF-07: Gestionar estado del alumno

PATCH /students/:id/activate\
PATCH /students/:id/deactivate

### Reglas

-   Eliminación lógica\
-   Solo Admin puede cambiar estado\
-   Respuesta: 200 OK


# 3. Módulo Materias (RF-02, RF-06)


## RF-02: CRUD de materias

| **Método** | **Endpoint** |
| :--- | :--- |
| POST | `/subjects` |
| GET | `/subjects` |
| GET | `/subjects/:id` |
| PATCH | `/subjects/:id` |
| DELETE | `/subjects/:id` |


### Request DTO

``` json
{
  "clave": "MAT101",
  "nombre": "Matemáticas I",
  "semestre": 1
}
```

### Reglas

-   Clave única\
-   Nombre obligatorio\
-   Eliminación lógica recomendada\
-   Semestre numérico y positivo


## RF-06: Asignar docente a materia

PATCH /subjects/:id/assign-teacher

### Request DTO

``` json
{
  "teacherId": 5
}
```

### Reglas

-   El docente debe existir\
-   Solo Admin puede asignar


# 4. Módulo Calificaciones (RF-03, RF-05)


## RF-03: Capturar calificaciones

POST /grades

### Request DTO

``` json
{
  "studentId": 1,
  "subjectId": 2,
  "value": 8.5
}
```

### Reglas

-   value entre 0 y 10\
-   Incrementos únicamente de 0.5\
-   Solo docente asignado puede registrar\
-   Registrar en bitácora de auditoría\
-   Si alumno o materia no existen → 404 Not Found

Respuesta: 201 Created


## RF-05: Generar acta final por grupo

GET /reports/final-grades/:subjectId

### Response DTO

``` json
{
  "subject": "Matemáticas I",
  "grupo": "1A",
  "alumnos": [
    { "nombre": "Juan Pérez", "calificacion": 8.5 }
  ]
}
```

### Reglas

-   Solo Admin o Docente\
-   La materia debe existir\
-   Respuesta: 200 OK


# Trazabilidad RF → Endpoint

| **Requisito** | **Endpoint** |
| :--- | :--- |
| RF-01 | POST `/students` |
| RF-02 | CRUD `/subjects` |
| RF-03 | POST `/grades` |
| RF-04 | GET `/students/:id/history` |
| RF-05 | GET `/reports/final-grades/:subjectId` |
| RF-06 | PATCH `/subjects/:id/assign-teacher` | 
| RF-07 | PATCH `/students/:id/activate` / `deactivate` |
| RF-08 | CRUD `/users` + `/auth/login` |
