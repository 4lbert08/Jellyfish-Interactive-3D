# Jellyfish Interactive 3D

## 👤 Autor y asignatura

**Autor:** Alberto José Rodríguez Ruano
**Universidad:** ULPGC — Grado en Ingeniería Informática
**Asignatura:** Informática Gráfica

---

# Introducción

Este proyecto implementa una **medusa 3D interactiva y reactiva al audio** utilizando **Three.js**, combinando visualización generativa, animación biológica y efectos de post-procesado. La medusa responde al sonido ambiental con pulsos luminosos y cambios de color suaves, mientras que el usuario puede interactuar con ella mediante drag & drop, creando una experiencia inmersiva en un entorno submarino virtual.

El proyecto se ha diseñado para ser **ligero, modular y extensible**, permitiendo agregar nuevas interacciones, efectos de audio o cambios estéticos sin comprometer el rendimiento.

---

# Motivación artística y conceptual

El proyecto busca capturar la **fluidez y belleza de los organismos marinos**, llevando la interacción del usuario a un nivel visual y sensorial. Los principios detrás del diseño incluyen:

* **Movimiento orgánico y natural** de la medusa y sus tentáculos.
* **Interactividad lúdica**: el usuario puede manipular la medusa y observar su respuesta física y visual.
* **Visualización generativa**: colores, luz y partículas reaccionan de manera dinámica al audio y al tiempo.
* **Entorno submarino**: degradados, niebla, partículas y rayos de luz crean una experiencia inmersiva.

Este proyecto combina arte digital y programación, buscando un equilibrio entre estética y rendimiento.

---

# Funcionalidades principales

1. **Medusa 3D detallada**

   * Campana translúcida con efecto Fresnel.
   * Núcleo central emitiendo luz.
   * Tentáculos y brazos orales animados mediante esqueletos y SkinnedMesh.

2. **Interactividad avanzada**

   * Arrastrar y soltar con ratón o pantalla táctil.
   * Escalado y retorno suave al centro con animaciones tipo elastic.

3. **Audio reactivo**

   * Análisis de audio en tiempo real.
   * Glow y pulsos de la medusa modulados por la intensidad del sonido.

4. **Sistema de partículas flotantes**

   * Partículas de agua que reaccionan a la proximidad del usuario.
   * Variación de tamaño y movimiento para simular flujo submarino.

5. **Entorno submarino completo**

   * Fondo degradado mediante shader esférico.
   * Niebla vertical y rayos de luz cinematográficos.
   * Suelo y algas para dar profundidad al escenario.

6. **Post-processing avanzado**

   * Bloom para resaltar luminancia.
   * ACES Filmic Tone Mapping para renderizado realista.

---

# Explicación técnica

## 1. Setup inicial

Se crean la escena, la cámara y el renderer, junto con controles **OrbitControls**:

```javascript
camera = new THREE.PerspectiveCamera(62, window.innerWidth / window.innerHeight, 0.1, 1000);
controls = new OrbitControls(camera, renderer.domElement);
controls.enableDamping = true;
```

Esto permite rotación, zoom y control fluido.

## 2. Medusa 3D

* Campana y núcleo: **MeshPhysicalMaterial** y **MeshStandardMaterial**.
* Efecto Fresnel para halo luminoso mediante **ShaderMaterial**.
* Tentáculos y brazos orales: **SkinnedMesh** con animación ondulatoria.

## 3. Animación y color shift

* Cambios de color suave entre azul y morado.
* Intensidad y brillo modulados por el audio.
* Pulso de campana sincronizado con audio.

## 4. Interactividad

* Drag & drop con mouse o touch.
* Animaciones suaves de escala y retorno al centro.
* Cursor cambia según interacción.

## 5. Partículas y entorno

* Partículas flotantes que responden al mouse.
* Fondo generado con **shader esférico** y degradado invertido (claro arriba, oscuro abajo).
* Plantas y suelo de baja opacidad para profundidad.

## 6. Audio reactivo

* Uso de **AudioContext** y **AnalyserNode**.
* Intensidad media de frecuencias modula glow y pulsos.

---

# DEMO

Aquí se muestra un video demostrativo de la demo (haz clic sobre él para ver el video):

[![Ver demo](https://img.youtube.com/vi/aJOoplboNdo/0.jpg)](https://www.youtube.com/watch?v=aJOoplboNdo)


---

# Repositorio del proyecto

[Enlace al repositorio](https://codesandbox.io/p/sandbox/ig2526-s10-forked-rkl2zf)

---

# Técnicas y optimización

* Uso de **ShaderMaterial** para degradados y rayos de luz.
* **SkinnedMesh** optimizado para movimientos de tentáculos.
* **TWEEN.js** para animaciones suaves.
* **BufferGeometry** para partículas, reduciendo carga de render.
* Post-processing con **UnrealBloomPass**.

---

# 📚 Fuentes y referencias

* Three.js Documentation
* *The Book of Shaders* — Patricio González Vivo & Jen Lowe
* Investigación propia en animación y visualización generativa
* Inspiración en medusas y ecosistemas submarinos
* IA generativa (ChatGPT) para apoyo en optimización y organización del código
