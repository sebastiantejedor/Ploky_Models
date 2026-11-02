# Floki — rig listo para animar

"izq / der" = lado izquierdo/derecho **visto desde quien mira el dibujo**.
Cada grupo trae `data-pivot="x y"` con el punto de rotación sugerido (unidades del viewBox 559 × 693.93).

## Archivos
| Archivo | Para qué |
|---|---|
| `floki_partes.svg` | Personaje por capas, con fondo blanco |
| `floki_partes_sin_fondo.svg` | Igual, fondo transparente (úsalo para animar) |
| `floki_demo_animado.svg` | Demo con CSS (parpadeo, respiración, orejas...). Ábrelo en el navegador |
| `partes/` | Cada pieza en su propio SVG (mismo viewBox, para After Effects / Rive / Spine / Lottie) |

## Jerarquía (de atrás hacia adelante)
```
floki_personaje
├─ pierna_izq            pivote 205,585   └ pierna_izq_pie
├─ pierna_der            pivote 335,585   └ pierna_der_pie
├─ cuerpo                pivote 280,590   └ cuerpo_barriga
├─ brazo_izq             pivote 172,440   └ brazo_izq_mano
├─ brazo_der             pivote 378,440   └ brazo_der_mano
└─ cabeza                pivote 270,425
   ├─ mechon             pivote 258,66
   ├─ cabeza_contorno
   ├─ oreja_izq          pivote 140,150
   ├─ oreja_der          pivote 440,78
   ├─ hocico             pivote 393,305
   ├─ ojo_der            pivote 467,163   ├ ojo_der_blanco  └ ojo_der_pupila (recortada al ojo)
   ├─ cabeza_pelaje
   ├─ ojo_izq            pivote 232,213   ├ ojo_izq_contorno ├ ojo_izq_blanco └ ojo_izq_pupila (recortada)
   ├─ linea_menton
   ├─ nariz              pivote 394,240
   ├─ boca               pivote 400,300   ├ boca_contorno └ boca_dientes
   └─ parpado_izq / parpado_der   (extra: arrancan cerrados a escala 0; anímalos con scaleY para parpadear)
```

## Ojo con esto
El dibujo original era una sola silueta, así que brazos, piernas y cabeza se separaron con **recortes rectos**
(`clip_*` en `<defs>`). Se ven perfectos en reposo y con movimientos suaves:
- cabeza: ±3–4°
- brazos: hasta ~20–25° (se ven bien)
- piernas: ~5° (más que eso se nota el corte en la cadera; para caminar conviene redibujar esa zona)

Orejas, hocico y ojo derecho van **debajo** del pelaje a propósito: se ven por los huecos del pelaje original.
