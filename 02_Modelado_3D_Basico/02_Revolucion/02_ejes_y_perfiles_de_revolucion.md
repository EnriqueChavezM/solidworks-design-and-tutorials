# 02. Ejes y Perfiles de Revolución en CAD 📐

En el modelado tridimensional por simetría axial, la correcta definición del **Eje de Revolución** y la geometría del **Perfil 2D** determina si la operación se ejecutará con éxito. Este apunte profundiza en las reglas geométricas, las restricciones y las técnicas de acotado radial y diametral.

---

## 🎯 Objetivos del Módulo

- Identificar y aplicar correctamente los diferentes tipos de ejes válidos para operaciones de rotación.
- Dominar el acotado inteligente de diámetros en piezas cilíndricas directamente sobre el croquis.
- Prevenir fallas de reconstrucción por auto-intersección de perfiles o ejes mal definidos.

---

## Tabla de Contenidos

- [02. Ejes y Perfiles de Revolución en CAD 📐](#02-ejes-y-perfiles-de-revolución-en-cad-)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de Contenidos](#tabla-de-contenidos)
  - [1. Tipos de Ejes de Revolución](#1-tipos-de-ejes-de-revolución)
  - [2. Reglas del Perfil de Revolución](#2-reglas-del-perfil-de-revolución)
  - [3. Trazado y Acotado Diametral vs. Radial](#3-trazado-y-acotado-diametral-vs-radial)
    - [Cómo acotar en Diámetro](#cómo-acotar-en-diámetro)
  - [4. Errores Comunes de Geometría](#4-errores-comunes-de-geometría)
  - [Buenas Prácticas de Modelado](#buenas-prácticas-de-modelado)
  - [5. Ejemplo Práctico: Modelado de un Pivote o Casquillo Cónico](#5-ejemplo-práctico-modelado-de-un-pivote-o-casquillo-cónico)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Tipos de Ejes de Revolución

El eje actúa como el pivote central de rotación ($\theta$). Puede ser definido mediante diferentes elementos dentro del entorno de diseño:

| Elemento utilizado como Eje | Validez | Descripción / Aplicación |
| :--- | :--- | :--- |
| **Línea constructiva / Centro (*Centerline*)** | ✅ Recomendado | Elemento de referencia en el croquis actual que no añade geometría al sólido. |
| **Arista recta del sólido** | ✅ Válido | Permite revolucionar un croquis nuevo utilizando el borde de una característica 3D previa. |
| **Eje de referencia 3D (*Axis*)** | ✅ Válido | Eje generado previamente mediante operaciones de geometría de referencia. |
| **Línea de croquis continua** | ⚠️ Precaución | Si se usa una línea sólida como eje, el software intentará incluirla en el contorno del volumen. |

---

## 2. Reglas del Perfil de Revolución

Para que la matriz matemática de rotación calcule el volumen tridimensional, el perfil trazado en el croquis debe cumplir con tres condiciones geométricas fundamentales:

1. **Unilateralidad estricta:** Todo el contorno debe residir en uno de los dos lados del eje. Si el perfil cruza el eje de rotación, la operación fallará por auto-intersección.
2. **Contacto con el eje:** El perfil puede estar **separado del eje** (para crear piezas huecas o tubulares) o **coincidente con el eje** (para sólidos macizos), pero nunca atravesarlo.
3. **Continuidad del contorno:**
   - **Perfil cerrado:** Genera un sólido compacto de volumen completo.
   - **Perfil abierto:** Requiere obligatoriamente activar la *Operación Lámina / Thin Feature* para definir un grosor de pared.

---

## 3. Trazado y Acotado Diametral vs. Radial

Al diseñar componentes cilíndricos (como flechas o poleas), las cotas del plano de fabricación representan **diámetros** y no radios.

### Cómo acotar en Diámetro

1. Selecciona la **Línea constructiva** (eje de simetría).
2. Selecciona la entidad o punto a acotar.
3. Mueve el puntero del mouse hacia el **lado opuesto del eje.** El software cambiará automáticamente la cota radial por una cota diametral antecedida por el símbolo $\varnothing$.

## 4. Errores Comunes de Geometría

- **Geometría en ambos lados del eje:** Tener entidades a la izquierda y derecha del eje de centro en el mismo croquis.
- **Múltiples líneas de centro ambiguas:** Si el croquis contiene más de una línea constructiva, se debe indicar explícitamente en el menú de propiedades cuál servirá como eje de rotación.
- **Esquinas en el eje:** Dejar huecos microscópicos entre los vértices del perfil y la línea de centro cuando se busca un sólido cerrado.

## Buenas Prácticas de Modelado

1. **Regla de oro:** Acota siempre en diámetros cuando trabajes con perfiles de revolución. Esto garantiza que tus dimensiones en el modelo 3D coincidan directamente con las especificaciones de los planos de taller para torneado.
2. **Eje en el origen:** Haz coincidir la línea de centro constructiva con el punto de origen del sistema de coordenadas para asegurar la posición del modelo.
3. **Geometría previa:** Si necesitas realizar una cavidad circular interna, inclúyela directamente en el perfil del croquis de revolución en lugar de agregar un corte extra posteriormente.

---

## 5. Ejemplo Práctico: Modelado de un Pivote o Casquillo Cónico

Vamos a analizar cómo estructurar correctamente un perfil y su eje para modelar una pieza cónica escalonada.

### Paso a Paso

1. **Abrir Croquis y Trazar el Eje:**
   - Abre un croquis en el plano **Alzado**.
   - Dibuja una **Línea constructiva** horizontal que pase exactamente por el **Origen (`0,0`)**. Esta será nuestra línea de referencia de giro.

2. **Dibujar el Perfil Superior (Mitad de la Pieza):**
   - Dibuja el contorno escalonado de la pieza utilizando líneas normales, asegurándote de que la parte inferior de tu perfil toque o se acerque al eje de simetría, pero **sin cruzarlo**.
   - Cierra los extremos abiertos del perfil para asegurar que el área sombreada en gris claro aparezca (indicador de que el contorno está completamente cerrado).

3. **Acotación Diametral Inteligente:**
   - Selecciona la herramienta **Cota Inteligente**.
   - Haz clic en una línea exterior de tu perfil y luego haz clic en la línea constructiva central (eje).
   - Mueve el cursor al otro lado del eje. Observa cómo SOLIDWORKS cambia automáticamente a una **cota de diámetro (Ø)** en lugar de radio, facilitando la lectura industrial de la pieza.

4. **Ejecutar la Revolución:**
   - Ve a **Operaciones > Revolución de saliente/base**.
   - Verifica que el eje seleccionado sea tu línea constructiva y que el ángulo esté en **360°**.
   - Haz clic en la paloma verde para generar el sólido.

### Captura / Evidencia

<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica14.png" width="500" alt="Captura de pantalla de la práctica">

---

[Inicio](#02-ejes-y-perfiles-de-revolución-en-cad-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
