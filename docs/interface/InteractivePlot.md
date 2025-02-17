# Documentação do Módulo InteractivePlot

O módulo `InteractivePlot` permite a criação de uma interface gráfica interativa para selecionar pontos em um mapa e gerar um arquivo de configuração baseado nos pontos selecionados. 

## Requisitos

Para utilizar este módulo, é necessário instalar as seguintes bibliotecas:

- `matplotlib`
- `xml.etree.ElementTree`
- `contextily`
- `shapely`
- `geopandas`
- `configparser`

## Utilização

### Classe `InteractivePlot`

A classe `InteractivePlot` é a principal classe do módulo. Ela é responsável por criar a interface gráfica e gerar o arquivo de configuração.

#### Métodos

- **`__init__(self, xml_file)`**: Inicializa a classe com o caminho do arquivo XML contendo as coordenadas dos veículos.
- **`extract_coordinates(self, xml_file)`**: Extrai as coordenadas dos veículos do arquivo XML.
- **`on_mouse_move(self, event)`**: Atualiza as coordenadas exibidas na interface conforme o movimento do mouse.
- **`on_click(self, event)`**: Adiciona um ponto ao mapa quando o usuário clica em uma área válida.
- **`on_confirm(self, event)`**: Fecha a interface gráfica quando o botão de confirmação é clicado.
- **`on_pattern_select(self, label)`**: Atualiza o padrão selecionado com base na escolha do usuário.
- **`generate_config(self)`**: Gera um arquivo de configuração (`config.ini`) com base nos pontos selecionados.
- **`show(self)`**: Exibe a interface gráfica interativa.

### Função `run(path)`

A função `run(path)` é a função principal para executar a interface gráfica e gerar o arquivo de configuração.

#### Parâmetros

- **`path`**: Caminho do arquivo XML.

### Exemplo de Uso

```python
from interactive_plot import run

# Caminho do arquivo XML
xml_file = "caminho/para/seu/arquivo.xml"

# Executa a interface gráfica e gera o arquivo de configuração
run(xml_file)