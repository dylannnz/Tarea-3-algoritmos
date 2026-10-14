# Tarea 3 - Algoritmos

Aplicaciones de escritorio en **Java (Swing)** que practican operaciones básicas, interfaces gráficas, arreglos unidimensionales, manejo de archivos de texto, POO y colecciones dinámicas (`ArrayList`).

**Autor:** Dylan (`dygrz`) · Octubre 2026
**Entorno:** Apache NetBeans · Maven · paquete `umg.tarea3`

---

## 📁 Estructura del proyecto

```
Tarea-3-algoritmos/
├── README.md
└── tarea3/                          ← proyecto Maven (abrir ESTA carpeta en NetBeans)
    ├── pom.xml
    ├── temp/                        ← carpeta temporal de lectura/escritura de archivos
    │   ├── Dylan_reporte_notas.txt      (Ejercicio 1)
    │   ├── Dylan_manifiesto.txt         (Ejercicio 2)
    │   ├── Dylan_temperaturas.txt       (Ejercicio 3)
    │   └── Dylan_discos.csv             (Ejercicio 4)
    └── src/main/java/umg/tarea3/
        ├── Sistema_de_Registro.java / .form       (Ejercicio 1)
        ├── Manifiesto_pasajeros.java / .form      (Ejercicio 2)
        ├── Analizador_Temperatura.java / .form    (Ejercicio 3)
        ├── Mantenimiento_Datos.java / .form       (Ejercicio 4)
        ├── Fundamentos_de_Objetos.java / .form    (Ejercicio 5)
        ├── Artista.java                           (clase del Ejercicio 5)
        ├── Cancion.java                           (clase del Ejercicio 5)
        ├── Colecciones_dinamicas.java / .form     (Ejercicio 6)
        └── videojuego.java                        (clase del Ejercicio 6)
```

---

## ▶️ Cómo ejecutar

1. Abrir **NetBeans** → **File → Open Project** → seleccionar la carpeta `tarea3`.
2. En **Projects**, desplegar `Source Packages → umg.tarea3`.
3. **Clic derecho sobre el formulario que se quiera probar → Run File** (o `Shift + F6`).

> ⚠️ Cada ejercicio es una ventana independiente con su propio `main`. Se ejecutan **de uno en uno** con *Run File*.
> Los archivos se leen y escriben en `temp/` (ruta relativa a la carpeta `tarea3`). Si no existe, el programa la crea al exportar.

**Desde terminal** (opcional), dentro de la carpeta `tarea3`:

```bash
mvn compile
java -cp target/classes umg.tarea3.Sistema_de_Registro
```

Cambiar `Sistema_de_Registro` por el nombre de la clase que se quiera abrir.

---

## 📚 Guía rápida por ejercicio

### 1️⃣ Sistema de Registro y Estadísticas de Calificaciones
**Clase:** `Sistema_de_Registro`

| Elemento | Nombre |
|---|---|
| Caja de texto de la nota | `txtNota` |
| Botón agregar | `btnAgregar` (Agregar Nota) |
| Botón reporte | `btnGenerar` (Generar Reporte) |
| Arreglo / índice (globales) | `int[] notas = new int[6]` / `int indice` |

**Cómo se usa**
1. Escribir una nota (0 a 100) y presionar **Agregar Nota**. Repetir hasta tener **6 notas**.
2. Presionar **Generar Reporte**.
3. Se crea `temp/Dylan_reporte_notas.txt` con aprobados (nota ≥ 61), reprobados y promedio.

```
Reporte de Notas
Aprobados: 4
Reprobados: 2
Promedio de Notas: 66.00
```

---

### 2️⃣ Manifiesto de Pasajeros de Vuelo
**Clase:** `Manifiesto_pasajeros`

| Elemento | Nombre |
|---|---|
| Caja de texto del nombre | `txtPasajero` |
| Área de texto (lista) | `tamanifiesto` |
| Botón registrar | `btnAgregar` (Registrar Pasajero) |
| Botón exportar | `btnExportar` (Exportar Manifiesto) |
| Arreglo / índice (globales) | `String[] pasajeros = new String[5]` / `int indice` |

**Cómo se usa**
1. Escribir el nombre y presionar **Registrar Pasajero**; aparece numerado en el área de texto. Repetir hasta **5 pasajeros**.
2. Presionar **Exportar Manifiesto**.
3. Se crea `temp/Dylan_manifiesto.txt`:

```
Manifiesto Oficial de Vuelo
1. Juan Perez
2. Maria Lopez
3. Carlos Estrada
4. Ana Morales
5. Luis Santos
```

---

### 3️⃣ Lector y Analizador de Temperaturas
**Clase:** `Analizador_Temperatura`

| Elemento | Nombre |
|---|---|
| Botón cargar | `btnCargar` (Cargar Datos) |
| Botón calcular | `btncalcular` (Calcular estadísticas) |
| Área de resultados | `taReporte` |
| Apoyo para generar el archivo | `txtTemperatura`, `btnAgregar`, `btnExportar` |
| Globales | `double[] temperaturas = new double[6]`, `int indice`, `String ruta = "temp/Dylan_temperaturas.txt"` |

**Cómo se usa**
1. El archivo `temp/Dylan_temperaturas.txt` debe tener **6 números, uno por línea** (sin numerar). Se puede generar con los botones de apoyo (**Agregar** 6 temperaturas y **Exportar**) o escribirlo a mano.
2. Presionar **Cargar Datos**: lee el archivo línea por línea y avisa con un mensaje que quedó en memoria.
3. Presionar **Calcular estadísticas**: muestra promedio, días cálidos (≥ 25.0°) y días frescos (< 25.0°) en el área de texto.

```
Análisis Climático
------------------
Promedio de Temperatura: 24.5
Días Cálidos (>= 25°): 3
Días Frescos (< 25°): 3
```

---

### 4️⃣ Mantenimiento Completo de Datos (Biblioteca de Discos)
**Clase:** `Mantenimiento_Datos`

| Elemento | Nombre |
|---|---|
| Entrada `Título,Año` | `txtDisco` |
| Botones crear archivo | `btnAgregar` (Agregar disco), `btnExportar` (Exportar Registro) |
| Búsqueda | `txtBuscar`, `btnBuscar`, resultado en `taDisco` |
| Actualización | `txtAnioNuevo`, `btnActualizar` |
| Arreglos paralelos / contador | `String[] titulos`, `int[] anios` (tamaño 5), `int total` |
| Ruta | `temp/Dylan_discos.csv` |

**Cómo se usa**
1. **Primera vez** (sin archivo): escribir cada disco como `Título,Año` (ej. `Thriller,1982`), presionar **Agregar disco** (5 veces) y luego **Exportar Registro** para crear el CSV.
2. **Desde la siguiente vez**, el CSV se lee solo al abrir la ventana (método `cargarDatos()` llamado en el constructor).
3. **Buscar:** escribir el título (sin importar mayúsculas) y presionar **Buscar**; se muestra título y año.
4. **Actualizar:** con el disco escrito en *Buscar disco*, poner el nuevo año y presionar **Actualizar**. Se cambia el arreglo `anios` y se **sobrescribe** el CSV completo con `FileWriter` en modo `false`.

Formato del CSV: una línea por disco, `Título,Año`.

---

### 5️⃣ Fundamentos de Clases y Objetos (Plataforma de Streaming)
**Clase de la ventana:** `Fundamentos_de_Objetos` · **Clases del modelo:** `Artista`, `Cancion`

| Clase | Atributos |
|---|---|
| `Artista` | `nombre` (String), `paisOrigen` (String), `oyentesMensuales` (int) |
| `Cancion` | `titulo` (String), `duracionSegundos` (int), `genero` (String), `nombreArtista` (String) |

| Bloque | Cajas de texto | Botón |
|---|---|---|
| Artista | `txtNombreA`, `txtPaisA`, `txtOyentesA` | `btnCrearArtista` |
| Canción | `txtTituloC`, `txtInterpreteC`, `txtDuracionC`, `txtGeneroC` | `btnCrearCancion` |
| Salida | `taResultados` (un solo `JTextArea`) | |

**Cómo se usa**
1. Llenar los datos del artista y presionar **Crear Artista**: se instancia un objeto `Artista` con `new`, se asignan sus atributos con el operador punto y se imprime en `taResultados` con `.append()`.
2. Llenar los datos de la canción (incluyendo el intérprete) y presionar **Crear Canción**: igual, con un objeto `Cancion`.
3. El área de texto funciona como **bitácora**: cada registro se agrega debajo del anterior sin borrar nada.

---

### 6️⃣ Colecciones Dinámicas de Objetos (Catálogo de Videojuegos)
**Clase de la ventana:** `Colecciones_dinamicas` · **Clase del modelo:** `videojuego`

| Elemento | Nombre |
|---|---|
| Atributos de `videojuego` | `titulo`, `consola`, `anioLanzamiento` (con constructor de 3 parámetros) |
| Lista global | `ArrayList<videojuego> catalogo = new ArrayList<>();` |
| Cajas de texto | `txtTitulo`, `txtConsola`, `txtAnio` |
| Botones | `btnAgregar` (Agregar Juego), `btnMostrar` (Mostrar Catálogo), `btnEliminar` (Eliminar Último) |
| Salida | `taCatalogo` |

**Cómo se usa**
- **Agregar Juego:** captura los tres datos, crea el objeto con el constructor, lo guarda con `.add()` y limpia las cajas.
- **Mostrar Catálogo:** limpia el área, recorre la lista con un `for` usando `.get(i)` y al final muestra el total con `.size()`.
- **Eliminar Último:** si la lista no está vacía, borra el último con `.remove(catalogo.size() - 1)` y avisa con un `JOptionPane`. Al presionar **Mostrar** otra vez se ve que la lista se ajustó sola.

---

## 🧰 Conceptos aplicados

| Tema | Dónde |
|---|---|
| Arreglos unidimensionales + índice | Ejercicios 1, 2, 3 |
| Escritura de archivos (`FileWriter`) | Ejercicios 1, 2, 3, 4 |
| Lectura de archivos (`File`, `Scanner`, `.split(",")`) | Ejercicios 3, 4 |
| Búsqueda secuencial y sobrescritura de archivo | Ejercicio 4 |
| Clases, objetos y operador punto | Ejercicio 5 |
| Constructores y `ArrayList` | Ejercicio 6 |
| Validación con `try/catch` y `JOptionPane` | Todos |

---

## ✍️ Autor

**Dylan (`dygrz`)** · Tarea 3 de Algoritmos · Octubre 2026
Cada ventana muestra "Tarea 3 - Dylan" en su barra de título y los archivos generados llevan el prefijo `Dylan_`.
