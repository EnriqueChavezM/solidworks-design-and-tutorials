# 01. Saliente y Corte por Revolución 🔄

Las operaciones por revolución permiten generar o remover volumen tridimensional girando un perfil 2D alrededor de un eje central de rotación. Son fundamentales para el diseño de piezas cilíndricas, simétricas o cónicas como ejes, poleas, bujes y botellas.

---

## 🎯 Objetivos del Módulo

- Comprender el principio de generación geométrica por rotación axial.
- Diferenciar adecuadamente entre la adición (saliente) y la sustracción (corte) por revolución.
- Manejar acotaciones de diámetro directamente en el croquis 2D respecto al eje de simetría.

---

## Tabla de Contenidos

- [01. Saliente y Corte por Revolución 🔄](#01-saliente-y-corte-por-revolución-)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de Contenidos](#tabla-de-contenidos)
  - [1. Requisitos Indispensables del Croquis](#1-requisitos-indispensables-del-croquis)
  - [2. Saliente de Revolución (Revolved Boss/Base)](#2-saliente-de-revolución-revolved-bossbase)
  - [3. Corte por Revolución (Revolved Cut)](#3-corte-por-revolución-revolved-cut)
  - [4. Parámetros de la Operación](#4-parámetros-de-la-operación)
  - [💡 Buenas Prácticas y Criterios de Diseño](#-buenas-prácticas-y-criterios-de-diseño)
  - [2. Ejemplo Práctico: Modelado de una Polea o Eje Escalonado](#2-ejemplo-práctico-modelado-de-una-polea-o-eje-escalonado)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Requisitos Indispensables del Croquis

Para ejecutar una operación por revolución exitosa sin errores de geometría, el croquis debe cumplir con:

1. **Eje de Revolución (Axis of Revolution):** Se requiere una línea constructiva (*Centerline*) o una arista recta que sirva como pivote central de rotación.
2. **Ubicación del Perfil:** El perfil 2D debe encontrarse completamente a **un solo lado** del eje de revolución. Cruzar el eje genera una geometría auto-intersectada inválida.
3. **Perfil Cerrado:** Para sólidos masivos el contorno debe estar cerrado. Si el perfil es abierto, la herramienta requerirá activar la opción de *Operación Lámina / Thin Feature*.

---

## 2. Saliente de Revolución (Revolved Boss/Base)

Genera un volumen sólido continuo al hacer girar la sección transversal trazada alrededor del eje seleccionado.

- **Tipos de Revolución:**
  - **Hasta un ángulo (Una dirección / Dos direcciones):** Define un valor angular explícito (ej. $180^\circ$, $270^\circ$ o $360^\circ$).
  - **Plano Medio:** Distribuye el ángulo de rotación de forma equitativa a ambos lados del plano del croquis.
  - **Hasta la superficie / Hasta el vértice:** Extiende la revolución hasta tocar una cara o referencia existente.

---

## 3. Corte por Revolución (Revolved Cut)

Sustrae material de un sólido tridimensional previo girando un perfil 2D alrededor de un eje.

- **Aplicaciones habituales:**
  - Creación de ranuras circulares u orificios para tóricos (*O-rings*).
  - Chaflanes o biseles cilíndricos en extremos de ejes.
  - Aliviaderos de tensión, gargantas de desahogo de rosca o cavidades internas cónicas.
- **Invertir lado a cortar (*Flip side to cut*):** Permite conservar el interior del contorno y remover la masa exterior de la pieza sólida.

---

## 4. Parámetros de la Operación

| Parámetro | Función |
| :--- | :--- |
| **Eje de Revolución** | Especifica la línea de centro o arista sobre la cual girará el croquis. |
| **Ángulo ($\theta$)** | Grados de rotación de la operación (por defecto $360^\circ$ para sólidos completos). |
| **Operación Lámina (*Thin Feature*)** | Añade un espesor constante a perfiles abiertos o cerrados sin necesidad de acotar doble pared. |
| **Fusión de resultados (*Merge result*)** | Determina si el nuevo sólido revolucionado se une a un cuerpo existente o permanece como un cuerpo independiente (*Multicuerpo*). |

---

## 💡 Buenas Prácticas y Criterios de Diseño

1. **Regla de oro para acotado:** Al acotar líneas paralelas al eje de revolución, arrastra el puntero de la cota hacia el lado opuesto del eje de simetría para colocar **Cotas de Diámetro** en lugar de cotas radiales. Esto coincide con los planos de taller para torneado.
2. **Líneas de centro explícitas:** Dibuja el eje de revolución como *Línea constructiva* para evitar que el software confunda el eje con el perfil sólido de la pieza.
3. **Eficiencia en el árbol:** Siempre que una pieza sea completamente cilíndrica o tenga simetría axial, genera la geometría base en una sola **Saliente por Revolución** en lugar de acumular múltiples extrusiones cilíndricas independientes.

---

## 2. Ejemplo Práctico: Modelado de una Polea o Eje Escalonado

Vamos a diseñar una pieza simétrica circular utilizando la mitad de su perfil transversal y revolucionándolo 360 grados.

### Paso a Paso

1. **Preparar el Croquis Transversal:**
   - Abre un croquis en el plano **Alzado**.
   - Dibuja una **Línea constructiva (Centerline)** que pase exactamente por el **Origen (`0,0`)**. Esta será nuestro eje de giro.
   - Dibuja la mitad del perfil de la pieza (por ejemplo, el perfil escalonado de un eje o una polea) utilizando líneas normales, asegurándote de que el croquis quede completamente cerrado y acotado solo en radio (la mitad de la medida real del diámetro).

2. **Aplicar Saliente por Revolución:**
   - Ve a la pestaña **Operaciones (Features)** en la barra superior.
   - Haz clic en **Revolución de saliente/base**.
   - Si trazaste una línea constructiva clara, SOLIDWORKS la detectará automáticamente como el *Eje de revolución*. Si no, haz clic en la casilla correspondiente y selecciónala manualmente.
   - Asegúrate de que el ángulo esté configurado a **270°**.
   - Haz clic en la **paloma verde (Aceptar)**. Observa cómo el perfil 2D se transforma instantáneamente en un sólido de revolución tridimensional.

3. **Aplicar Corte por Revolución (Opcional - Canaleta de Polea):**
   - Abre un croquis sobre un plano de sección que atraviese el centro de tu pieza (o el plano de origen original).
   - Dibuja un pequeño triángulo o perfil de ranura en la zona exterior.
   - Selecciona **Corte por revolución**, indica la misma línea de eje central y acepta. Se habrá esculpido una ranura circunferencial perfecta alrededor de toda la pieza.

### Captura / Evidencia

<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica13.png" width="500" alt="Captura de pantalla de la práctica">

---

[Inicio](#01-saliente-y-corte-por-revolución-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
