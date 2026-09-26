# TP2 - Gestión de Eventos Universitarios

**Materia:** Paradigmas de Programación (PP)
**Alumno:** Nicolás Salazar
**Legajo:** 52114

## Descripción

Trabajo Práctico N.º 2 de la materia, que modela un sistema de gestión de eventos universitarios en Java. El TP está organizado en tres ejercicios incrementales, cada uno en su propia carpeta, donde se van incorporando conceptos de programación orientada a objetos: herencia, polimorfismo, interfaces, manejo de excepciones, persistencia de objetos e interfaces genéricas.

## Estructura del repositorio

```
PP_TP2_52114/
├── TP2_Ejercicio1_Eventos/   # Modelo base: herencia y polimorfismo
├── TP2_Ejercicio2_Eventos/   # Se agregan Inscripcion y la interfaz Certificable
└── TP2_Ejercicio3_Eventos/   # Se incorpora generics en EventoUniversitario + nueva actividad (Curso)
```

Cada carpeta es un proyecto Maven independiente, con la misma organización interna:

```
src/main/java/
├── App.java                      # Punto de entrada principal
├── AppAlternativo.java           # Punto de entrada alternativo (lectura de objetos serializados)
├── excepciones/
│   └── CupoExcedidoException.java
└── modelo/
    ├── EventoUniversitario.java
    ├── Estudiante.java
    ├── Sala.java
    ├── Inscripcion.java
    ├── actividades/
    │   ├── Actividad.java         # Clase abstracta
    │   ├── Charla.java
    │   ├── Taller.java
    │   └── Curso.java             # Solo en Ejercicio 3
    └── certificacion/
        └── Certificable.java      # Interface (Ejercicios 2 y 3)
```

## Ejercicios

### Ejercicio 1 — Herencia y polimorfismo
Modelo base del sistema. `Actividad` es una clase abstracta de la que heredan `Charla` y `Taller`, cada una con su propia implementación de `getTipo()` y `calcularCostoMateriales()`. Se gestionan inscripciones de estudiantes a actividades, controlando el cupo mediante la excepción personalizada `CupoExcedidoException`.

### Ejercicio 2 — Interfaces y certificación
Se extiende el modelo del Ejercicio 1 incorporando la clase `Inscripcion` como entidad propia y la interfaz `Certificable`, que define el protocolo para emitir constancias a los estudiantes, independientemente de la jerarquía de `Actividad`.

### Ejercicio 3 — Generics
Se incorpora el uso de **generics** dentro de `EventoUniversitario` para administrar sus actividades, y se suma un tercer tipo de actividad, `Curso`, además de `Charla` y `Taller`.

## Tecnologías

- **Java 17**
- **Maven** (gestión de dependencias y build)
- Serialización de objetos (`Serializable`) para persistir eventos en archivos `.dat`

## Cómo ejecutar

Desde la carpeta de cada ejercicio (por ejemplo `TP2_Ejercicio1_Eventos`):

```bash
mvn compile
mvn exec:java
```

Esto ejecuta `App.java`, que crea los objetos del modelo, registra inscripciones y persiste los datos. También existe `AppAlternativo.java`, que permite leer y mostrar los eventos previamente serializados en los archivos `.dat`.
