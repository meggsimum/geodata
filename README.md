# Geodata

## World.gpkg

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
  -d natural_earth_vector\
  natural_earth_vector.zip

# create GeoPackage
ogr2ogr \
  -f GPKG \
  world.gpkg \
  natural_earth_vector/10m_cultural \
  ne_10m_admin_0_countries \
  ne_10m_populated_places

ogr2ogr \
  -f GPKG \
  -update \
  world.gpkg \
  natural_earth_vector/10m_physical/ne_10m_rivers_lake_centerlines.shp
```

## World.tiff

A downsampled version of the rasterfile from [Natural Earth](https://www.naturalearthdata.com/).
