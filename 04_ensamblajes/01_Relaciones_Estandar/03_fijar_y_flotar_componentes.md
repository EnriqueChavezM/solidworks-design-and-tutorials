# 03. Fijar y Flotar Componentes en Ensamblajes ⚓

La gestión del estado de movilidad de los componentes dentro de un entorno de ensamblaje —mediante los estados **Fijo** (*Fixed*) y **Flotante** (*Float*)— constituye la base estructural para construir modelos 3D robustos, estables y bien restringidos.

---

## 🎯 Objetivos del Módulo

- **Establecer el ancla del ensamblaje:** Comprender la importancia del componente base para la referencia espacial de todo el conjunto.
- **Alternar estados de movilidad:** Dominar el cambio entre estados fijo y flotante según las necesidades de modelado.
- **Evitar errores de posición:** Prevenir el desplazamiento accidental de piezas y asegurar la coincidencia con los sistemas de coordenadas globales.

---

## Tabla de contenido

- [03. Fijar y Flotar Componentes en Ensamblajes ⚓](#03-fijar-y-flotar-componentes-en-ensamblajes-)
  - [🎯 Objetivos del Módulo](#-objetivos-del-módulo)
  - [Tabla de contenido](#tabla-de-contenido)
  - [1. Componente Fijo (Fixed Component)](#1-componente-fijo-fixed-component)
  - [2. Componente Flotante (Floating Component)](#2-componente-flotante-floating-component)
  - [3. Fijar respecto al Origen Principal](#3-fijar-respecto-al-origen-principal)
  - [4. Buenas Prácticas y Criterios de Diseño](#4-buenas-prácticas-y-criterios-de-diseño)
  - [2. Ejemplo Práctico: Anclando la Base y Gestionando la Movilidad](#2-ejemplo-práctico-anclando-la-base-y-gestionando-la-movilidad)
    - [Paso a Paso](#paso-a-paso)
    - [Captura / Evidencia](#captura--evidencia)

---

## 1. Componente Fijo (Fixed Component)

Un componente en estado **Fijo** tiene bloqueados sus 6 grados de libertad ($DoF$) respecto al espacio del ensamblaje. No puede trasladarse ni rotarse, sirviendo como estructura base sobre la cual se posicionan los demás elementos.

- **Identificación:** En el árbol del Gestor de Diseño (*FeatureManager*), el componente muestra el prefijo `(f)` antes de su nombre.
- **Comportamiento automático:** Por defecto, el primer componente que se inserta en un ensamblaje se coloca automáticamente en estado fijo en la posición donde se haga clic.
- **Cambio de estado:** Al hacer clic derecho sobre el componente en el área gráfica o en el árbol, se selecciona la opción **Flotar** (*Float*) para liberarlo.

---

## 2. Componente Flotante (Floating Component)

Un componente en estado **Flotante** conserva sus grados de libertad libres hasta que se le apliquen relaciones de posición (*Mates*) que restrinjan su movimiento.

- **Identificación:** En el árbol de diseño, se representa con el prefijo `(-)` antes de su nombre, indicando que está sub-definido (*Under-defined*).
- **Movilidad manual:** Se puede arrastrar libremente mediante clic izquierdo (traslación) o clic derecho (rotación) en el espacio de trabajo.
- **Fijación manual:** Cualquier componente flotante puede fijarse en su posición actual haciendo clic derecho sobre él y seleccionando **Fijar** (*Fix*).

---

## 3. Fijar respecto al Origen Principal

Aunque la opción **Fijar** fija una pieza en el espacio, la mejor práctica de modelado consiste en relacionar explícitamente la pieza base con el origen global.

| Método | Resultado en el Ensamblaje | Recomendación |
| :--- | :--- | :--- |
| **Fijar (*Fix*) simple** | La pieza queda anclada en una posición arbitraria $X,Y,Z$. | Evitar para componentes principales. |
| **Hacer coincidir Orígenes** | El origen de la pieza coincide exactamente con el origen del ensamblaje ($0,0,0$). | **Recomendado:** Garantiza la alineación de planos principales. |

---

## 4. Buenas Prácticas y Criterios de Diseño

1. **Un solo componente fijo base:** Como regla general, únicamente el componente base (bastidor, carcasa o chasis) debe estar fijo o emparejado al origen del ensamblaje. Los demás componentes deben posicionarse mediante relaciones mecánicas o geométricas.
2. **Flotar antes de alinear al origen:** Al insertar la primera pieza, haz clic en el botón de confirmación verde (✔) del PropertyManager en lugar de hacer clic en el área gráfica; esto alineará automáticamente el origen de la pieza con el origen del ensamblaje.
3. **Revisa los prefijos del árbol:** Un ensamblaje completamente definido no debe tener componentes con el prefijo `(-)` ni piezas fijadas arbitrariamente que impidan la simulación kinemática esperada.

---

## 2. Ejemplo Práctico: Anclando la Base y Gestionando la Movilidad

Vamos a configurar un ensamblaje básico asegurando el componente estructural principal al origen y liberando el elemento acoplado para comprobar su movilidad.

### Paso a Paso

1. **Insertar el Componente Base:**
   - Crea un nuevo archivo de **Ensamblaje (.sldasm)** en SOLIDWORKS.
   - Haz clic en **Insertar componentes** y selecciona la pieza soporte base *(Practica27-A)*. En lugar de hacer clic arbitrariamente en el área gráfica, haz clic en el **botón de confirmación verde (Aceptar)** del PropertyManager lateral para que su origen coincida exactamente con el origen global del ensamblaje.
   - Observa la letra `(f)` que aparece automáticamente al lado de su nombre en el árbol de diseño.

2. **Insertar el Componente Móvil:**
   - Vuelve a hacer clic en *Insertar componentes* y añade la segunda pieza *(Practica27-B)*. Por defecto, aparecerá como flotante con el prefijo `(-)` en el árbol.

3. **Cambiar Estados (Prueba de Fijar y Flotar):**
   - Haz clic derecho sobre el componente base en el árbol de diseño y selecciona **Flotar (`Float`)**. Nota cómo la letra `(f)` desaparece y se convierte en `(-)`. Intenta arrastrarlo con el ratón: verás que se mueve libremente por el espacio.
   - Vuelve a hacer clic derecho sobre el componente y selecciona **Fijar (`Fix`)** para devolverle su condición de ancla estable.
   - Haz lo mismo con el componente móvil: haz clic derecho y selecciona **Fijar** para bloquearlo temporalmente, y luego **Flotar** para restaurar su capacidad de movimiento antes de aplicarle relaciones de posición.

4. **Verificación del Comportamiento:**
   - Asegúrate de que únicamente el componente base se mantenga fijo y que los elementos móviles conserven su libertad de movimiento a la espera de sus *mates*.

### Captura / Evidencia

- **Archivos**
  - [Eje Cilíndrico](/06_retos_y_proyectos/01_Practicas/Practica27-B.SLDPRT)
  - [Placa Base](/06_retos_y_proyectos/01_Practicas/Practica27-B.SLDPRT)
  
<!-- markdownlint-disable MD033 -->
<img src="/06_retos_y_proyectos/01_Practicas/Practica29.png" width="500" alt="Captura de pantalla de la práctica">

---

[Inicio](#03-fijar-y-flotar-componentes-en-ensamblajes-)

---

[Tabla de contenido principal](/Tabla_Contenido.md)
