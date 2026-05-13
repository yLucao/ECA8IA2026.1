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
### 5. Justificativa da Abordagem

Para o desenvolvimento do núcleo de inteligência do **Agente ThermoGrid 4.0**, foi selecionada a abordagem baseada em **Redes Neurais Artificiais (RNA)** integrada com **Lógica Fuzzy**, formando uma arquitetura híbrida capaz de realizar monitoramento térmico preditivo em componentes eletrônicos.

#### **Por que esta abordagem foi escolhida?**

* **Natureza do Problema:**  
O monitoramento térmico de componentes eletrônicos envolve fenômenos altamente não lineares, nos quais pequenas variações de corrente, tensão ou carga computacional podem gerar aumentos significativos de temperatura. Além disso, muitos processos de degradação térmica não são perceptíveis por sensores convencionais de temperatura ambiente, exigindo uma solução capaz de identificar padrões complexos e tendências futuras de aquecimento.

* **Capacidade de Generalização:**  
A utilização da **RNA (MLPRegressor)** foi escolhida devido à sua capacidade de aprender com dados históricos de dissipação térmica e identificar correlações complexas entre corrente elétrica, temperatura e comportamento operacional do hardware. Dessa forma, o sistema consegue prever tendências de superaquecimento antes que ocorram falhas críticas em semicondutores, trilhas e módulos de potência.

* **Interpretação Inteligente com Lógica Fuzzy:**  
A abordagem fuzzy complementa a RNA ao transformar dados numéricos em classificações interpretáveis, como “Saudável”, “Alerta” e “Crítico”. Isso permite que o sistema tome decisões mais próximas da lógica humana, considerando simultaneamente a temperatura atual e a taxa de variação térmica do componente.

* **Escalabilidade:**  
A arquitetura desenvolvida permite a integração futura de novos sensores e variáveis de entrada, como vibração, consumo energético, frequência de chaveamento e umidade, sem necessidade de reconstrução completa do sistema. Isso torna o projeto adaptável para aplicações industriais maiores dentro do contexto de Smart Grids e manutenção preditiva.

* **Integração com IA Generativa:**  
A utilização da API Gemini adiciona uma camada interpretativa ao sistema, permitindo transformar dados técnicos e mapas térmicos em diagnósticos compreensíveis e recomendações operacionais automáticas, facilitando a tomada de decisão por operadores e equipes de manutenção.

### 6. Evidências Visuais e Desempenho
A convergência do modelo garante que o erro na predição de temperatura seja mínimo, permitindo uma visualização "no futuro" do comportamento do componente:
<img width="859" height="473" alt="image" src="https://github.com/user-attachments/assets/3ef7a8c9-d4e7-438f-a3a9-57e5eb54171d" />

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
├── README.md                  # Documentação principal do projeto
├── requirements.txt           # Dependências do sistema
├── .env.example               # Exemplo de configuração da API Gemini
├── .gitignore                 # Arquivos ignorados no versionamento
│
├── assets/
│   └── images/                # Gráficos, mapas térmicos, diagramas e logs
│
├── data/                      # Datasets e arquivos de entrada utilizados nos testes
│
├── notebooks/
│   └── SmartGrid.ipynb        # Notebook principal executável no Google Colab
│
└── src/
    ├── __init__.py
    ├── fuzzy_logic.py         # Sistema Fuzzy para classificação térmica
    ├── ai_interpreter.py      # Interpretação inteligente via Gemini API
    └── model_rna.py           # Predição térmica utilizando MLPRegressor
```

---

### 8. Instruções para Execução

1. Clone o repositório do projeto:
   ```bash
   git clone [URL_DO_REPOSITORIO]
   ```

2. Acesse a pasta do projeto:
   ```bash
   cd smartgrid-fuzzy
   ```

3. Abra o notebook:
   ```text
   /notebooks/SmartGrid.ipynb
   ```

4. Instale as dependências:
   ```bash
   !pip install scikit-fuzzy
   !pip install google-genai
   !pip install matplotlib scikit-learn
   ```

5. Configure a API Gemini:
   ```python
   genai.configure(api_key=os.getenv("GEMINI_API_KEY"))
   ```

---

## 9. Apêndice de IA

Relato sobre o suporte de ferramentas de Inteligência Artificial Generativa no desenvolvimento do projeto **Agente ThermoGrid 4.0**.

### Ferramentas
- ChatGPT (OpenAI)
- Gemini API (Google AI)

### Aplicação
As ferramentas de IA generativa foram utilizadas como suporte técnico e acadêmico durante o desenvolvimento do projeto, auxiliando em:

- Estruturação e organização do código em Python;
- Apoio na construção da arquitetura do agente inteligente;
- Revisão textual e padronização da documentação técnica;
- Sugestões para modelagem da lógica Fuzzy e da RNA (MLPRegressor);
- Organização da estrutura do repositório GitHub;
- Geração e refinamento de descrições técnicas do sistema;
- Apoio na interpretação dos resultados térmicos e métricas do modelo;
- Sugestões de melhoria para o pipeline de monitoramento preditivo.

---
© 2026 - Agente ThermoGrid 4.0 - Faculdade Engenheiro Salvador Arena
