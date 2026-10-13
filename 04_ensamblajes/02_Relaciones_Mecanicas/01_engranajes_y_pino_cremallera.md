# 01. Engranajes y Piñón-Cremallera en Ensamblajes ⚙️

Las **Relaciones de Posición Mecánicas** (*Mechanical Mates*) permiten simular la cinemática de transmisión de movimiento entre componentes de un mecanismo sin necesidad de modelar las geometrías de los dientes de forma exacta, optimizando los recursos computacionales del sistema.

---

## 🎯 Objetivos del Módulo

- **Simular movimientos de rotación acoplados:** Relacionar la velocidad angular de dos o más engranajes mediante relaciones proporcionales.
- **Convertir movimiento rotatorio en lineal:** Aplicar el mecanismo de piñón y cremallera para sistemas de desplazamiento horizontal o vertical.
- **Optimizar modelos virtuales:** Evitar el uso de geometrías de dientes pesadas utilizando relaciones mecánicas idealizadas.

---

## Tabla de contenido

- [01. Engranajes y Piñón-Cremallera en Ensamblajes ⚙️](#01-engranajes-y-piñón-cremallera-en-ensamblajes-️)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de contenido](#tabla-de-contenido)
  - [1. Relación de Posición de Engranaje (Gear Mate)](#1-relación-de-posición-de-engranaje-gear-mate)
    - [Relación de Transmisión (Ratio)](#relación-de-transmisión-ratio)
  - [2. Relación de Posición Piñón-Cremallera (Rack and Pinion Mate)](#2-relación-de-posición-piñón-cremallera-rack-and-pinion-mate)
  - [3. Consideraciones Cinemáticas y Restricciones Previas](#3-consideraciones-cinemáticas-y-restricciones-previas)
  - [4. Buenas Prácticas y Criterios de Diseño](#4-buenas-prácticas-y-criterios-de-diseño)
  - [5. Ejemplo Práctico: Configurando un Mecanismo de Transmisión](#5-ejemplo-práctico-configurando-un-mecanismo-de-transmisión)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Relación de Posición de Engranaje (Gear Mate)

La relación de **Engranaje** vincula la rotación de un componente alrededor de un eje con la rotación de otro componente alrededor de su respectivo eje.

- **Entidades de selección:** Se seleccionan caras cilíndricas, ejes de revolución, aristas circulares o planos congruentes de los dos componentes en rotación.
- **Comportamiento cinemático:** Al girar un engranaje de forma manual, el segundo componente gira de manera sincronizada respetando la proporción establecida.

### Relación de Transmisión (Ratio)

La relación matemática entre las velocidades de giro se define mediante el cociente de sus diámetros primitivos o número de dientes ($N_1 / N_2$):

- **Inversión de giro (*Reverse*):** Permite cambiar el sentido de rotación relativo entre ambos elementos (engranajes exteriores vs. engranajes interiores/exteriores).

---

## 2. Relación de Posición Piñón-Cremallera (Rack and Pinion Mate)

La relación de **Piñón-Cremallera** convierte un movimiento de rotación (del piñón) en un movimiento de translación rectilínea (de la cremallera), o viceversa.

- **Entidades de selección:**
  - *Piñón:* Una cara cilíndrica, eje o arista circular.
  - *Cremallera:* Una arista lineal o trayectoria recta a lo largo del desplazamiento del componente.
- **Parámetro de desplazamiento:** Se define mediante el **paso de cremallera** (*Rack travel per revolution*), que corresponde a la distancia lineal que avanza la cremallera por cada vuelta completa del piñón, calculada típicamente como $\pi \times \text{diámetro primitivo}$.

---

## 3. Consideraciones Cinemáticas y Restricciones Previas

Para que las relaciones mecánicas funcionen correctamente dentro del ensamblaje, se deben cumplir ciertos requisitos previos:

1. **Restricción de ejes:** Los engranajes y piñones deben estar previamente posicionados mediante relaciones de **Concentricidad** y **Coincidencia** lateral para mantener sus ejes fijos y paralelos.
2. **Grados de libertad activos:** El componente accionado debe conservar libre el grado de libertad correspondiente (rotación axial o translación lineal) para permitir el movimiento impulsado por la relación mecánica.

---

## 4. Buenas Prácticas y Criterios de Diseño

1. **Alineación visual de dientes:** Utiliza la opción de inversión de giro o rota manualmente los componentes antes de fijar la relación de engranaje para que los dientes encajen visualmente sin solaparse.
2. **Evita sobrecargar el ensamblaje:** No utilices geometrías de dientes de engranaje reales a menos que sea estrictamente necesario para análisis de elementos finitos (FEA); los cilindros lisos con relaciones de engranaje reducen drásticamente el consumo de memoria RAM.
3. **Combina con límites:** Utiliza relaciones de posición de distancia límite en la cremallera para evitar que el mecanismo sobrepase el recorrido físico modelado en el bastidor.

---

## 5. Ejemplo Práctico: Configurando un Mecanismo de Transmisión

Vamos a ensamblar un piñón giratorio acoplado a una barra con cremallera lineal para simular un mecanismo de avance controlado.

### Paso a Paso

1. **Alinear los Componentes Base:**
   - Asegúrate de que el piñón y la cremallera estén posicionados previamente en el ensamblaje mediante relaciones estándar (concentricidad en el eje del piñón y coincidencia deslizante en la guía de la cremallera), dejando activos sus grados de libertad correspondientes.

2. **Acceder a las Relaciones Mecánicas:**
   - Haz clic en la herramienta **Relación de posición (Mate)** en la barra superior.
   - En el panel de propiedades izquierdo, despliega la sección de **Relaciones de posición mecánicas (Mechanical Mates)**.

3. **Configurar el Piñón-Cremallera:**
   - Selecciona la **arista lineal o trayectoria** de la cremallera.
   - Selecciona la **cara cilíndrica o eje de revolución** del piñón.
   - Configura el **Paso de cremallera** (`Rack travel per revolution`), que corresponde a la distancia lineal que avanza la cremallera por cada vuelta completa del piñón (calculada típicamente como $\pi \times \text{diámetro primitivo}$).
   - Haz clic en la **paloma verde (Aceptar)** para confirmar.

4. **Verificar el Movimiento Cinemático:**
   - Gira manualmente el piñón con el ratón. Observarás cómo la cremallera se desplaza de manera lineal y sincronizada con exactitud matemática.

### Captura / Evidencia

- **Archivos**
  
<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica30.png" width="500" alt="Captura de pantalla de la práctica">

---

[Inicio](#01-engranajes-y-piñón-cremallera-en-ensamblajes-️)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
