# IAProjects
Projeto Prático: Manutenção Preditiva de Portas de elevador (IoT + Small Data + IA)
# Manutenção Preditiva em Portas de Elevador (IoT + IA + MLOps)

Este repositório contém a solução desenvolvida para a disciplina **Internet das Coisas e Aplicações de IA (Big Data)**. O projeto consiste em um pipeline completo (End-to-End) de manutenção preditiva industrial focado no monitoramento e previsão de falhas em portas de elevador.

## 📌 Sobre o Projeto
As portas de elevador passam por milhares de ciclos diários. Falhas nesses sistemas causam paralisações indesejadas e riscos à segurança. Nossa solução simula dados de telemetria de sensores industriais e utiliza Machine Learning para prever o momento exato em que a manutenção preventiva deve ser realizada, evitando falhas catastróficas.

### 🛠️ Pilares do Projeto
1. **IoT**: Simulação de sensores de temperatura do motor, vibração física, tempo de ciclo, consumo de corrente e atraso nos contatos de segurança.
2. **Big Data / Tratamento de Sinais**: Implementação de Filtro de Média Móvel (Rolling Filter) e tratamento de outliers por Z-Score Móvel Adaptativo para lidar com séries temporais não-estacionárias.
3. **Inteligência Artificial (IA)**: Modelo não-supervisionado de detecção de anomalias usando o algoritmo **Isolation Forest**.
4. **MLOps**: Monitoramento ativo de desvio de dados (*Data Drift*) utilizando o Índice de Estabilidade Populacional (**PSI**) para disparo automático de retreinamento do modelo.
5. **Regras de Negócio**: Filtro de persistência temporal para eliminação de falsos positivos operacionais e mapeamento de zonas de divergência crítica (*Hot-Zones*).

---

## 📊 Resultados Obtidos
* **Detecção Adaptativa de Outliers**: Filtro de ruídos de alta frequência sem distorcer o desgaste natural e real dos componentes físicos.
* **Pipeline MLOps Ativo**: Identificação ágil de *Data Drift* sob cenários de falhas repentinas (PSIs de sensores atingindo limites acima de `1.5` contra limite padrão de `0.25`), forçando a recalibração imediata do modelo.
* **Otimização de Limiar**: Varredura refinada que estabeleceu o limiar ótimo de decisão em `-0.4894`, obtendo um **F1-Score de 47.68%** na classe de manutenção em ambiente hostil de produção.
* **Controle de Persistência**: A aplicação de regras de negócio (limiar de ativação apenas com persistência de anomalias) garantiu uma **Acurácia Final de 72.87%** no sistema real em produção, blindando a operação contra alarmes falsos de oscilações elétricas rápidas.

---

## 📂 Estrutura do Notebook
O código está estruturado nas seguintes etapas sequenciais:
* **Bloco 1**: Configuração e Importação de Bibliotecas
* **Bloco 2**: Simulação dos Dados de Operação da Porta do Elevador
* **Bloco 3**: Processamento de dados e Tratamento de Ruídos
* **Bloco 4**: Análise Exploratória e Visualização dos Dados
* **Bloco 5**: Aplicação de Inteligência Artificial para Predição de Manutenção (Isolation Forest)
* **Bloco 6**: Pipeline Unificado de Produção: Ingestão de Dados e MLOps (PSI & Retreinamento)
* **Bloco 7**: Dashboard Gráfico Final de Tomada de Decisão
* **Bloco 8**: Conclusões e Trabalhos Futuros

---

## 🚀 Como Executar o Projeto

### Pré-requisitos
Você precisará do Python 3.8+ instalado ou utilizar diretamente o Google Colab.

## # Executando
Abra o arquivo .ipynb no Jupyter Notebook ou Google Colab.
Execute sequencialmente as células do Bloco 1 ao Bloco 7.
A base de dados SQLite local telemetria_producao.db e o modelo serializado modelo_ia_producao.pkl serão gerados automaticamente no seu diretório.

### Instalação de Dependências
Se for rodar localmente, instale as bibliotecas necessárias:
```bash
pip install numpy pandas scikit-learn matplotlib seaborn joblib sqlite3
