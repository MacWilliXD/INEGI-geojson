<div align="center">

# 🗺️ INEGI-geojson

### Repositorio de Datos Geográficos de México 2025

*Colección completa de archivos GeoJSON con geometrías y datos demográficos del INEGI*

[![GeoJSON](https://img.shields.io/badge/GeoJSON-4EAA25?style=for-the-badge&logo=json&logoColor=white)]()
[![INEGI](https://img.shields.io/badge/INEGI_2025-00ADD8?style=for-the-badge&logo=gov&logoColor=white)]()
[![México](https://img.shields.io/badge/México-006341?style=for-the-badge&logo=mexico&logoColor=white)]()
[![Open Data](https://img.shields.io/badge/Open_Data-FF6B6B?style=for-the-badge&logo=opendatainitiative&logoColor=white)]()

[Estructura](#-estructura-de-archivos) • [Nomenclatura](#-nomenclatura) • [Uso](#-cómo-usar) • [Contenido](#-contenido-de-los-datos)

</div>

---

## 📋 Descripción

**INEGI-geojson** es un repositorio que almacena datos geográficos oficiales de México del **Instituto Nacional de Estadística y Geografía (INEGI)** actualizados a **2025**.

Contiene archivos **GeoJSON** con multipolígonos georreferenciados y datos demográficos de:
- 🇲🇽 **República Mexicana** (completa)
- 🏛️ **32 Estados**
- 🏘️ **2,469 Municipios**
- 📍 **Miles de Localidades (AGEB)**

### 🎯 Propósito

Este repositorio sirve como fuente de datos para:
- 📊 Visualización de mapas interactivos
- 🗺️ Análisis geoespacial y demográfico
- 💻 Desarrollo de aplicaciones GIS
- 📱 Sistemas de información geográfica web
- 🔬 Investigación y estudios territoriales

---

## 📂 Estructura de Archivos

```
INEGI-geojson/
│
├── 📁 geojson_descargas/          # ✅ CARPETA PRINCIPAL (Formato actual 2025)
│   ├── AGEE.geojson                  # México completo - Todos los estados
│   ├── AGEM_01.geojson               # Municipios de Aguascalientes
│   ├── AGEM_02.geojson               # Municipios de Baja California
│   ├── AGEM_03.geojson               # Municipios de Baja California Sur
│   ├── ...                           # (32 archivos de estados)
│   ├── AGLOC_01001.geojson           # Localidades del municipio 001 de Aguascalientes
│   ├── AGLOC_01002.geojson           # Localidades del municipio 002 de Aguascalientes
│   └── ...                           # (Cientos de archivos de localidades)
│
├── 📁 Estados-OLD/                # ⚠️ Formato antiguo (Deprecated)
│   ├── AGEE_01.geojson               # Estado individual (formato antiguo)
│   └── ...
│
└── 📁 Municipios-OLD/             # ⚠️ Formato antiguo (Deprecated)
    └── ...
```

> **💡 Nota:** Se recomienda usar únicamente la carpeta **`geojson_descargas/`** que contiene el formato actualizado y consolidado.

---

## 🏷️ Nomenclatura

### Convención de Nombres

Los archivos siguen la nomenclatura oficial del INEGI basada en claves geográficas:

#### 🗺️ **AGEE.geojson** - Estados Completos
- Contiene todos los 32 estados de México en un solo archivo
- Geometrías tipo `MultiPolygon`
- Propiedades con datos demográficos

#### 🏘️ **AGEM_XX.geojson** - Municipios por Estado
Formato: `AGEM_[CódigoEstado].geojson`

| Código | Estado | Archivo |
|--------|--------|---------|
| 01 | Aguascalientes | `AGEM_01.geojson` |
| 02 | Baja California | `AGEM_02.geojson` |
| 09 | Ciudad de México | `AGEM_09.geojson` |
| 15 | Estado de México | `AGEM_15.geojson` |
| 19 | Nuevo León | `AGEM_19.geojson` |
| 23 | Quintana Roo | `AGEM_23.geojson` |
| ... | ... | ... |

<details>
<summary><b>📋 Ver tabla completa de códigos de estados (32 estados)</b></summary>

| Código | Estado |
|--------|--------|
| 01 | Aguascalientes |
| 02 | Baja California |
| 03 | Baja California Sur |
| 04 | Campeche |
| 05 | Coahuila |
| 06 | Colima |
| 07 | Chiapas |
| 08 | Chihuahua |
| 09 | Ciudad de México |
| 10 | Durango |
| 11 | Guanajuato |
| 12 | Guerrero |
| 13 | Hidalgo |
| 14 | Jalisco |
| 15 | México |
| 16 | Michoacán |
| 17 | Morelos |
| 18 | Nayarit |
| 19 | Nuevo León |
| 20 | Oaxaca |
| 21 | Puebla |
| 22 | Querétaro |
| 23 | Quintana Roo |
| 24 | San Luis Potosí |
| 25 | Sinaloa |
| 26 | Sonora |
| 27 | Tabasco |
| 28 | Tamaulipas |
| 29 | Tlaxcala |
| 30 | Veracruz |
| 31 | Yucatán |
| 32 | Zacatecas |

</details>

#### 📍 **AGLOC_XXXXX.geojson** - Localidades (AGEB)
Formato: `AGLOC_[CódigoEstado][CódigoMunicipio].geojson`

**Ejemplos:**
- `AGLOC_01001.geojson` → Localidades del municipio **001** de **Aguascalientes (01)**
- `AGLOC_23005.geojson` → Localidades del municipio **005** de **Quintana Roo (23)** (Benito Juárez/Cancún)
- `AGLOC_09002.geojson` → Localidades de la alcaldía **002** de **CDMX (09)** (Azcapotzalco)

---

## 📊 Contenido de los Datos

Cada archivo GeoJSON contiene propiedades con información estadística y demográfica:

### 🗺️ Estados (AGEE.geojson)

```json
{
  "type": "FeatureCollection",
  "features": [
    {
      "type": "Feature",
      "properties": {
        "cvegeo": "01",              // Clave geográfica
        "nom_agee": "Aguascalientes", // Nombre del estado
        "pob": 1425607,              // Población total
        "viv": 364470,               // Total de viviendas
        "pob_mas": 691821,           // Población masculina
        "pob_fem": 733786            // Población femenina
      },
      "geometry": {
        "type": "MultiPolygon",
        "coordinates": [...]
      }
    }
  ]
}
```

### 🏘️ Municipios (AGEM_XX.geojson)

```json
{
  "properties": {
    "cvegeo": "01001",           // Clave: Estado + Municipio
    "cve_agee": "01",            // Código del estado
    "cve_agem": "001",           // Código del municipio
    "nom_agem": "Aguascalientes", // Nombre del municipio
    "pob": 877190,               // Población
    "viv": 223456,               // Viviendas
    "pob_mas": 425789,           // Población masculina
    "pob_fem": 451401            // Población femenina
  },
  "geometry": {
    "type": "Polygon",
    "coordinates": [...]
  }
}
```

### 📍 Localidades (AGLOC_XXXXX.geojson)

```json
{
  "properties": {
    "cvegeo": "010010001",       // Clave: Estado + Municipio + Localidad
    "nom_loc": "Aguascalientes",  // Nombre de la localidad
    "pob": 877190,               // Población
    "lat": 21.88234,             // Latitud
    "lon": -102.29187,           // Longitud
    "altitud": 1880              // Altitud en metros
  },
  "geometry": {
    "type": "Point",
    "coordinates": [-102.29187, 21.88234]
  }
}
```

---

## 💻 Cómo Usar

### 📥 Clonar el Repositorio

```bash
git clone https://github.com/MacWilliXD/INEGI-geojson.git
cd INEGI-geojson
```

### 🗂️ Acceder a los Datos

```bash
# Navegar a la carpeta principal
cd geojson_descargas

# Ver archivos disponibles
ls -l
```

### 🔗 Uso en JavaScript (Fetch)

```javascript
// Cargar estados de México
fetch('geojson_descargas/AGEE.geojson')
  .then(response => response.json())
  .then(data => {
    console.log('Estados de México:', data);
    // data.features contiene todos los estados
  });

// Cargar municipios de Quintana Roo
fetch('geojson_descargas/AGEM_23.geojson')
  .then(response => response.json())
  .then(data => {
    console.log('Municipios de Q. Roo:', data);
  });
```

### 🗺️ Uso con Leaflet

```html
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />
  <script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>
</head>
<body>
  <div id="map" style="height: 600px;"></div>
  
  <script>
    // Crear mapa centrado en México
    const map = L.map('map').setView([23.6345, -102.5528], 5);
    
    // Añadir capa base
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      attribution: '© OpenStreetMap contributors'
    }).addTo(map);
    
    // Cargar y mostrar estados
    fetch('geojson_descargas/AGEE.geojson')
      .then(response => response.json())
      .then(data => {
        L.geoJSON(data, {
          style: { color: '#0066cc', weight: 2, fillOpacity: 0.3 },
          onEachFeature: (feature, layer) => {
            layer.bindPopup(`
              <b>${feature.properties.nom_agee}</b><br>
              Población: ${feature.properties.pob.toLocaleString()}<br>
              Viviendas: ${feature.properties.viv.toLocaleString()}
            `);
          }
        }).addTo(map);
      });
  </script>
</body>
</html>
```

### 🐍 Uso con Python (GeoPandas)

```python
import geopandas as gpd
import matplotlib.pyplot as plt

# Cargar estados
estados = gpd.read_file('geojson_descargas/AGEE.geojson')

# Visualizar
estados.plot(column='pob', cmap='YlOrRd', legend=True, figsize=(12, 8))
plt.title('Población por Estado en México')
plt.axis('off')
plt.show()

# Filtrar estados con más de 5 millones de habitantes
estados_grandes = estados[estados['pob'] > 5000000]
print(estados_grandes[['nom_agee', 'pob']])
```

### 🔍 Uso con QGIS

1. Abre **QGIS**
2. Ve a **Capa** → **Añadir Capa** → **Añadir Capa Vectorial**
3. Selecciona el archivo `.geojson` que necesites
4. Visualiza y analiza los datos

---

## 📦 Tamaño de los Archivos

| Tipo | Cantidad | Tamaño Aproximado |
|------|----------|-------------------|
| Estados completos | 1 archivo | ~15-20 MB |
| Municipios (por estado) | 32 archivos | ~5-30 MB c/u |
| Localidades (por municipio) | ~2,469 archivos | ~100 KB - 5 MB c/u |

> **⚠️ Nota:** Este repositorio puede ocupar varios GB de espacio. Considera clonar solo lo que necesites usando sparse-checkout.

### Clonar Solo lo Necesario

```bash
# Configurar sparse-checkout
git clone --filter=blob:none --sparse https://github.com/MacWilliXD/INEGI-geojson.git
cd INEGI-geojson
git sparse-checkout set geojson_descargas
```

---

## 🎨 Casos de Uso

### 1. Mapas Electorales
Visualización de resultados por municipio combinando con datos electorales.

### 2. Análisis Demográfico
Estudios de densidad poblacional, distribución urbana-rural.

### 3. Dashboards Geográficos
Paneles interactivos con estadísticas por región.

### 4. Planificación Territorial
Análisis de cobertura de servicios, infraestructura.

### 5. Investigación Académica
Estudios sociodemográficos, económicos y ambientales.

---

## 🔄 Actualización de Datos

Los datos en este repositorio corresponden al **Marco Geoestadístico 2025** del INEGI.

Para obtener datos más recientes:
1. Visita el sitio oficial del INEGI: https://www.inegi.org.mx/
2. Descarga los archivos actualizados del Marco Geoestadístico
3. Reemplaza los archivos en `geojson_descargas/`

---

## 🛠️ Herramientas Compatibles

Este repositorio es compatible con:

| Herramienta | Tipo | Uso |
|-------------|------|-----|
| **Leaflet** | JavaScript | Mapas web interactivos |
| **QGIS** | Desktop GIS | Análisis geoespacial avanzado |
| **Python (GeoPandas)** | Análisis de datos | Procesamiento y visualización |
| **R (sf)** | Análisis estadístico | Análisis espacial |
| **ArcGIS** | Desktop/Web GIS | Análisis profesional |
| **Mapbox** | Web mapping | Mapas personalizados |
| **D3.js** | Visualización | Gráficos interactivos |

---

## 📖 Documentación Adicional

Para más información sobre los datos y su estructura:

- 📚 [Marco Geoestadístico INEGI](https://www.inegi.org.mx/temas/mg/)
- 🗺️ [Especificaciones GeoJSON](https://geojson.org/)
- 🏛️ [Catálogo de Claves Geoestadísticas](https://www.inegi.org.mx/app/ageeml/)

---

## ⚠️ Carpetas Deprecadas

Las carpetas `Estados-OLD/` y `Municipios-OLD/` contienen datos en formatos anteriores que **ya no se mantienen**.

**Diferencias:**
- `Estados-OLD/`: Cada estado en archivo separado (AGEE_01.geojson, AGEE_02.geojson...)
- `geojson_descargas/AGEE.geojson`: Todos los estados en un solo archivo (formato actual)

Se recomienda **no usar** las carpetas `-OLD` para nuevos proyectos.

---

## 🤝 Contribuciones

Las contribuciones son bienvenidas para:
- 🐛 Reportar archivos corruptos o con errores
- 📝 Mejorar la documentación
- ✨ Añadir ejemplos de uso
- 🔄 Actualizar datos cuando haya nuevas versiones del INEGI

Para contribuir:
1. Fork este repositorio
2. Crea una rama para tu mejora
3. Commit tus cambios
4. Abre un Pull Request

---

## 📄 Licencia y Créditos

### Fuente de Datos
Todos los datos geográficos y demográficos pertenecen al **Instituto Nacional de Estadística y Geografía (INEGI)** de México.

- 🏛️ **Organismo:** INEGI - Instituto Nacional de Estadística y Geografía
- 📅 **Versión:** Marco Geoestadístico 2025
- 🔗 **Sitio Oficial:** https://www.inegi.org.mx/

### Uso de los Datos
Los datos del INEGI son de **dominio público** y pueden ser utilizados libremente con la atribución correspondiente.

---

## 🔗 Repositorios Relacionados

- 📚 [INEGI-ConsultasJS](https://github.com/tu-usuario/INEGI-ConsultasJS) - API JavaScript para consultar estos datos
- 🗺️ [AnalyGIS](https://github.com/tu-usuario/AnalyGIS) - Plataforma de visualización de mapas

---

## 📞 Soporte

Si encuentras problemas con los archivos:
- 🐛 Abre un [Issue](https://github.com/MacWilliXD/INEGI-geojson/issues)
- 📧 Contacta al mantenedor del repositorio
- 🏛️ Consulta la fuente oficial del [INEGI](https://www.inegi.org.mx/)

---

<div align="center">

**⭐ Si este repositorio te es útil, considera darle una estrella ⭐**

📊 Datos geográficos oficiales de México para toda la comunidad GIS

**🇲🇽 Hecho en México • 2025**

</div>