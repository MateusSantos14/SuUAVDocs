# Documentação da Classe `Simulation`

A classe `Simulation` é responsável por representar uma simulação de veículos e drones. Ela permite a leitura de um arquivo XML de traços, criação de drones e exportação de resultados.

## Métodos

### `__init__(trace_path: str)`

Inicializa a simulação com base no caminho do arquivo XML de traços.

**Parâmetros:**
- `trace_path` (str): Caminho do arquivo XML contendo os traços da simulação.

### `read_xml(trace_path: str)`

Lê o arquivo XML e popula a lista de veículos.

**Parâmetros:**
- `trace_path` (str): Caminho do arquivo XML.

### `getVehicleById(id: str) -> Vehicle`

Retorna um veículo pelo ID.

**Parâmetros:**
- `id` (str): ID do veículo.

**Retorna:**
- `Vehicle`: Objeto do veículo.

**Lança:**
- `ValueError`: Se o ID não for encontrado.

### `export_to_video(video_directory: str, limits_map: int = 0, only_vants: int = 0)`

Exporta a simulação para um vídeo.

**Parâmetros:**
- `video_directory` (str): Diretório de saída do vídeo.
- `limits_map` (int): Limites do mapa. Se 0, calcula automaticamente.
- `only_vants` (int): Define se apenas drones devem ser incluídos no vídeo.

### `get_timestep_total() -> int`

Retorna o total de intervalos de tempo da simulação.

**Retorna:**
- `int`: Total de intervalos de tempo.

### `export_timesteps_to_xml(new_xml_path: str, geo: int = 1)`

Exporta os intervalos de tempo para um arquivo XML.

**Parâmetros:**
- `new_xml_path` (str): Caminho do arquivo XML de saída.
- `geo` (int): Define se as coordenadas devem ser mantidas geográficas. Se 0 converte para valores maiores que 0.

### `create_drone_angular(start_point: Tuple[float, float], max_length: float, start_angle: int = 0, max_turns: int = 3, angle_alpha: int = 30, max_speed: float = 10)`

Cria um drone com um padrão de movimento angular.

**Parâmetros:**
- `start_point` (Tuple[float, float]): Ponto inicial (latitude, longitude).
- `max_length` (float): Comprimento máximo de cada segmento.
- `start_angle` (int): Ângulo inicial de movimento.
- `max_turns` (int): Número máximo de curvas.
- `angle_alpha` (int): Ângulo de inclinação para as curvas.
- `max_speed` (float): Velocidade máxima do drone.

### `create_drone_static(point: Tuple[float, float])`

Cria um drone estacionário em um ponto específico.

**Parâmetros:**
- `point` (Tuple[float, float]): Coordenadas do ponto (latitude, longitude).

### `create_drone_following(vehicle_id: str, offset_distance: float, max_speed: float = 10)`

Cria um drone que segue um veículo.

**Parâmetros:**
- `vehicle_id` (str): ID do veículo a ser seguido.
- `offset_distance` (float): Distância de offset entre o drone e o veículo.
- `max_speed` (float): Velocidade máxima do drone.

**Lança:**
- `ValueError`: Se o ID do veículo não for encontrado.

### `create_drone_tractor(start_point: Tuple[float, float], width_between_tracks: float, max_length: float, max_turns: int, orientation: str = "horizontal", max_speed: float = 10)`

Cria um drone com um padrão de movimento em trator.

**Parâmetros:**
- `start_point` (Tuple[float, float]): Ponto inicial (latitude, longitude).
- `width_between_tracks` (float): Distância entre as trilhas.
- `max_length` (float): Comprimento máximo de cada trilha.
- `max_turns` (int): Número máximo de curvas.
- `orientation` (str): Orientação do movimento ("horizontal" ou "vertical").
- `max_speed` (float): Velocidade máxima do drone.

### `create_drone_circular(center: Tuple[float, float], radius_meters: float, max_speed: float = 10, start_angle: int = 0)`

Cria um drone com um padrão de movimento circular.

**Parâmetros:**
- `center` (Tuple[float, float]): Coordenadas do centro do círculo.
- `radius_meters` (float): Raio do círculo em metros.
- `max_speed` (float): Velocidade máxima do drone.
- `start_angle` (int): Ângulo inicial de movimento.

### `create_drone_square(center_point: Tuple[float, float], side_length: float, angle_degrees: int = 90, max_speed: float = 10)`

Cria um drone com um padrão de movimento quadrado.

**Parâmetros:**
- `center_point` (Tuple[float, float]): Coordenadas do centro do quadrado.
- `side_length` (float): Comprimento do lado do quadrado.
- `angle_degrees` (int): Ângulo inicial de movimento.
- `max_speed` (float): Velocidade máxima do drone.

### `create_drone_generic(start_point: Tuple[float, float], distance_lists: List[float], angles_list: List[float], max_speed: float = 10)`

Cria um drone com um padrão de movimento genérico.

**Parâmetros:**
- `start_point` (Tuple[float, float]): Ponto inicial (latitude, longitude).
- `distance_lists` (List[float]): Lista de distâncias a serem percorridas.
- `angles_list` (List[float]): Lista de ângulos de movimento.
- `max_speed` (float): Velocidade máxima do drone.

### `addVehicle(vehicle: Vehicle)`

Adiciona um veículo à simulação.

**Parâmetros:**
- `vehicle` (Vehicle): Objeto do veículo a ser adicionado.

**Lança:**
- `ValueError`: Se o ID do veículo já existir.

### `removeVehicle(vehicleId: str)`

Remove um veículo da simulação.

**Parâmetros:**
- `vehicleId` (str): ID do veículo a ser removido.

**Lança:**
- `ValueError`: Se o ID do veículo não existir.

### `changeLegend(oldLegend: str, newLegend: str)`

Altera a legenda de um tipo de veículo.

**Parâmetros:**
- `oldLegend` (str): Legenda antiga.
- `newLegend` (str): Nova legenda.

**Lança:**
- `ValueError`: Se a legenda antiga não existir.

### `print_all_vehicle_info(vehicle_id: str)`

Imprime todas as informações de um veículo.

**Parâmetros:**
- `vehicle_id` (str): ID do veículo.

**Lança:**
- `ValueError`: Se o ID do veículo não for encontrado.

### `get_vehicle_dict(vehicle_id: str) -> List[Optional[Dict]]`

Retorna um dicionário com todas as informações de um veículo.

**Parâmetros:**
- `vehicle_id` (str): ID do veículo.

**Retorna:**
- `List[Optional[Dict]]`: Lista de dicionários com informações de cada intervalo de tempo.

**Lança:**
- `ValueError`: Se o ID do veículo não for encontrado.

### `vector_with_all_coordinates() -> List[List[Tuple[float, float]]]`

Retorna um vetor com todas as coordenadas dos veículos.

**Retorna:**
- `List[List[Tuple[float, float]]]`: Lista de listas de coordenadas (latitude, longitude).