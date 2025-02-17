# Conversão de Coordenadas

Este módulo fornece funções para converter coordenadas de latitude e longitude em coordenadas UTM (Universal Transversa de Mercator) e coordenadas Cartesianas (x, y). Além disso, ele inclui uma função para processar um arquivo XML, convertendo as coordenadas de latitude e longitude contidas nele para coordenadas Cartesianas.

## Funções

### `longitude_to_utm_zone(longitude: float) -> int`

Calcula o número da zona UTM a partir da longitude.

**Parâmetros:**
- `longitude` (float): Longitude em graus decimais.

**Retorna:**
- `int`: Número da zona UTM.

### `latlon_to_utm(lat: float, lon: float) -> Tuple[float, float]`

Converte latitude e longitude para coordenadas UTM.

**Parâmetros:**
- `lat` (float): Latitude em graus decimais.
- `lon` (float): Longitude em graus decimais.

**Retorna:**
- `Tuple[float, float]`: Coordenadas UTM (Easting, Northing).

### `latlon_to_xy(lat: float, lon: float, min_lat: float, min_lon: float) -> Tuple[float, float]`

Converte latitude e longitude para coordenadas Cartesianas (x, y).

**Parâmetros:**
- `lat` (float): Latitude em graus decimais.
- `lon` (float): Longitude em graus decimais.
- `min_lat` (float): Latitude mínima de referência.
- `min_lon` (float): Longitude mínima de referência.

**Retorna:**
- `Tuple[float, float]`: Coordenadas Cartesianas em metros.

### `convert_coordinates(input_xml_path: str, output_xml_path: str) -> None`

Converte coordenadas de latitude e longitude em um arquivo XML para coordenadas Cartesianas.

**Parâmetros:**
- `input_xml_path` (str): Caminho do arquivo XML de entrada.
- `output_xml_path` (str): Caminho do arquivo XML de saída.

**Retorna:**
- `None`

## Exemplo de Uso

Aqui está um exemplo de como usar as funções deste módulo:

```python
from coordenadas import latlon_to_utm, latlon_to_xy, convert_coordinates

# Convertendo latitude e longitude para UTM
lat, lon = -23.5505, -46.6333
easting, northing = latlon_to_utm(lat, lon)
print(f"UTM: {easting}, {northing}")

# Convertendo latitude e longitude para coordenadas Cartesianas
min_lat, min_lon = -23.5600, -46.6400
x, y = latlon_to_xy(lat, lon, min_lat, min_lon)
print(f"Cartesianas: {x}, {y}")

# Convertendo coordenadas em um arquivo XML
convert_coordinates('input.xml', 'output.xml')
```