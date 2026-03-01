# Tipologias de Consumo e Acesso à Internet no Brasil

**Projeto 9 — FACOM32701 – Ciência de Dados II**  
**Universidade Federal de Uberlândia**

---

## Integrantes
- Arthur Rodrigues Cândido
- Lucas Mendes Lacerda
- Yuri Ferreira Machado

---
### Fonte de Dados
- **PNAD Contínua TIC 2024** - 4º Trimestre (IBGE)
- Formato: Arquivo de largura fixa (`.txt` compactado em `.zip`)
- Download direto: https://ftp.ibge.gov.br/Trabalho_e_Rendimento/Pesquisa_Nacional_por_Amostra_de_Domicilios_continua/Anual/Microdados/Trimestre/Trimestre_4/Dados/PNADC_2024_trimestre4_20251014.zip

---

## ⚙️ Pré-requisitos

- **Python 3.8+**
- **pip** (gerenciador de pacotes Python)
- **Jupyter Notebook** ou **Jupyter Lab** (para executar o notebook)
- **~6GB de espaço em disco** (3GB compactado + 3GB descompactado)
- Arquivo de dados: `PNADC_2024_trimestre4_20251014.zip` (baixar do link acima, precisa descompactar)

---

##  Como Reproduzir o Projeto

### 1. Clonar/Baixar o Repositório
```bash
# Ou simplesmente extrair os arquivos do projeto
cd "Tipologias_de_Consumo_e_Acesso_a_Internet_no_Brasil"
```

### 2. Instalar Dependências (em lote)
```bash
# Instalar todos os pacotes necessários de uma vez
python -m pip install -r requirements.txt 
```
### 3. Preparar os Dados

O arquivo de microdados está compactado em formato `.zip` dentro do repositório. Você precisa **descompactá-lo** antes de executar o notebook.

> ⚠️ **Aviso:** O arquivo descompactado tem ~3GB. Certifique-se de ter espaço em disco disponível!

### 4. Executar o Notebook

Existem várias opções para executar o notebook. Escolha a que mais se adequa:

#### **Opção A: VS Code** 
1. Abra o VS Code
2. Abra a pasta do projeto: `File → Open Folder`
3. Instale a extensão "Jupyter" (Microsoft) se não tiver
4. Clique no arquivo `Projeto9_PNAD_TIC_2024_A_L_Y.ipynb`
5. Selecione um kernel Python (será solicitado)
6. Execute as células clicando no ícone ▶️ ao lado de cada célula

#### **Opção B: Google Colab** (Sem instalação local)
1. Acesse https://colab.research.google.com
2. Clique em `File → Open notebook`
3. Selecione a aba `Upload`
4. Arraste ou selecione o arquivo `Projeto9_PNAD_TIC_2024_A_L_Y.ipynb`
5. Na primeira célula, execute para descompactar (se subiu o .zip):
```python
# Se tiver feito upload do .zip, descompacte primeiro
import zipfile
import os

# Verificar e descompactar se necessário
if os.path.exists('PNADC_2024_trimestre4_20251014.zip'):
    with zipfile.ZipFile('PNADC_2024_trimestre4_20251014.zip', 'r') as zip_ref:
        zip_ref.extractall('.')
    print("✅ Arquivo descompactado!")

# Instalar dependências
!pip install -q pandas numpy matplotlib seaborn scikit-learn scipy jupyter
```

> **Nota (Colab):** Se não tiver upload do arquivo `PNADC_2024_trimestre4.txt` ou `.zip`, faça upload manualmente:
```python
from google.colab import files
uploaded = files.upload()  # Selecione o arquivo .zip ou .txt
```

##  Dependências

| Pacote | Versão | Uso |
|--------|--------|-----|
| **pandas** | ≥1.3.0 | Manipulação e análise de dados |
| **numpy** | ≥1.20.0 | Operações numéricas |
| **matplotlib** | ≥3.3.0 | Visualizações básicas |
| **seaborn** | ≥0.11.0 | Visualizações estatísticas avançadas |
| **scikit-learn** | ≥0.24.0 | Machine Learning (clustering, PCA, t-SNE, métricas) |
| **scipy** | ≥1.5.0 | Clustering hierárquico |
| **jupyter** | ≥1.0.0 | Ambiente Jupyter Notebook |

---

##  Troubleshooting

### Problema: Arquivo de dados não encontrado após descompactar
**Solução:** Verifique:
1. Se `PNADC_2024_trimestre4.txt` existe: `ls -lh PNADC_2024_trimestre4.txt`
2. Se está no diretório correto (raiz do projeto)
3. Tente descompactar novamente

### Problema: Sem espaço em disco para descompactar
**Solução:**
- O arquivo precisa de ~6GB total (3GB + 3GB)
- Libere espaço ou use outro disco
- Se usar um SSD com espaço limitado, considere usar um disco externo

### Problema: Erro ao selecionar kernel no VS Code
**Solução:** 
1. Certifique-se de que o Python está instalado
2. Abra o terminal integrado (Ctrl + `)
3. Execute: `pip install -r requirements.txt`
4. Reabra o VS Code

### Problema: VS Code não encontra a extensão Jupyter
**Solução:** Instale a extensão oficial da Microsoft:
1. Abra a aba Extensions (Ctrl + Shift + X)
2. Procure por "Jupyter"
3. Clique em instalar na extensão oficial da Microsoft

### Problema: `ModuleNotFoundError: No module named 'pandas'` no Colab
**Solução:** Execute na primeira célula:
```python
!pip install pandas numpy matplotlib seaborn scikit-learn
```

### Problema: Arquivo de dados não encontrado
**Solução:** Verifique se `PNADC_2024_trimestre4.txt` está no diretório correto

### Problema: Erro ao importar bibliotecas
**Solução:** Atualize o pip:
```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### Problema: No Colab, dados não encontrados
**Solução:** Upload dos dados no Colab:
```python
from google.colab import files
uploaded = files.upload()  # Selecione o arquivo PNADC_2024_trimestre4.txt
```

---

##  Estrutura de Arquivos

```
Tipologias_de_Consumo_e_Acesso_a_Internet_no_Brasil/
├── Projeto9_PNAD_TIC_2024_A_L_Y.ipynb       (Notebook principal)
├── PNADC_2024_trimestre4_20251014.zip       (Arquivo baixado do IBGE ~3GB)
├── PNADC_2024_trimestre4.txt                (Gerado após descompactar - ~3GB)
├── imagens/                                 (Pasta para salvar gráficos)
├── requirements.txt                         (Dependências do projeto)
└── README.md                                (Este arquivo)
```

> **Nota:** Após descompactar o arquivo `PNADC_2024_trimestre4_20251014.zip`, aparecerá automaticamente o `PNADC_2024_trimestre4.txt` no diretório raiz

---

## Saídas Esperadas

O notebook gera:
- **Tabelas**: Perfis de clusters, correlações, estatísticas descritivas
- **Gráficos**: Distribuições, dendrogramas, t-SNE, PCA, heatmaps
- **Métricas**: Silhueta, Davies-Bouldin, Calinski-Harabasz, ARI, NMI

---

##  Referências

- IBGE - PNAD Contínua TIC: https://www.ibge.gov.br/
- Scikit-learn Clustering: https://scikit-learn.org/stable/modules/clustering.html
- Pandas Documentation: https://pandas.pydata.org/docs/
- Matplotlib Tutorial: https://matplotlib.org/stable/contents.html

---

##  Licença

Este projeto foi desenvolvido como trabalho acadêmico para a disciplina FACOM32701 - Ciência de Dados II.

---