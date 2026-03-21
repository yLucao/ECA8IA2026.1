# Projeto: Agente ThermoGrid 4.0.
### 1. Identificação do Grupo
* **Instituição:** Fundação Salvador Arena
* **Curso:** Engenharia de Controle e Automação
* **Grupo:** Grupo F
* **Integrantes:**
* Lucas Bandeira Barbosa - RA: 062220009
* Enzo dos Passos Santos – RA: 062220015
* João Victor Ugolini Coelho – RA: 062220035
* Vinicius Premero Rocha de Souza – RA: 062230044


---

### 2. Área Problema Selecionada
Selecione a trilha tecnológica do projeto (marque com um [x]):
* [ ] **Saúde 4.0:** Robótica Assistiva (Controladores Inteligentes/Fuzzy)
* [X] **Smart Grid:** Eficiência Energética e Descarbonização
* [ ] **Agtech:** Automação de Precisão e Visão Computacional
* [ ] **Logística Autônoma:** Coordenação de AGVs e Otimização de Rotas

---

### 3. Diagnóstico e Definição do Agente
Nesta seção, descrevemos o cenário de atuação e a modelagem do agente inteligente.

* **Contexto:** O projeto integra-se ao ecossistema de Smart Grid Industrial, focado no monitoramento preditivo de ativos elétricos. Atualmente, a análise de eficiência térmica é manual, lenta e subjetiva, dificultando a integração de dados em tempo real para o gerenciamento de carga.
* **Problema:** Falhas térmicas em componentes elétricos geram resistência excessiva, causando desperdício de energia (perdas por calor) e picos de consumo inesperados. A análise manual não permite uma resposta rápida para a otimização do consumo em plantas complexas.
* **Impacto:** O agente automatiza a varredura termográfica, permitindo a identificação imediata de perdas energéticas. Isso reduz a pegada de carbono, otimiza o gerenciamento de carga em tempo real e evita paradas críticas, alinhando a manutenção à eficiência energética do Smart Grid.

#### Modelagem PEAS (Agente Inteligente)
| Componente | Descrição |
| :--- | :--- |
| **Performance (P)** | Maximizar a precisão na detecção de anomalias; Minimizar perdas energéticas por dissipação de calor; Reduzir o tempo de resposta em diagnósticos; Otimizar o balanceamento de carga baseado na saúde dos ativos.|
| **Ambiente (E)** | Painéis elétricos industriais, sistemas de distribuição de energia em Smart Grids, plantas industriais complexas.|
| **Atuadores (A)** | Geração de laudos automatizados, alertas de eficiência energética, sinalização para algoritmos de gerenciamento de carga sobre a necessidade de redistribuição de energia. |
| **Sensores (S)** | Câmera termográfica (via interface YOLOv8), sensores de consumo (Dataset Steel Industry), logs de temperatura por componente. |

---

### 4. Arquitetura de Dados e IA
Definição das fontes de dados e da inteligência por trás da solução.

* **Origem dos Dados:** Steel Industry Energy Consumption Dataset e imagens termográficas rotuladas via Roboflow.
* **Lógica de IA:** Visão Computacional (YOLOv8): Para identificação de componentes e detecção de pontos quentes em imagens térmicas. Machine Learning (Redes Neurais/Scikit-learn): Para análise de padrões de consumo e predição de carga energética.
* **Justificativa:** A integração da Visão Computacional com algoritmos de busca permite transformar a imagem térmica em um dado acionável. Isso automatiza processos anteriormente subjetivos, otimiza o consumo de energia em plantas industriais complexas e reduz diretamente a pegada de carbono, conforme os requisitos de eficiência do Smart Grid.
---

### 5. Plano de Tratamento de Dados (ETL)
O fluxo de processamento dos dados segue estas etapas:
1. **Extração:** Leitura do dataset de consumo e ingestão de imagens térmicas brutas das pastas locais ou Roboflow.
2. **Transformação:** Limpeza de ruídos e normalização dos dados de consumo; redimensionamento e rotulação de imagens para o formato YOLO. Cálculo de variáveis de "Eficiência de Perda Térmica" (relacionando temperatura detectada vs. carga consumida).
3. **Carga:** Armazenamento dos modelos (.pt para visão e .pkl para heurísticas) na pasta /models.
---

### 6. Estrutura do Repositório
Organização simplificada para o Milestone 1:
* `/data`: Dados brutos e processados do setor metalúrgico.
* `/images`: Armazena as imagens térmicas originais e as rotuladas pelo Roboflow.
* `/models`: Pesos do YOLOv8 e scripts de lógica heurística.
* `/notebooks`: Análise exploratória e prototipagem dos modelos de visão e energia.
* `/scripts`: Scripts Python para ETL, treinamento e detecção de anomalias em tempo real.
* `requirements.txt`: Bibliotecas (YOLOv8, OpenCV, Pandas, Scikit-learn, PyTorch/TensorFlow).
* `README.md`: Documentação técnica do Agente ThermoGrid 4.0.
---

### 7. Instruções para Execução
Para reproduzir o ambiente e testar o diagnóstico:
1. Clone este repositório.
2. Instale as dependências:
   ```bash
   pip install -r requirements.txt
   python scripts/etl.py
   python scripts/train_model.py
   python scripts/detect_thermal_anomaly.py

   # Bibliotecas de Visão Computacional
