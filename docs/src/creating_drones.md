# Documentação do Código de Geração de Coordenadas para Drones

## Funções

### haversine_distance
Calcula a distância do círculo máximo entre dois pontos na superfície da Terra com base em suas latitudes e longitudes.

**Parâmetros:**
- `lat1 (float)`: Latitude do primeiro ponto em graus.
- `lon1 (float)`: Longitude do primeiro ponto em graus.
- `lat2 (float)`: Latitude do segundo ponto em graus.
- `lon2 (float)`: Longitude do segundo ponto em graus.

**Retorno:**
- `float`: Distância entre os dois pontos em metros.

---

### calculate_angle
Calcula o ângulo de direção entre dois pontos na superfície da Terra.

**Parâmetros:**
- `p1 (Tuple[float, float])`: Tupla contendo a latitude e longitude do primeiro ponto.
- `p2 (Tuple[float, float])`: Tupla contendo a latitude e longitude do segundo ponto.

**Retorno:**
- `float`: Ângulo de direção em radianos.

---

### limit_speed
Limita a distância entre dois pontos a um valor máximo, preservando a direção.

**Parâmetros:**
- `start_point (Tuple[float, float])`: Ponto inicial (latitude, longitude).
- `end_point (Tuple[float, float])`: Ponto final (latitude, longitude).
- `max_distance (float)`: Distância máxima permitida em metros.

**Retorno:**
- `Tuple[float, float]`: Novo ponto ajustado para não exceder a distância máxima.

---

### generate_drone_coordinates
Gera coordenadas para o drone com base nas coordenadas do veículo e na distância de offset.

**Parâmetros:**
- `vehicle_coordinates (List[Tuple[float, float]])`: Lista de coordenadas (latitude, longitude) do veículo.
- `offset_distance (float)`: Distância entre o veículo e o drone em metros.
- `max_speed (float)`: Velocidade máxima do drone em metros por segundo.
- `smoothing_factor (float)`: Fator de suavização para movimentos suaves. Valor entre 0 e 1.

**Retorno:**
- `List[Tuple[float, float, float]]`: Lista de coordenadas (latitude, longitude, velocidade) para o drone.

---

### generate_drone_coordinates_static
Gera coordenadas discretas para o drone girando em torno de um ponto específico na Terra.

**Parâmetros:**
- `point (Tuple[float, float])`: Coordenadas do centro (latitude, longitude) em graus.
- `num_samples (int)`: Número de amostras discretas a serem geradas.

**Retorno:**
- `List[Tuple[float, float, float]]`: Lista de coordenadas (latitude, longitude, velocidade) do drone.

---

### generate_generic_pattern
Gera coordenadas para um padrão de mobilidade genérico.

**Parâmetros:**
- `start_point (Tuple[float, float])`: Coordenadas iniciais (latitude, longitude).
- `distance_lists (List[float])`: Lista de distâncias a serem percorridas em cada estado.
- `angles_list (List[float])`: Lista de ângulos de movimento para cada estado.
- `num_samples (int)`: Número de amostras a serem geradas.
- `max_speed (float)`: Velocidade máxima do drone em metros por segundo.

**Retorno:**
- `List[Tuple[float, float, float]]`: Lista de coordenadas (latitude, longitude, velocidade) para o padrão de mobilidade.

---

### create_drone_static_point
Cria um drone estacionário em um ponto específico.

**Parâmetros:**
- `timesteps (int)`: Número de intervalos de tempo.
- `drone_id (str)`: Identificador do drone.
- `point (Tuple[float, float])`: Coordenadas do ponto (latitude, longitude).

**Retorno:**
- `Vehicle`: Objeto do drone com as coordenadas definidas.

---

### create_drone_following_object
Cria um drone que segue um objeto móvel.

**Parâmetros:**
- `timesteps (int)`: Número de intervalos de tempo.
- `drone_id (str)`: Identificador do drone.
- `vehicle (Vehicle)`: Objeto do veículo a ser seguido.
- `offset_distance (float)`: Distância de offset entre o drone e o veículo.
- `max_speed (float)`: Velocidade máxima do drone.

**Retorno:**
- `Vehicle`: Objeto do drone com as coordenadas definidas.

---

### create_drone_generic_pattern
Cria um drone com um padrão de mobilidade genérico.

**Parâmetros:**
- `timesteps (int)`: Número de intervalos de tempo.
- `drone_id (str)`: Identificador do drone.
- `start_point (Tuple[float, float])`: Coordenadas iniciais (latitude, longitude).
- `distance_lists (List[float])`: Lista de distâncias a serem percorridas.
- `angles_list (List[float])`: Lista de ângulos de movimento.
- `max_speed (float)`: Velocidade máxima do drone.

**Retorno:**
- `Vehicle`: Objeto do drone com as coordenadas definidas.

