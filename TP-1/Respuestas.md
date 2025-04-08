## FUNDAMENTOS, INTEGRIDAD Y CONCURRENCIA
### Ejercicio 1: Reglas de identidad. 
### Dado un modelo de base de datos de una universidad, identificar violaciones posibles a la integridad referencial si se elimina un estudiante con cursos inscritos. ¿Qué mecanismos usarías para evitarlo?

ESTUDIANTE (id_estudiante, nombre, fecha_nacimiento, carrera, dni) <br>
INSCRIPCIONES (id_inscripcion, id_estudiante, id_curso)

Se podria violar la integridad si se elimina un ESTUDIANTE con cursos inscritos porque INSCRIPCIONES apunta a un id_estudiante que ya no existe.

Podriamos evitarlo usando Restricciones, por ejemplo:

    - ON DELETE RESTRICT: No permite eliminar estudiantes si tiene inscripciones asociadas.
    - ON DELETE CASCADE: Si se elimina un estudiante, tambien se elimina las inscripciones asociadas.
    - ON DELETE SET NULL: Si se elimina a un estudiante, INSCRIPCIONES id_estudiante queda en null.

### Ejercicio 2 Implementacion de restricciones:
### Crear una tabla Matriculas con restricciones de clave foránea. Luego, insertar datos que violen la integridad y mostrar el error generado. 