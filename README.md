# PACV — Copresença acústica em CPS

Reprodução computacional dos experimentos disponíveis para o **Capítulo 5 — Autenticação de Copresença Acústica em Sistemas Ciberfísicos** da tese *Explorando Propriedades Acústicas na Proteção de Dispositivos Ciberfísicos*.

O estudo passivo compara áudio capturado por dois dispositivos em dois veículos. Os pares são organizados em GP-SS (mesma sessão), FP-SV (sessões distintas do mesmo veículo) e FP-DV (veículos diferentes). São extraídos vetores de 126 dimensões por dispositivo e 505 dimensões por par, utilizados na comparação dos verificadores BASE, AE++ e fusão.

## Arquivos

- [`PACV_Copresenca_Acustica_Capitulo5.ipynb`](PACV_Copresenca_Acustica_Capitulo5.ipynb): código, explicações e resultados calculados.
- `requirements.txt`: dependências do ambiente de reprodução.
- `.gitignore`: exclusão de dados, caches, modelos treinados e saídas locais.

## Executar

Use **Python 3.9**, compatível com o TensorFlow 2.13.1 da execução original:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
python -m ipykernel install --user --name pacv-capitulo5 --display-name "PACV — Capítulo 5"
python -m jupyterlab
```

No Windows, ative o ambiente com `.venv\Scripts\activate`. Selecione o kernel **PACV — Capítulo 5**, abra o notebook e execute **Restart Kernel and Run All Cells**.

Disponibilize os 112 WAV originais em `data/raw/`, preservando as pastas dos veículos, das capturas e dos aparelhos:

```text
data/raw/
├── Veículo City/
│   └── CapturaNN/
│       ├── Celular Preto/.../*.wav
│       └── Celular Rosa/.../*.wav
└── Veiculo Civic/
    └── CaptureNN/
        ├── Celular Preto/.../*.wav
        └── Celular Rosa/.../*.wav
```

O identificador de experimento é `Experimento6`. O Prover é identificado por `preto` e o Verifier por `rosa`. Nomes e subdiretórios de aquisição devem ser preservados; JSON de telemetria não são necessários. Baixe os arquivos sob demanda antes da execução. A leitura, o alinhamento e a extração integral podem levar bastante tempo; caches por par evitam repetir o processamento dos mesmos dados.

Tabelas, curvas, escores contínuos e modelos são gerados em `results/`. Caches ficam em `data/derived/` e `.cache/`. Esses diretórios permanecem locais.

## Correspondência metodológica

A versão conserva o procedimento que produziu os resultados do notebook original. Ele não implementa a separação independente por sessões descrita na tese e contém diferenças na padronização, no alinhamento e na arquitetura do AE++. Essas diferenças e a comparação numérica estão registradas nas seções correspondentes do notebook. Duas execuções completas reproduziram as mesmas métricas neste ambiente. Os resultados principais do BASE-mahalanobis coincidem com os publicados; AE++ e fusão apresentam as variações quantificadas no notebook. Os valores publicados são referências explícitas, não saídas substitutas da execução.

## Dataset

O dataset será disponibilizado por meio de uma publicação científica associada. Enquanto isso, pesquisadores interessados podem solicitar acesso diretamente ao autor pelos canais acadêmicos ou de correspondência da publicação. Os áudios e a telemetria não integram este repositório.
