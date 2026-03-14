# Sistema de Biblioteca

## Descripción

Sistema de gestión de biblioteca desarrollado en Java que permite administrar diferentes tipos de materiales bibliográficos (libros, revistas y películas). El sistema incluye funcionalidades para agregar materiales, listarlos y simular préstamos con cálculo automático de multas por retraso.

Este proyecto fue desarrollado como parte de la asignatura **Técnicas de Modelado de Software** para demostrar conceptos de herencia, polimorfismo y diseño orientado a objetos en Java.

## Características Principales

- ✅ **Gestión de tres tipos de materiales**: Libros, Revistas y Películas
- ✅ **Agregar nuevos materiales** a la biblioteca de forma interactiva
- ✅ **Listar materiales** con toda su información detallada
- ✅ **Simular préstamos** y calcular multas por retraso
- ✅ **Multas diferenciadas** según el tipo de material
- ✅ **Menú interactivo** fácil de usar
- ✅ **Validación de entrada** del usuario

## Estructura del Proyecto

```
Sistema de Biblioteca/
├── Main.java                    # Punto de entrada y menú principal
├── Biblioteca.java              # Gestión de la colección de materiales
├── MaterialBibliografico.java   # Clase base abstracta
├── Libro.java                   # Clase para libros
├── Revista.java                 # Clase para revistas
├── Pelicula.java                # Clase para películas
└── README.md                    # Este archivo
```

## Requisitos del Sistema

- **Java**: JDK 8 o superior
- **IDE recomendado**: Visual Studio Code con extensión Extension Pack for Java

## Instalación y Ejecución

### Opción 1: Usando Visual Studio Code

1. Abre el proyecto en VS Code
2. Instala la extensión **Extension Pack for Java** si no la tienes
3. Haz clic en el botón **Run** (▶) en la parte superior derecha al abrir `Main.java`
4. O presiona `F5` para ejecutar en modo debug

### Opción 2: Desde la terminal

```bash
# Compilar
javac *.java

# Ejecutar
java Main
```

## Funcionalidades

### 1. Agregar Material
Permite agregar nuevos materiales a la biblioteca (Libro, Revista o Película) con sus características específicas.

**Parámetros por tipo:**
- **Libro**: Título, Autor, Año, Género, Número de Páginas
- **Revista**: Título, Autor, Año, Periodicidad, Número de Edición
- **Película**: Título, Autor/Productor, Año, Director, Duración (minutos)

### 2. Listar Materiales
Muestra el catálogo completo de la biblioteca con toda la información de cada material, incluyendo días de préstamo permitidos y multa por día de retraso.

### 3. Simular Préstamo y Calcular Multas
Simula el préstamo de uno o todos los materiales e indica la multa a pagar según los días de retraso.

## Detalles de las Clases

### MaterialBibliografico (Clase Base)
Clase abstracta que define los atributos y comportamientos comunes de todos los materiales.

**Atributos:**
- `titulo`: String - Título del material
- `autor`: String - Autor o creador
- `anioPublicacion`: int - Año de publicación

**Métodos principales:**
- `calcularMultas(int diasRetraso)`: Calcula la multa por retraso (implementado en subclases)
- `getDiasPrestamo()`: Retorna los días permitidos de préstamo
- `getMultaPorDia()`: Retorna la tarifa diaria de multa
- `mostrarInformacion()`: Muestra la información del material

### Libro
Extiende `MaterialBibliografico` para representar libros.

**Atributos adicionales:**
- `genero`: String - Género literario
- `numPaginas`: int - Número de páginas

**Política de multas:**
- Días de préstamo: **14 días**
- Multa por día de retraso: **$5.000**

### Revista
Extiende `MaterialBibliografico` para representar revistas.

**Atributos adicionales:**
- `periodicidad`: String - Frecuencia de publicación (Mensual, Semanal, etc.)
- `numEdicion`: int - Número de la edición

**Política de multas:**
- Días de préstamo: **7 días**
- Multa por día de retraso: **$3.000**

### Pelicula
Extiende `MaterialBibliografico` para representar películas.

**Atributos adicionales:**
- `director`: String - Director de la película
- `duracion`: int - Duración en minutos

**Política de multas:**
- Días de préstamo: **3 días**
- Multa por día de retraso: **$10.000**

### Biblioteca
Gestiona la colección de materiales y realiza cálculos de multas.

**Métodos principales:**
- `agregarMaterial(MaterialBibliografico material)`: Agrega un nuevo material
- `listarMateriales()`: Muestra todos los materiales disponibles
- `calcularMultaMaterial(int indice, int diasRetraso)`: Calcula multa de un material específico
- `calcularMultasTodos(int diasRetraso)`: Calcula multas para todos los materiales
- `getCantidadMateriales()`: Retorna la cantidad de materiales

## Ejemplos de Uso

### Menú Principal
```
=== MENU PRINCIPAL ===
1. Agregar Material
2. Listar Materiales
3. Simular prestamo y calcular multas
4. Salir
=====================
Selecciona una opción: _
```

### Agregar un Libro
```
=== AGREGAR MATERIAL ===
Tipo de material:
1. Libro
2. Revista
3. Película
Selecciona tipo: 1
Título: El Quijote
Autor: Miguel de Cervantes
Año de Publicación: 1605
Género: Novela
Número de Páginas: 863
Material agregado exitosamente.
```

### Ver Catálogo
```
=== CATÁLOGO DE LA BIBLIOTECA ===

--- Material 1 ---
Título: El Quijote
Autor: Miguel de Cervantes
Año de Publicación: 1605
Género: Novela
Número de Páginas: 863
Días de préstamo: 14
Multa por día de retraso: $5000
```

### Calcular Multa por Retraso
```
=== SIMULAR PRÉSTAMO ===
[Lista de materiales]
Selecciona el número del material (0 para todos): 1
Días de retraso: 5

--- CÁLCULO DE MULTA ---
Material: El Quijote
Días de préstamo permitidos: 14
Días de retraso: 5
Multa por día de retraso: $5000
Multa total: $25000
```

## Cálculo de Multas

El sistema aplica una fórmula simple de cálculo de multas:

$$\text{Multa Total} = \text{Multa por Día} \times \text{Días de Retraso}$$

**Ejemplos:**
- Libro con 10 días de retraso: $5.000 × 10 = $50.000
- Revista con 3 días de retraso: $3.000 × 3 = $9.000
- Película con 7 días de retraso: $10.000 × 7 = $70.000

## Materiales Preinstalados

Al iniciar el sistema, se cargan automáticamente los siguientes materiales:

1. **El Quijote** - Miguel de Cervantes (Libro)
2. **Cien años de soledad** - Gabriel García Márquez (Libro)
3. **National Geographic** - Varios autores (Revista)
4. **Muy Interesante** - Varios autores (Revista)
5. **Inception** - Christopher Nolan (Película)
6. **Nosferatu** - F.W. Murnau (Película)

## Validación de Entrada

El sistema incluye manejo de errores para:
- Entradas no numéricas cuando se esperan números
- Opciones de menú fuera del rango válido
- Índices de materiales inválidos
- Valores negativos o inválidos en registros de materiales

## Conceptos de Programación Orientada a Objetos Utilizados

- **Herencia**: Las clases Libro, Revista y Película heredan de MaterialBibliografico
- **Polimorfismo**: Cada subclase implementa `calcularMultas()` de forma diferente
- **Encapsulación**: Uso de atributos privados y métodos getters públicos
- **Abstracción**: La clase base define el contrato que todas las subclases deben cumplir

## Notas de Desarrollo

- El proyecto utiliza `ArrayList` para almacenar los materiales
- Se implementa `Scanner` para la entrada interactiva del usuario
- Se usa formato de salida con `String.format()` para alinear valores monetarios
- La gestión de excepciones se centra en `InputMismatchException`

## Posibles Mejoras Futuras

- 📌 Persistencia de datos (guardar en archivo o base de datos)
- 📌 Búsqueda y filtrado de materiales
- 📌 Sistema de usuarios y préstamos reales
- 📌 Historial de préstamos y multas pagadas
- 📌 Interfaz gráfica (GUI con Swing o JavaFX)
- 📌 Export de reportes en PDF

## Licencia

Proyecto educativo desarrollado como parte de la asignatura de Técnicas de Modelado de Software.

## Autor

Desarrollo académico - Tecnología en Desarrollo de Software

---

**Versión**: 1.0  
**Última actualización**: Marzo 2026
