# 02. Distancia y Ángulo en Ensamblajes 📏

Las relaciones de **Distancia** y **Ángulo** dentro del grupo de **Relaciones de Posición Estándar** (*Standard Mates*) permiten definir restricciones espaciales cuantitativas y acotadas entre componentes, estableciendo separaciones fijas o límites de movimiento para simular mecanismos reales.

---

## 🎯 Objetivos del Módulo

- **Controlar la separación entre componentes:** Definir luces, holguras y posiciones relativas fijas mediante valores numéricos.
- **Orientar piezas angularmente:** Establecer inclinaciones precisas entre caras o planos de referencia.
- **Restringir rangos de movimiento:** Utilizar límites dimensionales y angulares para simular la cinemática real sin colisiones.

---

## Tabla de contenido

- [02. Distancia y Ángulo en Ensamblajes 📏](#02-distancia-y-ángulo-en-ensamblajes-)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de contenido](#tabla-de-contenido)
  - [1. Relación de Distancia (Distance Mate)](#1-relación-de-distancia-distance-mate)
  - [2. Relación de Ángulo (Angle Mate)](#2-relación-de-ángulo-angle-mate)
  - [3. Relaciones de Posición Límite (Limit Mates)](#3-relaciones-de-posición-límite-limit-mates)
  - [4. Buenas Prácticas y Criterios de Diseño](#4-buenas-prácticas-y-criterios-de-diseño)
  - [5. Ejemplo Práctico: Limitando la Carrera de un Ensamblaje Deslizante](#5-ejemplo-práctico-limitando-la-carrera-de-un-ensamblaje-deslizante)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Relación de Distancia (Distance Mate)

La relación de **Distancia** fija un valor dimensional específico ($d$) entre dos entidades geométricas paralelas (caras, planos, aristas o vértices).

- **Entre caras planas paralelas:** Mantiene una separación constante $d$, eliminando un grado de libertad de translación perpendicular a las caras.
- **Inversión de dimensión (*Flip Dimension*):** Permite cambiar el sentido del desplazamiento para situar el componente a un lado u otro del plano de referencia.
- **Alineación de relación:** Controla la orientación relativa (*Alineado* o *Alineación opuesta*) de las normales de las caras seleccionadas.

---

## 2. Relación de Ángulo (Angle Mate)

La relación de **Ángulo** establece una inclinación angular fija ($\theta$) entre dos caras planas, planos de referencia o aristas lineales.

- **Orientación fija:** Restringe la rotación de un componente a un ángulo determinado respecto a otro elemento rígido.
- **Solución de ángulos complementarios:** Permite seleccionar entre el ángulo agudo, obtuso o complementario ($180^\circ - \theta$) mediante las opciones de alineación.

---

## 3. Relaciones de Posición Límite (Limit Mates)

Ubicadas dentro de las opciones avanzadas, permiten establecer un rango de movimiento cinemático especificando valores máximos y mínimos:

| Tipo de Límite | Parámetros | Aplicación Típica |
| :--- | :--- | :--- |
| **Límite de Distancia** | $d_{\text{máx}}$, $d_{\text{mín}}$, $d_{\text{nominal}}$ | Carreras de cilindros neumáticos, guías lineales, pistones. |
| **Límite de Ángulo** | $\theta_{\text{máx}}$, $\theta_{\text{mín}}$, $\theta_{\text{nominal}}$ | Apertura de puertas, rangos de pivote en brazos articulados. |

---

## 4. Buenas Prácticas y Criterios de Diseño

1. **Utiliza límites para simular movimiento:** En lugar de dejar componentes completamente desaprovechados o fijos en una sola posición, aplica relaciones de límite para verificar el envolvente dimensional en los extremos de la carrera.
2. **Prioriza planos de referencia sobre caras secundarias:** Define las relaciones de ángulo o distancia utilizando los planos principales de los componentes (*Alzado*, *Planta*, *Vista Lateral*) para evitar fallas si las caras geométricas sufren modificaciones.
3. **Evita redundancias dimensionales:** No combines relaciones de distancia o ángulo con restricciones coincidentes en el mismo eje, ya que esto generará un estado sobredefinido (*Over-defined*) en el ensamblaje.

## 5. Ejemplo Práctico: Limitando la Carrera de un Ensamblaje Deslizante

Vamos a configurar un mecanismo compuesto por una guía lineal y un bloque deslizante, utilizando una relación de distancia con límites para simular su carrera máxima y mínima.

### Paso a Paso

1. **Abrir el Ensamblaje Base:**
   - Asegúrate de tener insertados y parcialmente posicionados (con relaciones de concentricidad previas) la guía fija *(Practica27-A)* y el eje cilíndrico *(Practica27-B)*.

2. **Acceder a la Herramienta Relación de Posición:**
   - Haz clic en la herramienta **Relación de posición (Mate)** en la barra superior.

3. **Configurar la Relación de Distancia con Límites:**
   - Selecciona la **cara lateral frontal** del bloque deslizante y la **cara interna del tope** de la guía lineal.
   - En el panel de propiedades izquierdo, despliega la sección de **Relaciones de posición avanzadas (Advanced Mates)** y selecciona **Límite de distancia (Distance Limit)**.
   - Define los siguientes parámetros:
     - **Distancia máxima ($d_{\text{máx}}$):** `30 mm`
     - **Distancia mínima ($d_{\text{mín}}$):** `0 mm`
     - **Distancia nominal (inicial):** `30 mm`
   - Haz clic en la **paloma verde (Aceptar)** para confirmar.

4. **Verificar el Movimiento Cinemático:**
   - Intenta desplazar el bloque deslizante con el ratón. Notarás que su movimiento de translación queda perfectamente restringido y confinado dentro del rango exacto de `0 mm` a `30 mm`, simulando un tope mecánico real.

### Captura / Evidencia

- **Archivos**
  - [Eje Cilíndrico](/06_retos_y_proyectos/01_Practicas/Practica27-B.SLDPRT)
  - [Placa Base](/06_retos_y_proyectos/01_Practicas/Practica27-B.SLDPRT)
  - [Ensamble](/06_retos_y_proyectos/01_Practicas/Practica28_Ensamblaje.SLDASM)
  
<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica28.png" width="500" alt="Captura de pantalla de la práctica">

---

[Inicio](#02-distancia-y-ángulo-en-ensamblajes-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
