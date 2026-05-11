# Projeto: Agente ThermoGrid 4.0

![Google Colab](https://img.shields.io/badge/Colab-F9AB00?style=for-the-badge&logo=googlecolab&color=525252)
![Gemini API](https://img.shields.io/badge/Gemini%20API-8E75B2?style=for-the-badge&logo=googlebard&logoColor=white)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)


### 1. Identificação do Grupo
* **Instituição:** Faculdade Engenheiro Salvador Arena (FESA)
* **Curso:** Engenharia de Controle e Automação
* **Grupo:** Grupo F
* **Integrantes:**
  * Lucas Bandeira Barbosa - RA: 062220009
  * Enzo dos Passos Santos – RA: 062220015
  * João Victor Ugolini Coelho – RA: 062220035
  * Vinicius Premero Rocha de Souza – RA: 062230044

---

### 2. Diagnóstico e Área Problema
* **Área Selecionada:** `[X]` **Smart Grid:** Eficiência Energética e Descarbonização
* **Contexto:** O sistema é focado na monitoração e visualização do comportamento térmico de componentes eletrônicos em tempo real. Utiliza visão computacional e telemetria para identificar pontos de calor (hotspots) em placas e módulos de potência.
* **Problema:** A dificuldade de correlacionar visualmente o calor gerado por componentes eletrônicos com sua carga de trabalho atual, o que muitas vezes leva a falhas catastróficas por fadiga térmica que não são detectadas por sensores de temperatura ambiente comuns.
* **Impacto:** Visualização preditiva do desgaste de componentes, permitindo identificar falhas iminentes em semicondutores, capacitores e trilhas antes que ocorra o colapso do sistema, otimizando o ciclo de vida do hardware.

---

### 3. Arquitetura Lógica e Aprendizado
O **Agente ThermoGrid 4.0** utiliza uma arquitetura híbrida para monitoramento eletrônico:

1.  **Módulo Preditivo (Etapa 2):** Uma **RNA (MLPRegressor)** analisa o histórico de dissipação térmica do componente em relação à corrente consumida, prevendo quando a temperatura ultrapassará o limite de segurança operacional (Tjunction).
2.  **Módulo de Controle (Etapa 3):** Um sistema de **Lógica Fuzzy** classifica o estado de saúde do componente (Saudável, Alerta, Crítico) cruzando a temperatura atual com a taxa de variação térmica ($\Delta T$).
3.  **Camada Interpretativa:** A **API do Gemini** traduz os mapas térmicos e dados de sensores em diagnósticos diretos (ex: "Possível fuga de corrente no componente X" ou "Sugestão: Reduzir frequência de chaveamento").

---

### 4. Modelagem PEAS
| Componente | Descrição |
| :--- | :--- |
| **Performance (P)** | Precisão na localização de hotspots, tempo de resposta para alertas de sobreaquecimento e acurácia da tendência térmica futura. |
| **Ambiente (E)** | Bancadas de teste, painéis industriais, servidores e ambientes de prototipagem eletrônica. |
| **Atuadores (A)** | Visualização via Dashboard (mapa de calor), alertas sonoros/visuais e recomendações técnicas via IA. |
| **Sensores (S)** | Câmeras térmicas infravermelhas, sensores de temperatura de contato (termistores), shunts de corrente e sensores de tensão. |

---

### 5. Monitoramento Preditivo: Abordagem RNA
A escolha por **Redes Neurais** deve-se à natureza não linear da dissipação térmica em eletrônicos. O comportamento térmico de um transistor, por exemplo, não é constante sob diferentes regimes de carga. A RNA aprende essas curvas de dissipação específicas para cada tipo de componente monitorado.

#### Desempenho do Modelo
A convergência do modelo garante que o erro na predição de temperatura seja mínimo, permitindo uma visualização "no futuro" do comportamento do componente:
<img width="859" height="473" alt="image" src="https://github.com/user-attachments/assets/3ef7a8c9-d4e7-438f-a3a9-57e5eb54171d" />

### 6. Exemplo de Execução
[INPUT]
Componente: Microcontrolador
Corrente medida: 450mA
Temperatura Atual: 45°C

[PROCESSAMENTO]
Fuzzy disponível: True
Método utilizado: Fuzzy Logic + RNA

[OUTPUT NUMÉRICO]
Índice de Risco Térmico: 0.15

[INTERPRETAÇÃO - GEMINI]
"O comportamento térmico do processador está estável. A temperatura de 45°C é considerada ideal para a carga de trabalho atual. Não foram detectados hotspots anômalos no entorno do componente."

---

### 7. Estrutura do Repositório
```text
smartgrid-fuzzy/
│
├── README.md
├── requirements.txt
├── .env.example
├── .gitignore
│
├── notebook/
│   └── ComportamentoTermico_Componentes.ipynb   
│
└── src/
    ├── __init__.py
    ├── fuzzy_logic.py     # Classificação de risco por componente
    ├── ai_interpreter.py  # Diagnóstico humanizado do hardware
    └── model_rna.py       # Predição de tendência de aquecimento
