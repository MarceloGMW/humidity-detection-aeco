# Checklist de Gobernanza y Licencias

## Privacidad y Consentimiento
- [x] Las imágenes del dataset NO contienen datos personales identificables (rostros, matrículas, etc.)
- [x] Las fotografías fueron tomadas en espacios de obra/edificios con autorización del propietario o cliente
- [x] No se almacenan datos de localización GPS en los metadatos de las imágenes

## Minimización de Datos
- [x] Solo se recopilaron imágenes directamente relevantes para la detección de manchas de humedad
- [x] El dataset no incluye información sensible más allá de las imágenes de patología
- [x] Se aplicó split 80/20 para maximizar el aprendizaje con los datos disponibles

## Declaración de Limitaciones (cuándo NO usar este modelo)
- ❌ No usar para diagnóstico estructural definitivo — es una herramienta de apoyo, no un sustituto de un técnico cualificado
- ❌ No aplicar en edificios con materiales muy distintos a los del dataset de entrenamiento (p.ej., fachadas prefabricadas especiales)
- ❌ No usar con imágenes de baja resolución (<300x300px) o con iluminación extremadamente deficiente
- ❌ Los resultados no son válidos para informes periciales legales sin validación de un experto humano

## Nota de Riesgos: FN vs FP
| Tipo de error | Riesgo | Impacto |
|---------------|--------|---------|
| **Falso Negativo (FN)** | **ALTO** | No detectar humedad real puede llevar a ignorar daños estructurales progresivos |
| **Falso Positivo (FP)** | Moderado | Genera alarmas innecesarias y coste de inspecciones adicionales, pero no causa daño directo |

> **Conclusión**: En contexto AECO, los FN son más críticos que los FP. Se recomienda operar con umbral de confianza reducido (conf=0.25) para minimizar FN, asumiendo más FP.

## Licencia del Modelo
**Licencia:** MIT

Este modelo y su código fuente se distribuyen bajo licencia MIT. Cualquier uso en producción debe incluir validación humana.

## Derechos del Dataset
- **Origen:** Dataset propio recopilado y etiquetado por los autores
- **Plataforma:** Roboflow Universe (workspace: marcelos-workspace-rfie2)
- **Etiquetado:** Manual asistido por SAM (Segment Anything Model)
- **Uso permitido:** Académico e investigación — uso comercial requiere autorización expresa de los autores

---
*Autores: Marcelo Melluso & Benoit Courbin — MAIC1125, 2026*
