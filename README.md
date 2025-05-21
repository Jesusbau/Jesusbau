erDiagram
    ALUMNO {
        VARCHAR(10) matricula PK "Matrícula del alumno"
        VARCHAR(100) nombre "Nombre completo"
        VARCHAR(255) direccion "Dirección"
        VARCHAR(15) telefono "Teléfono"
        VARCHAR(255) contacto_emergencia "Contacto de emergencia"
        DATE fecha_inscripcion "Fecha de inscripción"
    }

    GRUPO {
        INT id_grupo PK "ID del grupo"
        VARCHAR(50) nombre_grupo "Nombre del grupo"
    }

    CLASE {
        INT id_clase PK "ID de la clase"
        VARCHAR(100) nombre_clase "Nombre de la clase"
        VARCHAR(50) horario "Horario"
    }

    MAESTRO {
        VARCHAR(10) rfc PK "RFC del maestro"
        VARCHAR(100) nombre "Nombre completo"
        VARCHAR(15) telefono "Teléfono"
        VARCHAR(255) email "Email"
    }

    INSCRIPCION {
        VARCHAR(10) matricula_alumno FK "Matrícula del alumno"
        INT id_grupo FK "ID del grupo"
        DATE fecha_inscripcion_grupo "Fecha de inscripción al grupo"
        PK (matricula_alumno, id_grupo)
    }

    ASIGNACION_CLASE {
        INT id_clase FK "ID de la clase"
        INT id_grupo FK "ID del grupo"
        VARCHAR(10) rfc_maestro FK "RFC del maestro"
        PK (id_clase, id_grupo)
    }

    ALUMNO ||--o{ INSCRIPCION : "inscribe"
    GRUPO ||--o{ INSCRIPCION : "tiene"
    GRUPO ||--o{ ASIGNACION_CLASE : "imparte"
    CLASE ||--o{ ASIGNACION_CLASE : "es parte de"
    MAESTRO ||--o{ ASIGNACION_CLASE : "asigna a"
