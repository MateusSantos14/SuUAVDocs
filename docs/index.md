# SuUAV - Documentação

Bem-vindo à documentação do **SuUAV**, uma ferramenta para construção de cenários de mobilidade com UAVs (Veículos Aéreos Não Tripulados). Esta ferramenta facilita a integração de UAVs em simulações de tráfego geradas pelo SUMO, permitindo a geração de cenários complexos e a visualização dos resultados por meio de vídeos.


## Instalação de dependencias no Linux
Devido ao gerenciador de pacotes do linux, é possível instalar a ferramenta pelo terminal.
```
sudo apt install python pip ffmpeg
```

## Instalação

Para utilizar o **SuUAV**, siga os passos abaixo:

1. **Clone o repositório**:

    ```
    git clone https://github.com/MateusSantos14/SuUAV
    cd SuUAV
    ```

2. **Crie um ambiente virtual e instale as dependências**:

    Certifique-se de ter o **Python 3.11.4** e o pip estão instalados. Em seguida, instale as dependências necessárias:
    ```
    python -m venv .venv
    source .venv/bin/activate
    pip install -r requirements.txt
    ```

## Depêndencias

- Python
- pip
- ffmpeg

Caso não consiga instalar as depêndencias pelo terminal,é possível instalar nos respectivos sites das organizações



## Uso Básico

O **SuUAV** pode ser executado com dois comandos principais: `--setup` e `--run`.

### Configuração Inicial (`--setup`)

O comando `--setup` abre uma interface interativa para configurar os pontos iniciais dos UAVs no mapa. Para usar:

```
python SuUAV.py --setup -i caminho/do/arquivo_trace.xml
-i ou --input: Caminho para o arquivo de trace .xml.
```
### Execução da Simulação (--run)
O comando --run executa a simulação com base no arquivo de configuração fornecido. Para usar:

```
python SuUAV.py --run -i caminho/do/arquivo_de_configuracao.ini
-i ou --input: Caminho para o arquivo de configuração .ini.
```

### Exemplo de execução

Para testar a aplicação funcionando, rode o comando abaixo:

```
python SuUAV.py --setup -i example.xml
```

Escolha os UAVs que deseja adicionar, e clique em confirmar

Em seguida, rode o comando e aguarde o vídeo ser gerado:

```
python SuUAV.py --setup -i example.ini
```

Após isso, será gerado o vídeo example_video.mp4 e o trace exampleUAV.xml
