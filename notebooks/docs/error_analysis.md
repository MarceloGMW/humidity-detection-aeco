# Análisis de Errores — Detección de Manchas de Humedad

## Falsos Positivos (FP) — El modelo detecta humedad donde no la hay

| # | Tipo detectado | Hipótesis probable |
|---|----------------|--------------------|
| 1 | Eflorescencias | Zonas de pared con cambios de textura similares a eflorescencias pero causados por pintura descascarada |
| 2 | Filtraciones   | Sombras proyectadas en esquinas que el modelo confunde con manchas de filtración oscuras |
| 3 | Condensación   | Reflejos de luz en superficies vidriadas similares a patrones de condensación superficial |

## Falsos Negativos (FN) — El modelo no detecta humedad presente

| # | Tipo no detectado | Hipótesis probable |
|---|-------------------|--------------------|
| 1 | Capilaridad       | Manchas de capilaridad incipiente con bajo contraste respecto al fondo (pared blanca) |
| 2 | Filtraciones      | Manchas de tamaño muy pequeño (<30px) no suficientemente representadas en el dataset de entrenamiento |
| 3 | Eflorescencias    | Eflorescencias en estado inicial con textura difusa, difíciles de distinguir del ruido de la imagen |

## 3 Mejoras Prioritarias del Dataset

1. **Ampliar ejemplos de capilaridad incipiente** — Actualmente el dataset tiene pocas imágenes de manchas en estado temprano. Recolectar al menos 50 imágenes adicionales de capilaridad leve con variedad de iluminación.

2. **Añadir imágenes difíciles (hard negatives)** — Incluir imágenes de superficies con texturas similares a humedades (pintura descascarada, sombras, manchas de cal) etiquetadas como "no humedad" para reducir FP.

3. **Balancear clases** — Verificar que todas las clases (Capilaridad, Condensación, Eflorescencias, Filtraciones) tengan representación similar. Aplicar augmentación adicional en clases minoritarias.
