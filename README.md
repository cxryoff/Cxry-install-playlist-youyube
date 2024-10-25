# Cxry-install-playlist-youyube

Interface gráfica para a ferramenta de linha de comando [Cxry](https://github.com/cxryoffl/cxry-install-playlist) com personalização predefinida.

## Captura de tela

![](https://github.com/user-attachments/assets/8e758f07-3cdb-477c-91ab-0ee20c2443e8)

## Uso

Há duas maneiras de começar, dependendo de sua preferência e sistema:

* [`Portátil`](#portátil) ~ *Windows*
* [`Manual`](#manual) ~ *Independente de plataforma*

### Portátil

Baixe a versão portátil mais recente na seção [releases](https://github.com/cxryoffl/cxry-install-playlist/releases/latest).
Este é um arquivo ZIP contendo os arquivos do programa e todas as dependências necessárias.

*Todos os lançamentos são criados e lançados usando o GitHub Workflow*

### Manual

Você **deve** ter o [Python](https://www.python.org/downloads/) 3.9+ instalado.

```bash
git clone https://github.com/cxryoffl/cxry-install-playlist youyube
cd cxry-install-playlist youyube
pip install -r requirements.txt
cd app
python app.py
```

## Personalização de predefinições

**Observação:** todos os arquivos mencionados abaixo estão localizados no diretório raiz do programa.

Se você deseja criar suas próprias predefinições ou modificar as existentes, você está no lugar certo. Todas as opções de personalização podem ser encontradas no arquivo `config.toml`.

### Campos disponíveis

Para definir uma predefinição, o nome da seção deve começar com `presets.`. Abaixo estão os campos que você pode usar para personalizar suas predefinições:

- **args** (obrigatório): Este campo pode ser fornecido como uma string ou uma lista. Os argumentos especificados aqui serão adicionados aos argumentos [base](https://github.com/cxryoffl/cxry-install-playlist/blob/main/app/worker.py#L67) `yt-dlp`. Portanto, apenas o formato e outras opções relevantes para download devem ser especificados.

- **path** (opcional): Este campo de string permite que você especifique o caminho de saída. Se este campo for omitido, ele deve ser incluído no campo `args`.

- **filename** (opcional): Este campo de string permite que você defina a convenção de nomenclatura. Se este campo for omitido, ele deve ser especificado no campo `args`.

- **sponsorblock** (opcional): Este campo inteiro permite que você defina a funcionalidade SponsorBlock. `0` para desabilitar ou `1` para remover e `2` para marcar.

- **metadata** (opcional): Este campo booleano determina se deve incluir metadados.

- **subtitles** (opcional): Este campo booleano determina se deve incluir legendas.

- **thumbnail** (opcional): Este campo booleano determina se deve incluir miniaturas.

Abaixo, um exemplo de como adicionar o formato `wav`, você notará que deixei de fora `subtitles` e `thumbnail`, pois não são aplicáveis ​​a este formato.

```toml
[presets.wav]
args = "--extract-audio --audio-format wav --audio-quality 0"
path = ""
filename = "%(title)s.%(ext)s"
sponsorblock = 0
metadata = false
```

Tente você mesmo colando-o no final do seu arquivo `config.toml`! Você verá que todos os campos não incluídos na predefinição serão desabilitados na GUI. Se você encontrar algum problema com sua predefinição, verifique o arquivo `debug.log` para obter detalhes.