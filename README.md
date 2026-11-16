# JumpDataAnalysis (`kinepipe-jda`)

Herramienta web **100% offline y autocontenida** (un único archivo HTML sin dependencias ni instalación) para el análisis biomecánico de saltos verticales (SJ, CMJ, DJ, AJ) a partir de archivos **`.slk` (SYLK)** exportados desde **Noraxon myoRESEARCH** con datos capturados en plataforma **Zebris FDM 1.5**.

---

## Características Principales

- **Ingesta directa de archivos Noraxon myoRESEARCH (`.slk`):** Lee automáticamente la señal de fuerza vertical $F_z(t)$, metadatos del sujeto, tipo de salto y frecuencia de muestreo (también admite `.csv` / `.tsv` / `.txt`).
- **Curva $F_z(t)$ interactiva con tracking real:** Al recorrer la curva con el mouse muestra el tiempo exacto $t$ y la fuerza real interpolada $F(t)$ en Newtons.
- **Ajuste manual preciso de puntos clave:**
  - Arrastre directo de líneas verticales (`Onset`, `v = 0`, `Despegue`, `Aterrizaje`) sin desplazamiento de la curva de fondo.
  - Selección de tramos en el gráfico para asignar manualmente `Pesaje Basal (BW)`, `Impulso Total`, `Descarga`, `Propulsión`, `Fase de Vuelo` o `Shape Factor`.
  - Panel numérico con edición directa en segundos (`step = 0.005 s`) y `BW (N)`.
- **Métricas biomecánicas completas:**
  - Altura de salto por **tiempo de vuelo** ($h = \frac{g \cdot t_v^2}{8}$) y por **impulso-momento** ($h = \frac{v_{TO}^2}{2g}$).
  - Fuerza pico ($N$ y $\%BW$), impulso concéntrico neto ($N\cdot s$), potencia (Sayers / Harman) e índice de fuerza reactiva (RSI).
  - **RFD** pico instantánea y por ventanas tempranas (`0–50 ms`, `0–100 ms`, `0–200 ms`).
  - **Jump Shape Factor** calculado sobre el impulso propulsivo concéntrico (`v = 0` → `t_TO`):
    $$\text{Shape Factor} = \frac{J_{net}}{(F_{máx} - BW) \cdot t_{impulso}}$$
    - `< 0.40`: Picuda / Tardía (baja RFD inicial)
    - `0.40 – 0.65`: Triangular / Normal
    - `> 0.65`: Cuadrada / Rectangular (fuerza sostenida)
- **Exportación:** Informe técnico autónomo en HTML (color o escala de grises) y tabla comparativa multi-ensayo en CSV (`;`, UTF-8 con BOM).

---

## Uso Rápido

1. Descarga [`KineJump-Simple-Datos.html`](./KineJump-Simple-Datos.html) (o abre [`index.html`](./index.html) vía GitHub Pages).
2. Arrastra o carga uno o varios archivos **`.slk`** exportados desde **Noraxon myoRESEARCH** (capturados con **Zebris FDM 1.5**).
3. Ajusta manualmente los marcadores si es necesario y exporta el informe o el lote en CSV.

---

## Autoría y Contexto

- **Autor:** Klgo. Felipe Alonso Vargas Ríos (`@kinepipe`)
- **Asignatura:** RKI401 Análisis del Movimiento Humano — Escuela de Kinesiología
- **Hardware de referencia:** Plataforma Zebris FDM 1.5 / Software Noraxon myoRESEARCH
- **Licencia:** MIT
