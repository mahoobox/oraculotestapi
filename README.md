# Visor de Análisis de Biomasa

## 📝 Descripción
Interfaz web para la visualización de análisis de biomasa basado en imágenes satelitales. Esta herramienta permite visualizar y comparar datos NDVI (Índice de Vegetación de Diferencia Normalizada) entre dos imágenes satelitales, mostrando diversos análisis y métricas relacionadas con la biomasa.

## 🌟 Características
- Visualización de NDVI anterior, posterior y diferencia
- Histograma comparativo de NDVI
- Clasificación de NDVI
- Mapa de cambio en coberturas
- Conteo de píxeles por clase de cobertura
- Cálculos de biomasa y métricas relacionadas
- Interfaz responsiva y amigable
- Soporte para diferentes fuentes de datos (Landsat y Sentinel)

## 🛠️ Tecnologías Utilizadas
- HTML5
- JavaScript (ES6+)
- Tailwind CSS
- Plotly.js para visualizaciones
- Leaflet.js para mapas
- Fetch API para peticiones HTTP

## 📦 Dependencias CDN
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.7.1/leaflet.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet.draw/1.0.4/leaflet.draw.js"></script>
<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script src="https://cdn.tailwindcss.com"></script>
<script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
```

## 🚀 Instalación y Uso

### Instalación Local
1. Clona este repositorio:
```bash
git clone [URL-del-repositorio]
```

2. Navega al directorio del proyecto:
```bash
cd visor-analisis-biomasa
```

3. Estructura de archivos necesaria:
```
visor-analisis-biomasa/
├── index.html
├── resultadoAPI.html
└── README.md
```

### Uso
1. Abre `index.html` en un navegador web moderno
2. Ingresa la URL de la API en el formulario
3. Los resultados se mostrarán en `resultadoAPI.html`

### URL de API de Consulta por Defecto para test
```
https://oraculo.terrasacha.com/analisis-biomasa?imagenAnterior=img_20240806163058_2024_S2_B2_B3_B4_B5&imagenPosterior=img_20240806163016_2014_LC08_B2_B3_B4_B5&correcciones=normalization,radiance_conversion,topographic_correction&api=true
```

## 📊 Estructura de Datos
La API debe devolver un JSON con la siguiente estructura:

```javascript
{
    "NDVI": {
        "Anterior": {
            "Biomasa total (Ton)": number,
            "Área (Ha)": number,
            "Biomasa por Ha (Ton/Ha)": number,
            "Carbono Aéreo (Ton)": number,
            "CO2 Equivalente (Ton)": number
        },
        "Posterior": {
            // Misma estructura que Anterior
        },
        "Diferencia": {
            "Ganancia/Pérdida Biomasa Total (Ton)": number,
            "Ganancia/Pérdida Biomasa por Ha (Ton/Ha)": number,
            "Ganancia/Pérdida Carbono Aéreo (Ton)": number,
            "Ganancia/Pérdida CO2 Equivalente (Ton)": number,
            "Porcentaje Cambio Biomasa Total (%)": number
        }
    },
    "Histograma Comparativo del NDVI Resumido": {
        "NDVI Anterior (Promedio)": number,
        "NDVI Posterior (Promedio)": number,
        "NDVI Anterior (Desviación Estándar)": number,
        "NDVI Posterior (Desviación Estándar)": number
    },
    "Histograma Comparativo del NDVI Detalle": {
        "NDVI Anterior": number[],
        "NDVI Posterior": number[]
    },
    "Conteo de Píxeles por Clase de Cobertura": {
        "clases": string[],
        "datos": {
            "Anterior": {
                "valores": number[],
                "porcentajes": number[]
            },
            "Posterior": {
                "valores": number[],
                "porcentajes": number[]
            }
        }
    },
    "imagenes": {
        "ndvi_anterior_posterior_diferencia": string, // base64
        "clasificacion_ndvi": string, // base64
        "mapa_cambio_coberturas": string // base64
    }
}
```


## 🔍 Diagnóstico y Solución de Problemas

### Problemas Comunes
1. **Error CORS**
   - Solución: Habilitar una extensión CORS en el navegador para desarrollo
   - En producción: Configurar el servidor para permitir las peticiones

2. **Imágenes no se cargan**
   - Verificar que el base64 se está recibiendo correctamente
   - Comprobar la estructura del objeto `imagenes` en la respuesta

3. **Gráficos no se muestran**
   - Revisar la consola del navegador para errores
   - Verificar que los datos tienen el formato correcto

## 📄 Licencia
MIT

