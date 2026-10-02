# 03. Cartelas y Cordones de Soldadura en CAD 📐

En esta sección se documentan las herramientas de refuerzo estructural y representación de uniones en el módulo de **Piezas Soldadas** (*Weldments*): **Cartelas (Gussets)**, **Cordones de Soldadura (Weld Beads)** y la gestión de la **Lista de Cortes (Cut List)** para planos de taller.

---

## 🎯 Objetivos del Módulo

- **Reforzar uniones estructurales:** Colocar platinas de refuerzo entre miembros adyacentes para rigidizar bastidores mecánicos.
- **Documentar uniones soldadas:** Definir cordones de soldadura sólidos o cosméticos con su correspondiente simbología en planos.
- **Automatizar listas de manufactura:** Organizar y cuantificar perfiles, longitudes y accesorios mediante la lista de cortes.

---

## Tabla de contenido

- [03. Cartelas y Cordones de Soldadura en CAD 📐](#03-cartelas-y-cordones-de-soldadura-en-cad-)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de contenido](#tabla-de-contenido)
  - [1. Cartelas de Refuerzo (Gussets)](#1-cartelas-de-refuerzo-gussets)
    - [Parámetros Principales del PropertyManager](#parámetros-principales-del-propertymanager)
  - [2. Cordones de Soldadura (Weld Beads)](#2-cordones-de-soldadura-weld-beads)
    - [Opciones de Definición](#opciones-de-definición)
  - [3. Lista de Cortes de Pieza Soldada (Cut List)](#3-lista-de-cortes-de-pieza-soldada-cut-list)
  - [4. Buenas Prácticas y Criterios de Diseño](#4-buenas-prácticas-y-criterios-de-diseño)
  - [5. Ejemplo Práctico: Reforzando un Marco Estructural con Cartelas](#5-ejemplo-práctico-reforzando-un-marco-estructural-con-cartelas)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Cartelas de Refuerzo (Gussets)

La herramienta **Cartela** añade placas metálicas triangulares o poligonales de refuerzo entre dos caras planas de miembros estructurales que se intersectan.

### Parámetros Principales del PropertyManager

- **Caras de apoyo:** Selección de las dos caras planas adyacentes sobre las que se apoyará la cartela.
- **Perfil de la cartela:**
  - *Triangular:* Definido por dos distancias de cateto ($d_1, d_2$).
  - *Poligonal:* Permite añadir chaflanes o cortes en los extremos para librar cordones de soldadura o esquinas internas.
- **Espesor ($t$):** Define el grosor de la placa de la cartela.
- **Ubicación del espesor:** Centrado respecto a la junta, o desplazado hacia el Lado 1 o Lado 2.
- **Ubicación de la cartela:** Posiciona la cartela en el punto medio de las caras o a una distancia/porcentaje especificado desde el origen de la junta.

---

## 2. Cordones de Soldadura (Weld Beads)

La operación **Cordón de Soldadura** permite aplicar representaciones tridimensionales o símbolos cosméticos de soldadura en las aristas de contacto entre perfiles y placas.

### Opciones de Definición

- **Geometría de soldadura:**
  - *Ruta de soldadura:* Selección de las aristas exactas donde se aplicará el cordón.
  - *Caras de soldadura:* Selección de dos conjuntos de caras; el software calcula automáticamente la línea de intersección.
- **Tamaño del cordón ($s$):** Especifica el ancho o cateto del cordón de soldadura.
- **Símbolo de soldadura:** Incluye automáticamente la anotación bajo norma (ISO / ANSI) con especificaciones de tipo de junta (filete, bisel, V, etc.) para su posterior extracción en planos de taller.

---

## 3. Lista de Cortes de Pieza Soldada (Cut List)

A diferencia de una lista de materiales (BOM) convencional, la **Lista de Cortes** agrupa automáticamente todos los elementos estructurales según su perfil, ángulo de corte e iguales longitudes.

- **Actualización automática:** Al modificar la estructura 3D, haz clic derecho sobre la carpeta *Lista de cortes* y selecciona *Actualizar*.
- **Propiedades de lista de cortes:** Almacena información paramétrica clave como *Descripción*, *Longitud*, *Ángulo1*, *Ángulo2* y *Material*, requerida para el corte en sierra CNC.

---

## 4. Buenas Prácticas y Criterios de Diseño

1. **Prioriza soldadura cosmética en ensamblajes grandes:** Para minimizar el consumo de memoria gráfica en estructuras pesadas, utiliza cordones de soldadura cosméticos en lugar de geometría 3D completa.
2. **Deja holguras en cartelas poligonales:** Utiliza el perfil poligonal con chaflán interno para evitar que la esquina de la cartela interfiera con el radio de curvatura o la raíz de la soldadura entre los tubos.
3. **Mapeo correcto de la lista de cortes:** Asigna el material directamente sobre las propiedades del perfil o de la pieza soldada para que la masa total de la estructura se calcule correctamente en la lista de cortes.

---

## 5. Ejemplo Práctico: Reforzando un Marco Estructural con Cartelas

Vamos a simular la inserción de cartelas de refuerzo en una estructura o soporte metálico para darle rigidez mecánica en sus esquinas de 90°.

### Paso a Paso

1. **Partir de un Armazón Estructural:**
   - Asegúrate de tener una estructura base o una unión en escuadra hecha con perfiles tubulares o placas en el entorno de soldadura.

2. **Acceder a la Herramienta Cartela (Gusset):**
   - Ve a la pestaña **Piezas soldadas (Weldments)** en la barra superior (si no la visualizas, actívala haciendo clic derecho sobre las pestañas de herramientas).
   - Haz clic en la herramienta **Cartela**.
   - En el panel de propiedades izquierdo, selecciona las dos caras planas interiores que forman la esquina de la unión estructural que deseas reforzar.

3. **Configurar los Parámetros de la Cartela:**
   - **Perfil de Cartela:** Elige si la cartela será triangular o poligonal, y define sus dimensiones de lado (por ejemplo, **50 mm x 50 mm** con un espesor de placa de **6 mm**).
   - **Ubicación:** Selecciona si la cartela quedará centrada respecto a la arista, alineada a la izquierda o a la derecha.
   - Haz clic en la **paloma verde (Aceptar)**. Observa cómo se genera el rigidizador triangular cortado y ajustado exactamente al espacio interior de la unión.

4. **Añadir Símbolos de Cordón de Soldadura (Weld Bead):**
   - Haz clic en la flecha de la herramienta **Cordón de soldadura** en la barra de estructuras soldadas.
   - Selecciona las aristas donde se aplicará físicamente la unión.
   - Define el tamaño del cordón de soldadura (ej. **3 mm**). Esta operación añade una representación visual tridimensional y genera datos técnicos listos para los planos de ingeniería.

### Captura / Evidencia

<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica26.png" width="500" alt="Captura de pantalla de la práctica">

---

[Inicio](#03-cartelas-y-cordones-de-soldadura-en-cad-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
