## Seções do Arquivo de Configuração

- **trace_path** (`str`): Caminho do arquivo de trace a ser utilizado na simulação.

### Seção `DroneCircular`

- **center** (`Tuple[float, float]`): Coordenadas do centro do drone circular.
- **radius_meters** (`int`): Raio do drone circular em metros.
- **max_speed** (`int`, opcional): Velocidade máxima do drone. Valor padrão: `10`.
- **start_angle** (`int`, opcional): Ângulo inicial do drone. Valor padrão: `0`.

### Seção `DroneAngular`

- **start_point** (`Tuple[float, float]`): Ponto inicial do drone angular.
- **max_length** (`int`): Comprimento máximo do drone angular.
- **start_angle** (`int`, opcional): Ângulo inicial do drone. Valor padrão: `0`.
- **max_turns** (`int`, opcional): Número máximo de voltas. Valor padrão: `3`.
- **angle_alpha** (`int`, opcional): Ângulo alfa. Valor padrão: `30`.
- **max_speed** (`int`, opcional): Velocidade máxima do drone. Valor padrão: `10`.

### Seção `DroneTractor`

- **start_point** (`Tuple[float, float]`): Ponto inicial do drone trator.
- **width_between_tracks** (`int`): Largura entre as trilhas.
- **max_length** (`int`): Comprimento máximo.
- **max_turns** (`int`): Número máximo de voltas.
- **orientation** (`str`, opcional): Orientação do drone. Valor padrão: `"horizontal"`.
- **max_speed** (`int`, opcional): Velocidade máxima do drone. Valor padrão: `10`.

### Seção `DroneStatic`

- **point** (`Tuple[float, float]`): Ponto onde o drone estático será criado.

### Seção `DroneSquare`

- **center_point** (`Tuple[float, float]`): Ponto central do drone quadrado.
- **side_length** (`int`): Comprimento do lado do quadrado.
- **angle_degrees** (`int`, opcional): Ângulo do quadrado. Valor padrão: `90`.
- **max_speed** (`int`, opcional): Velocidade máxima do drone. Valor padrão: `10`.

### Seção `DroneFollowing`

- **vehicle_id** (`str`, opcional): ID do veículo a ser seguido. Valor padrão: `"0"`.
- **offset_distance** (`int`, opcional): Distância de offset. Valor padrão: `10`.
- **max_speed** (`int`, opcional): Velocidade máxima do drone. Valor padrão: `10`.

### Seção `ExportVideo`

- **video_directory** (`str`): Diretório onde o vídeo será exportado.
- **limits_map** (`Optional[Tuple[float, float]]`, opcional): Limites do mapa. Valor padrão: `0`.
- **only_vants** (`int`, opcional): Exportar apenas vants. Valor padrão: `0`.

### Seção `ExportXML`

- **new_xml_path** (`str`): Caminho do novo arquivo XML.
- **geo** (`int`, opcional): Configuração geográfica. Valor padrão: `1`.

### Seção `ChangeLegend`

- **old_legend** (`str`): Legenda antiga.
- **new_legend** (`str`): Nova legenda.

### Seção `PrintVehicleInfo`

- **vehicle_id** (`str`): ID do veículo cujas informações serão impressas.

### Seção `RemoveVehicle`

- **vehicle_id** (`str`): ID do veículo a ser removido.

# Exemplo de arquivo de configuração

```
[Simulation]
trace_path = manhattan.xml

[DroneCircular]
center = -73.986478, 40.744406
radius_meters = 40
max_speed = 10
start_angle = 0

[DroneAngular]
start_point = -73.983754, 40.745802
max_length = 40
max_turns = 3
angle_alpha = 30
max_speed = 10

[DroneTractor]
start_point = -73.983754, 40.745802
width_between_tracks = 70
max_length = 100
max_turns = 6
orientation = vertical
max_speed = 10

[DroneStatic]
point = -73.983754, 40.745802

[DroneFollowing]
vehicle_id = 14
offset_distance = 10
max_speed = 10

[DroneSquare]
center_point = -73.983754, 40.745802
side_length = 50
angle_degrees = 90
max_speed = 10

[ChangeLegend1]
old_legend = VANT
new_legend = UAV

[ChangeLegend2]
old_legend = type
new_legend = Car

[ExportVideo]
video_directory = output_video
only_vants = 0

[ExportXML]
new_xml_path = output_simulation.xml
geo = 0
```

# Detalhes:

Ao criar o arquivo de configuração, é importante manter uma ordem coesa. As configurações são lidas na ordem, então, se for remover um veiculo, o comando deve vir antes da exportação.
Se for alterar alguma legenda do vídeo, o comando deve vir antes de exportar para vídeo.