# BizCure · Simulador de Diagnóstico Empresarial

> **BizCure** es un simulador educativo de diagnóstico empresarial basado en el **Diagrama de Ishikawa** y el **Árbol de Problemas**, con estética cubista corporativa y gamificación progresiva. Desarrollado para la Unidad Didáctica de Investigación e Innovación Tecnológica (IDC) de la UTP.

---

## 🎯 Propósito didáctico

BizCure aplica el **ciclo de aprendizaje experiencial de Kolb** para que los estudiantes:

1. **Experimenten concretamente** un problema empresarial real (Fase 1 · Iceberg).
2. **Observen y reflejen** desglosando causas por categorías (Fase 2 · Ishikawa).
3. **Conceptualicen abstractamente** priorizando una causa raíz (Fase 3 · Árbol de Problemas).
4. **Activen y sinteticen** un pitch de intervención con diseño (Fase 4 · Veredicto).

---

## 📂 Archivos del proyecto

| Archivo | Descripción |
|---------|-------------|
| `bizcure_fase3_v2.html` | Simulador completo, self-contained, PWA-ready. Contiene todo el CSS, JS, imágenes en base64 y service worker. |
| `fase2_explicacion.md` | Documento pedagógico detallado que explica la Fase 2 (Ishikawa + 5 Porqués + posición en Kolb). |
| `README.md` | Este documento. |

---

## 🏗️ Arquitectura de fases

```
Registro de Agencia (2-4 consultores)
        ↓
┌─────────────────────────────────────────────────────────────┐
│  FASE 1 · ICEBERG (Kolb: Experiencia Concreta)             │
│  • Define el síntoma principal                               │
│  • Juego: Inmersión 390 — hunde causas raíz, deja pasar     │
│    síntomas (canvas interactivo)                             │
└─────────────────────────────────────────────────────────────┘
        ↓
┌─────────────────────────────────────────────────────────────┐
│  FASE 2 · ISHIKAWA (Kolb: Observación Reflexiva +          │
│  Conceptualización)                                          │
│  • 5 espinas: Medios, Mensaje, Mercado, Management, Métodos  │
│  • Técnica de los 5 Porqués en cada espina                   │
│  • "El Inquisidor" provoca profundidad con preguntas guiadas│
│  • Último porqué de cada espina migra al Árbol como raíz   │
└─────────────────────────────────────────────────────────────┘
        ↓
┌─────────────────────────────────────────────────────────────┐
│  FASE 2b · CAZASIGNOS (Mini-juego de refuerzo)              │
│  • ¿Causa o Efecto? contrarreloj                             │
│  • Caso transversal: IA generativa + resistencia orgánica   │
│  • Puerta de validación antes del Árbol                      │
└─────────────────────────────────────────────────────────────┘
        ↓
┌─────────────────────────────────────────────────────────────┐
│  FASE 3 · ÁRBOL DE PROBLEMAS (Kolb: Conceptualización        │
│  Abstracta) — MEJORADA                                      │
│  • Árbol SVG interactivo invertido (raíces → tronco → ramas)│
│  • Panel de subproblemas editable (decompose → solve →     │
│    merge)                                                    │
│  • Matriz de priorización 5×3 (Impacto × Facilidad × Diseño) │
│  • Campo de métrica de éxito                                 │
└─────────────────────────────────────────────────────────────┘
        ↓
┌─────────────────────────────────────────────────────────────┐
│  FASE 3b · QUIZ DE VALIDACIÓN (6 preguntas)                 │
│  • Verificación de comprensión conceptual                    │
│  • Retroalimentación positiva inmediata por pregunta         │
│  • Desbloqueo del Pitch solo con ≥4/6 aciertos             │
└─────────────────────────────────────────────────────────────┘
        ↓
┌─────────────────────────────────────────────────────────────┐
│  FASE 4 · SÍNTESIS / PITCH (Cierre · Triaje del Consultor) │
│  • Dossier ejecutivo con: causa raíz, subproblemas,         │
│    métrica de éxito, puntaje de matriz, firmas               │
│  • Exportable a PDF (impresión)                              │
└─────────────────────────────────────────────────────────────┘
```

---

## 🎨 Estética Cubista Corporativa (IDC)

La identidad visual de BizCure sigue una estética de **collage analítico** inspirada en el cubismo:

- **Paleta estricta:**
  - `#0072b9` — Azul IDC (estructura, planos)
  - `#f3a100` — Amarillo/Ámbar (acentos, aciertos, tronco)
  - `#33322f` — Tinta (bordes, texto, peso visual)
  - `#f2f1ec` — Papel (fondo)
  - `#555553` — Gris (textos secundarios)
- **Sin gradientes.** Sin claroscuro. Bloques puros de color.
- **Planos fragmentados:** recortes con `clip-path`, sombras desfasadas (`::after`), rotaciones mínimas (±0.8°).
- **Tipografía cartel:** títulos partidos en fragmentos (`.titulo-cubista`) con ángulos de rotación.

---

## 🎮 Gamificación · Sistema de Puntos y Rangos

Un HUD fijo muestra el progreso del consultor:

| Rango | Puntos necesarios |
|-------|-------------------|
| Practicante | 0 |
| Junior | 25 |
| Analista | 70 |
| Consultor Senior | 130 |
| Director de Estrategia | 200 |

**Fuentes de puntos:**
- Ishikawa con causas raíz: +30 pts
- Causa raíz priorizada: +25 pts
- Cazasignos superado: +20 pts
- Inmersión completada: +20 pts
- Quiz de validación aprobado: +25 pts
- Causas hundidas (Inmersión): +10 pts cada una
- Cazasignos correctos: variable (+10 a +25 según rapidez y racha)

---

## 🧩 Fase 3 · Mejoras destacadas (v2)

### Árbol SVG Interactivo
- Visualización de **árbol invertido** en SVG con 5 nodos raíz clickeables.
- Cada nodo muestra la causa raíz del Ishikawa correspondiente.
- Al seleccionar una raíz, el **tronco** se actualiza con animación y las líneas de conexión se iluminan.
- **Panel de detalle del nodo**: descripción editable + calificación de impacto (1-5 estrellas).

### Panel de Subproblemas (metáfora *Tree of Problems*)
- Sistema inspirado en el framework *Tree of Problems* (Zebaze et al., 2024): **decompose → solve → merge**.
- Cada subproblema tiene: nombre, espina de origen, impacto (1-5), toggle «¿Atacable con diseño?».
- Contador automático: subproblemas totales vs. atacables con diseño.

### Matriz de Priorización 5×3
- Cada raíz se evalúa en tres criterios (1-5): **Impacto**, **Facilidad de ataque**, **Relación con diseño**.
- Puntuación total automática. La fila ganadora se marca con ⭐ y puede ser usada como tronco.
- Campo adicional: **«¿Cómo medirás el éxito?»** para definir KPIs.

### Quiz de Validación (6 preguntas)
- Insertado como **Fase 3b** entre el Árbol y el Pitch.
- Verifica comprensión de conceptos clave: diferencia síntoma/causa, priorización de raíz única, significado de *merge*, posición en Kolb, etc.
- **Retroalimentación inmediata**: cada respuesta correcta o incorrecta incluye explicación pedagógica.
- **Reintentos por pregunta**: si falla, puede reintentar antes de avanzar.
- **Desbloqueo condicional**: solo ≥4/6 aciertos habilitan el Pitch.

### Pitch Mejorado
- Incluye resumen ejecutivo con: causa raíz, puntaje de matriz, subproblemas detectados, métrica de éxito.
- El pitch textual integra todos los elementos estructurados.
- Exportable a PDF mediante impresión (`Ctrl+P` / `Cmd+P`).

---

## 📱 PWA (Progressive Web App)

El archivo es una **PWA self-contained**:
- Manifest generado dinámicamente en JS.
- Service Worker con estrategia *cache-first*.
- Funciona offline después de la primera carga.
- Íconos en base64 (sin dependencias externas).
- Responsive: adaptado a desktop, tablet y móvil.

---

## 🚀 Cómo usar

### Opción 1: Abrir directamente
1. Abre `bizcure_fase3_v2.html` en cualquier navegador moderno (Chrome, Firefox, Edge, Safari).
2. No requiere servidor ni instalación.

### Opción 2: Instalar como PWA
1. Abre el archivo en Chrome/Edge.
2. Haz clic en el ícono de instalación (aparece en la barra de direcciones).
3. Se instala como aplicación standalone en tu dispositivo.

### Opción 3: Servir localmente
```bash
# Python 3
python -m http.server 8000

# Node.js
npx serve .
```
Luego abre `http://localhost:8000/bizcure_fase3_v2.html`.

---

## 🧪 Flujo de trabajo recomendado para el estudiante

1. **Registro:** forma un equipo de 2-4 consultores con nombre de agencia.
2. **Fase 1 (Iceberg):** define el síntoma principal y juega *Inmersión 390* para distinguir causa de síntoma bajo presión.
3. **Fase 2 (Ishikawa):** desglosa cada espina con los 5 Porqués hasta llegar a la raíz. El Inquisidor te empuja a profundizar.
4. **Fase 2b (Cazasignos):** demuestra que sabes distinguir causa de efecto. Supera el reto para acceder al Árbol.
5. **Fase 3 (Árbol):** selecciona una raíz como tronco, define subproblemas, evalúa la matriz de priorización y establece la métrica de éxito.
6. **Fase 3b (Quiz):** responde las 6 preguntas de validación. Revisa conceptos si fallas.
7. **Fase 4 (Pitch):** genera el dossier ejecutivo, firma con tu equipo y exporta a PDF.

---

## 📚 Referencias y marco teórico

- **Kolb, D. A.** — *Experiential Learning: Experience as the Source of Learning and Development* (1984). Las 4 fases de BizCure se mapean directamente al ciclo CE → RO → AC → AE.
- **Ishikawa, K.** — *Guía para el control de calidad* (1968). Las 5 espinas adaptadas del 6M industrial al contexto de servicios/creatividad.
- **Zebaze, A., Sagot, B. & Bawden, R.** — *Tree of Problems: Improving structured problem solving with compositionality* (2024). La metáfora decompose → solve → merge aplicada al panel de subproblemas.
- **Ohno, T.** — *Toyota Production System* (1978). Técnica de los 5 Porqués.

---

## 👤 Autor y créditos

**Desarrollado por:** Mg. Mario Rafael Quiroz Martínez  
**Unidad Didáctica:** Investigación e Innovación Tecnológica (IDC) — UTP  
**Marca creativa:** d3magindesign  
**Correo institucional:** c12139@utp.edu.pe

> *BizCure es parte de un ecosistema de herramientas didácticas interactivas que incluye el sistema **Roma-Capital-Generator** (construcción geométrica de la Capitalis Monumentalis) y el **Taller Semiótico** (gamificación del modelo de Barthes).* 

---

## 📄 Licencia

Este material es de uso exclusivo para fines educativos en la Unidad Didáctica IDC de la UTP. El código HTML/CSS/JS es self-contained y puede ser adaptado con atribución al autor.

---

## 🛠️ Notas técnicas

- **Sin dependencias externas** (salvo GSAP desde CDN para animaciones de scroll).
- **Sin framework JS** (vanilla JavaScript, ES6+).
- **Imágenes en base64** (logo IDC, favicon, apple-touch-icon) — no requiere conexión a internet.
- **Service Worker inline** generado dinámicamente vía `Blob` + `URL.createObjectURL`.
- **CSS con variables nativas** (`:root`) para la paleta IDC.
- **Compatible con impresión** (`@media print`) para exportación de dossier.

---

*Última actualización: 2025 · Fase 3 v2 (Árbol de Problemas mejorado + Quiz de validación)*
