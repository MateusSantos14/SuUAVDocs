# Funções de Geração de Vídeo com Coordenadas Vetoriais

Este módulo contém funções para gerar vídeos animados com base nas coordenadas de veículos e criar GeoDataFrames otimizados para visualização em mapas.

---

## Função `_create_dataframe_optimized`

A função `_create_dataframe_optimized` cria um `GeoDataFrame` otimizado a partir de coordenadas vetoriais ou limites de mapa.

### Parâmetros

- `vector_coordinates` (`List[List[List[Tuple[float, float]]]`): Lista de coordenadas dos veículos.
- `limits_map` (`Union[List[Tuple[float, float]], int]`): Limites do mapa. Se for `0`, os limites serão calculados automaticamente.

### Retorno

- `Tuple[gpd.GeoDataFrame, float]`: Retorna um `GeoDataFrame` contendo o polígono do cenário e a proporção entre largura e altura.

---

## Função `generate_video_with_vector_coordinates_image`

A função `generate_video_with_vector_coordinates_image` gera um vídeo animado com base nas coordenadas vetoriais dos veículos.

### Parâmetros

- `vector_coordinates` (`List[List[List[Tuple[float, float]]]`): Lista de coordenadas dos veículos.
- `directory_video` (`str`): Caminho onde o vídeo será salvo.
- `names` (`List[str]`): Nomes dos veículos para a legenda. (Padrão: lista vazia)
- `limits_map` (`Union[List[Tuple[float, float]], int]`): Limites do mapa. Se for `0`, os limites serão calculados automaticamente. (Padrão: `0`)
- `only_vants` (`int`): Se for `1`, considera apenas os UAVs (veículos aéreos não tripulados). (Padrão: `0`)

### Descrição

1. Se `only_vants` for `1`, apenas os UAVs serão considerados.
2. Cria o cenário com um `GeoDataFrame` e calcula sua proporção.
3. Define uma lista de cores para os veículos e atribui uma cor específica para cada tipo.
4. Plota o cenário e adiciona uma legenda para os veículos.
5. Adiciona um mapa de fundo usando o provedor OpenStreetMap.
6. Pré-computa as coordenadas para todos os frames e configura a animação.
7. Salva o vídeo usando o `ffmpeg`.

### Função Interna `update`

Atualiza a posição dos pontos no gráfico para cada frame da animação.

- `frame` (`int`): Número do frame atual.

**Retorna:** `Tuple[PathCollection]` com os pontos atualizados.

---

## Dependências

Este módulo utiliza as seguintes bibliotecas:

- `numpy`: Processamento de coordenadas vetoriais.
- `matplotlib.pyplot`: Geração de gráficos e vídeos.
- `matplotlib.animation.FuncAnimation`: Animação dos gráficos.
- `contextily`: Adição de mapas de fundo.
- `shapely.geometry.Polygon`: Criação de polígonos de limite para o mapa.
- `geopandas`: Criação de `GeoDataFrames` para visualização geográfica.
- `typing`: Definição de tipos para os parâmetros e retornos.
- `matplotlib.collections.PathCollection`: Manipulação de coleções de caminhos no gráfico.
