# Geodata

## vector-data.gpkg

Extracted from [Natural Earth](https://www.naturalearthdata.com/). Contains the layers:
- ne_10m_admin_0_countries
- ne_10m_populated_places
- ne_10m_populated_places

```shell
# download
wget \
  http://naciscdn.org/naturalearth/packages/natural_earth_vector.zip

# unzip
unzip \
  -d natural_earth_vector \
  natural_earth_vector.zip

# create GeoPackage
ogr2ogr \
  -f GPKG \
  -nlt PROMOTE_TO_MULTI \
  vector-data.gpkg \
  natural_earth_vector/10m_cultural \
  ne_10m_admin_0_countries \
  ne_10m_populated_places

ogr2ogr \
  -f GPKG \
  -nlt PROMOTE_TO_MULTI \
  -update \
  vector-data.gpkg \
  natural_earth_vector/10m_physical/ne_10m_rivers_lake_centerlines.shp
```

## World.tiff

A downsampled version of the rasterfile from [Natural Earth](https://www.naturalearthdata.com/).

## Postal Codes Germany

- Taken from [ESRI Open Data](https://opendata-esri-de.opendata.arcgis.com/datasets/5b203df4357844c8a6715d7d411a8341_0?geometry=7.120%2C47.019%2C12.294%2C48.314)
- License: `Die Daten stehen unter der Open Database Licence frei zur Verfügung. Quelle der Rohdaten: © OpenStreetMap contributorsEinwohnerzahlen als Berechnungsgrundlage © Statistische Ämter des Bundes und der Länder`
- Converted to GeoPackage via:

```shell
wget \
  -O postal_codes_germany.zip \
  'https://opendata.arcgis.com/datasets/5b203df4357844c8a6715d7d411a8341_0.zip?outSR=%7B%22latestWkid%22%3A3857%2C%22wkid%22%3A102100%7D'

unzip \
  postal_codes_germany.zip \
  -d postal_codes_germany

ogr2ogr \
  -f GPKG postal_codes_germany.gpkg \
  -t_srs EPSG:4326 \
  postal_codes_germany \
  OSM_PLZ_072019
```