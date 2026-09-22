# 03. Arcos, Redondeo y Chaflanes en Croquis 📐

En esta sección se documenta el uso de herramientas de curvatura de transición y esquinas en el entorno de croquis 2D en SolidWorks, fundamentales para reducir la concentración de esfuerzos mecánicos y definir geometrías continuas.

---

## 🎯 Objetivos del Módulo

- **Dominar la creación de arcos:** Comprender las diferencias técnicas entre *Arco tangente*, *Arco de 3 puntos* y *Arco centro extremos*.
- **Aplicar suavizado de esquinas:** Utilizar redondeos (*Fillets*) y chaflanes (*Chamfers*) en 2D optimizando el tiempo de diseño.
- **Diferenciar 2D vs. 3D:** Entender cuándo conviene aplicar un redondeo dentro del croquis 2D y cuándo es mejor dejarlo para la operación 3D.

---

## Tabla de contenido

- [03. Arcos, Redondeo y Chaflanes en Croquis 📐](#03-arcos-redondeo-y-chaflanes-en-croquis-)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de contenido](#tabla-de-contenido)
  - [1. Tipos de Arcos en Croquis](#1-tipos-de-arcos-en-croquis)
    - [Arco Tangente (Tangent Arc)](#arco-tangente-tangent-arc)
    - [Arco Centro Extremos (Centerpoint Arc)](#arco-centro-extremos-centerpoint-arc)
    - [Arco de 3 Puntos (3-Point Arc)](#arco-de-3-puntos-3-point-arc)
  - [2. Redondeo y Chaflanes de Croquis](#2-redondeo-y-chaflanes-de-croquis)
    - [Redondeo de croquis (Sketch Fillet)](#redondeo-de-croquis-sketch-fillet)
    - [Chaflán de Croquis (Sketch Chamfer)](#chaflán-de-croquis-sketch-chamfer)
  - [3. Buenas Prácticas y Criterios de Diseño](#3-buenas-prácticas-y-criterios-de-diseño)
  - [4. Ejemplo Práctico: Soporte con Extremo Redondeado y Chaflán](#4-ejemplo-práctico-soporte-con-extremo-redondeado-y-chaflán)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Tipos de Arcos en Croquis

Los arcos permiten conectar segmentos planos mediante curvas de radio constante. SolidWorks ofrece 3 herramientas principales:

### Arco Tangente (Tangent Arc)

Crea una curva suave de transición que se conecta automáticamente de forma **tangente** al extremo de una línea o curva existente.

- **Uso ideal:** Palancas, contornos suaves y transiciones orgánicas.

### Arco Centro Extremos (Centerpoint Arc)

Se define colocando primero el centro del radio, luego el punto inicial de la curva y finalmente barriendo el ángulo hasta el punto final.

- **Uso ideal:** Guías radiales, sectores circulares y agujeros rasgados manuales.

### Arco de 3 Puntos (3-Point Arc)

Se traza fijando el punto inicial, el punto final y posteriormente arrastrando el cursor para ajustar el radio y la curvatura del arco.

- **Uso ideal:** Conectar dos elementos que no están alineados sin imponer tangencia inicial obligatoria.

---

## 2. Redondeo y Chaflanes de Croquis

### Redondeo de croquis (Sketch Fillet)

Redondea la esquina formada por la intersección de dos entidades de croquis en un punto común, creando un arco tangente a ambas.

- **Parámetro clave:** Radio del empalme ($R$).
- **Propiedad:** Permite mantener las cotas virtuales de las esquinas o conservar las relaciones geométricas existentes al activar la casilla *Conservar esquinas virtuales*.

### Chaflán de Croquis (Sketch Chamfer)

Corta una esquina con un bisel recto.

- **Modos de definición:**
  - *Ángulo y distancia:* Especifica una longitud y un ángulo de inclinación (ej. $2\text{ mm} \times 45^\circ$).
  - *Distancia - Distancia:* Define las longitudes de corte sobre cada una de las dos líneas (pueden ser iguales o desiguales).

---

## 3. Buenas Prácticas y Criterios de Diseño

1. **¿Redondeo 2D o Redondeo 3D?**
    - *Regla general:* Es mejor aplicar los redondeos mediante la operación 3D (Redondeo / Fillet) al final del modelado. Esto mantiene el croquis 2D simple, limpio y más fácil de editar.
    - *Excepción:* Aplica el empalme en el croquis 2D únicamente cuando sea indispensable para definir la forma básica del contorno antes de extruir o cuando forme parte estructural de un boceto complejo.
2. **Uso del atajo de línea a arco:** Mientras usas la herramienta Línea, puedes regresar el cursor sobre el punto inicial para cambiar automáticamente a la herramienta Arco tangente sin necesidad de seleccionar otra opción en el menú.
3. **Mantenimiento de tangencias:** Asegúrate de que los arcos mantengan el símbolo verde de Tangencia ($\tan$) en sus puntos de unión para evitar cambios bruscos de curvatura que puedan fallar en la extrusión.

---

## 4. Ejemplo Práctico: Soporte con Extremo Redondeado y Chaflán

Vamos a modelar una placa de soporte de **20 mm x 40 mm** que tendrá un extremo superior redondeado con un arco, un chaflán en una esquina inferior y empalmes en las esquinas internas.

### Paso a Paso

1. **Crear la Base Rectangular:**
   - Abre un croquis en el plano **Alzado**.
   - Dibuja un **Rectángulo de esquina** desde el origen (`0,0`) y acótalos a **40 mm de ancho** por **20 mm de alto**.

2. **Añadir el Arco Superior:**
   - Utiliza la herramienta **Arco tangente** en la línea superior del rectángulo, o dibuja un **Arco de 3 puntos** en la parte alta para cerrar la figura convirtiéndola en una placa con cabeza redondeada.
   - Asegúrate de que las uniones entre las líneas verticales y el arco mantengan la relación geométrica de **Tangencia**.

3. **Aplicar Redondeo de croquis (Fillets):**
   - Selecciona la herramienta **Redondeo de croquis** en la barra superior.
   - En el panel de propiedades, configura un radio de **R = 10 mm**.
   - Haz clic en las dos esquinas inferiores del rectángulo para aplicar el redondeo automáticamente. Observa cómo se añade una relación de tangencia en las esquinas.

4. **Aplicar Chaflán de Croquis:**
   - Despliega la flecha debajo de la herramienta de empalme y selecciona **Chaflán de croquis**.
   - Configura la distancia a **5 mm x 45°** (o distancia-distancia de 5 mm).
   - Selecciona el vértice superior derecho (o la esquina que prefieras modificar) para biselarlo.

5. **Acotación Final y Verificación:**
   - Agrega cotas de radio y longitud generales si algún valor quedó pendiente.
   - Comprueba que todas las entidades del croquis se tornen de color **negro**, indicando que está **Completamente Definido**.

### Captura / Evidencia

<img src="/06_retos_y_proyectos/01_Practicas/Practica03.png" width="500">

---

[Inicio](#03-arcos-redondeo-y-chaflanes-en-croquis-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
