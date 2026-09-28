# 01. Saliente y Corte por Barrido ➰

La operación **Barrido (Sweep)** genera o remueve un sólido 3D desplazando un perfil 2D (*sección transversal*) a lo largo de una trayectoria o camino determinado en el espacio.

---

## 🎯 Objetivos del Módulo

- **Modelar geometrías continuas no rectilíneas:** Crear tuberías, resortes, cables, molduras y conductos.
- **Diferenciar entre perfil y trayectoria:** Entender la relación de coincidencia y penetración entre ambos croquis.
- **Controlar la torsión del perfil:** Aplicar reglas de orientación constantes o seguidoras de superficie.

---

## Tabla de contenido

- [01. Saliente y Corte por Barrido ➰](#01-saliente-y-corte-por-barrido-)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de contenido](#tabla-de-contenido)
  - [1. Requisitos Indispensables del Croquis](#1-requisitos-indispensables-del-croquis)
  - [2. Saliente por Barrido (Swept Boss/Base)](#2-saliente-por-barrido-swept-bossbase)
  - [3. Corte por Barrido (Swept Cut)](#3-corte-por-barrido-swept-cut)
  - [4. Opciones de Orientación y Torsión](#4-opciones-de-orientación-y-torsión)
  - [5. Buenas Prácticas y Criterios de Diseño](#5-buenas-prácticas-y-criterios-de-diseño)
  - [2. Ejemplo Práctico: Modelado de un Tubo Curvo (Manguera o Estructura Tubular)](#2-ejemplo-práctico-modelado-de-un-tubo-curvo-manguera-o-estructura-tubular)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Requisitos Indispensables del Croquis

Para ejecutar una operación de barrido se requieren obligatoriamente dos elementos independientes:

1. **Perfil (Profile):** Croquis cerrado que define la sección transversal del sólido (salvo que se use la opción de *Perfil Circular* nativa).
2. **Trayectoria (Path):** Croquis abierto o cerrado (o arista 3D) que marca el camino por donde viajará el perfil.

> [!WARNING]
> **Regla Geométrica:** El plano del perfil debe intersectar con la trayectoria, idealmente mediante una relación geométrica de **Perforar (Pierce)** entre el punto del perfil y la línea de la trayectoria.

---

## 2. Saliente por Barrido (Swept Boss/Base)

Permite construir tubos, barras formadas, resortes o asas a partir de la trayectoria definida.

- **Perfil de croquis:** Permite seleccionar un croquis 2D/3D personalizado.
- **Perfil circular:** Opción rápida que no requiere dibujar el perfil 2D; solo exige seleccionar la trayectoria y especificar el diámetro del tubo sólido o hueco.

---

## 3. Corte por Barrido (Swept Cut)

Sustrae material a lo largo de una trayectoria 3D dentro de un sólido existente.

- **Aplicaciones típicas:** Roscas helicoidales personalizadas, ranuras de lubricación en ejes o canales para pasaje de cables/fluidos.

---

## 4. Opciones de Orientación y Torsión

- **Seguir trayectoria (Follow Path):** El perfil mantiene un ángulo constante respecto a la tangente de la trayectoria a medida que se desplaza.
- **Mantener constante la orientación (Keep Normal Constant):** El perfil permanece paralelo a su plano original durante todo el recorrido.
- **Torsión a lo largo del trayecto (Twist Along Path):** Fuerza al perfil a girar un número determinado de vueltas, grados o radianes conforme avanza (útil para cables trenzados o brocas).

---

## 5. Buenas Prácticas y Criterios de Diseño

1. **Evita radios de curvatura menores al tamaño del perfil:** Si el radio de una curva en la trayectoria es más pequeño que el ancho del perfil, la geometría colapsará e intersecionará consigo misma, causando un error de reconstrucción.
2. **Utiliza Croquis 3D para trayectorias complejas:** Para tuberías o ruteados que cambian en múltiples planos, la herramienta de *Croquis 3D* simplifica la definición del camino.
3. **Relación de Perforar (Pierce):** Acostumbra a vincular el centro del perfil con la línea de trayectoria mediante la relación *Perforar* para garantizar estabilidad paramétrica.

---

## 2. Ejemplo Práctico: Modelado de un Tubo Curvo (Manguera o Estructura Tubular)

Vamos a diseñar una tubería con un cambio de dirección curvo utilizando un perfil circular y una trayectoria tridimensional.

### Paso a Paso

1. **Crear la Trayectoria (Ruta):**
   - Abre un croquis en el plano **Alzado**.
   - Dibuja una línea horizontal y una línea vertical conectadas por un **Redondeo de croquis (Fillet)** en la esquina para evitar ángulos rectos cerrados que el barrido no podría procesar. Cierra el croquis.

2. **Crear el Perfil (Sección Transversal):**
   - Abre un nuevo croquis en un plano que sea **perpendicular** al extremo inicial de tu trayectoria (puedes usar el plano *Planta* si la ruta inició en el alzado, o crear un plano de referencia si es necesario).
   - Dibuja un **círculo** cuyo centro coincida exactamente con el punto final de la trayectoria. Acótalos con un diámetro específico (ej. **Ø 30 mm**). Cierra el croquis.

3. **Ejecutar el Saliente por Barrido:**
   - Ve a la pestaña **Operaciones (Features)** en la barra superior.
   - Haz clic en la herramienta **Saliente/Base barrido**.
   - En el panel de propiedades izquierdo, selecciona el **Círculo** en el cuadro de *Perfil* y la **Línea con curva** en el cuadro de *Trayectoria*.
   - Observa la vista previa amarilla del tubo generado a lo largo del camino.
   - Haz clic en la **paloma verde (Aceptar)** para confirmar.

4. **Probar el Corte por Barrido (Opcional - Canal Interno):**
   - Si quisieras ahuecar el tubo, podrías usar la herramienta de *Vaciado (Shell)* aprendida antes, o bien dibujar una trayectoria helicoidal y usar un *Corte por barrido* para roscar su interior.

---

### Captura / Evidencia

<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica18.png" width="500" alt="Captura de pantalla de la práctica">

---

[Inicio](#01-saliente-y-corte-por-barrido-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
