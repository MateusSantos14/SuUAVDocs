# Classes Vehicle e Timestep

Este módulo contém as classes `Vehicle` e `Timestep`, que são usadas para armazenar e gerenciar informações sobre veículos e seus estados em diferentes momentos.

---

## Classe `Vehicle`

A classe `Vehicle` é projetada para armazenar e gerenciar informações de trajetória de um veículo.

### Atributos

- `_id` (`str`): Identificador único do veículo.
- `_type` (`str`): Tipo do veículo.
- `timesteps` (`Dict[int, Timestep]`): Dicionário que armazena objetos `Timestep`, indexados pelo tempo (como inteiros).

### Métodos

#### `__init__(self, id: str, type: str) -> None`

Inicializa uma nova instância da classe `Vehicle` com o ID e tipo especificados.

**Parâmetros:**
- `id` (`str`): Identificador único do veículo.
- `type` (`str`): Tipo do veículo.

---

#### `add_timestep(self, time: str, x: str, y: str, angle: str, speed: str, pos: str, lane: str, slope: str) -> None`

Adiciona um novo `Timestep` ao histórico do veículo, convertendo os valores de entrada (strings) para os tipos apropriados.

**Parâmetros:**
- `time` (`str`): Tempo do timestep.
- `x` (`str`): Coordenada x da posição do veículo.
- `y` (`str`): Coordenada y da posição do veículo.
- `angle` (`str`): Ângulo de orientação do veículo.
- `speed` (`str`): Velocidade do veículo.
- `pos` (`str`): Indicador de posição do veículo.
- `lane` (`str`): Faixa em que o veículo está.
- `slope` (`str`): Inclinação da via ou do veículo.

---

#### `get_timestep(self, time: int) -> Optional[Timestep]`

Retorna o objeto `Timestep` para um determinado tempo, se existir; caso contrário, retorna `None`.

**Parâmetros:**
- `time` (`int`): Tempo do timestep.

**Retorna:**
- `Optional[Timestep]`: Objeto `Timestep` ou `None`.

---

#### `get_timestep_dict(self, time: int) -> Optional[dict]`

Retorna uma representação em dicionário do `Timestep` para um determinado tempo, se existir; caso contrário, retorna `None`.

**Parâmetros:**
- `time` (`int`): Tempo do timestep.

**Retorna:**
- `Optional[dict]`: Dicionário com os dados do timestep ou `None`.

---

#### `print_timestep(self, time: int) -> None`

Imprime a representação em dicionário do `Timestep` para um determinado tempo, se existir.

**Parâmetros:**
- `time` (`int`): Tempo do timestep.

---

#### `is_present(self, time: int) -> bool`

Verifica se existe um `Timestep` para um determinado tempo.

**Parâmetros:**
- `time` (`int`): Tempo do timestep.

**Retorna:**
- `bool`: `True` se o timestep existir; `False` caso contrário.

---

#### `id(self) -> str`

Retorna o ID do veículo.

**Retorna:**
- `str`: ID do veículo.

---

#### `type(self) -> str`

Retorna o tipo do veículo.

**Retorna:**
- `str`: Tipo do veículo.

---

## Classe `Timestep`

A classe `Timestep` encapsula o estado de um veículo em um momento específico, detalhando sua posição, orientação e atributos de movimento.

### Atributos

- `_time` (`int`): Momento do timestep.
- `_x` (`float`): Coordenada x da posição do veículo.
- `_y` (`float`): Coordenada y da posição do veículo.
- `_angle` (`float`): Ângulo de orientação do veículo.
- `_speed` (`float`): Velocidade do veículo.
- `_pos` (`float`): Indicador de posição do veículo.
- `_lane` (`str`): Faixa em que o veículo está.
- `_slope` (`float`): Inclinação da via ou do veículo.

### Métodos

#### `__init__(self, time: int, x: float, y: float, angle: float, speed: float, pos: float, lane: str, slope: float) -> None`

Inicializa um `Timestep` com detalhes de posição, orientação e movimento.

**Parâmetros:**
- `time` (`int`): Momento do timestep.
- `x` (`float`): Coordenada x da posição do veículo.
- `y` (`float`): Coordenada y da posição do veículo.
- `angle` (`float`): Ângulo de orientação do veículo.
- `speed` (`float`): Velocidade do veículo.
- `pos` (`float`): Indicador de posição do veículo.
- `lane` (`str`): Faixa em que o veículo está.
- `slope` (`float`): Inclinação da via ou do veículo.

---

#### `time(self) -> int`

Retorna o momento do timestep.

**Retorna:**
- `int`: Momento do timestep.

---

#### `x(self) -> float`

Retorna a coordenada x da posição do veículo.

**Retorna:**
- `float`: Coordenada x.

---

#### `y(self) -> float`

Retorna a coordenada y da posição do veículo.

**Retorna:**
- `float`: Coordenada y.

---

#### `angle(self) -> float`

Retorna o ângulo de orientação do veículo.

**Retorna:**
- `float`: Ângulo de orientação.

---

#### `speed(self) -> float`

Retorna a velocidade do veículo.

**Retorna:**
- `float`: Velocidade.

---

#### `pos(self) -> float`

Retorna o indicador de posição do veículo.

**Retorna:**
- `float`: Indicador de posição.

---

#### `lane(self) -> str`

Retorna a faixa em que o veículo está.

**Retorna:**
- `str`: Faixa do veículo.

---

#### `slope(self) -> float`

Retorna a inclinação da via ou do veículo.

**Retorna:**
- `float`: Inclinação.

---

## Exemplo de Uso

Aqui está um exemplo de como usar as classes `Vehicle` e `Timestep`:

```python
# Criando um veículo
veiculo = Vehicle(id="car1", type="car")

# Adicionando um timestep
veiculo.add_timestep(time="1", x="10.5", y="20.3", angle="45.0", speed="30.0", pos="0.0", lane="left", slope="0.0")

# Obtendo um timestep
timestep = veiculo.get_timestep(time=1)
if timestep:
    print(f"Timestep encontrado: x={timestep.x()}, y={timestep.y()}")

# Verificando se um timestep existe
if veiculo.is_present(time=1):
    print("Timestep existe!")
```