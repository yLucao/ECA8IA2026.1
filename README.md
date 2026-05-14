# Projeto: Agente ThermoGrid 4.0

![Google Colab](https://img.shields.io/badge/Colab-F9AB00?style=for-the-badge&logo=googlecolab&color=525252)
![Gemini API](https://img.shields.io/badge/Gemini%20API-8E75B2?style=for-the-badge&logo=googlebard&logoColor=white)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)

### 🎥 Demonstração do Projeto
**[Assista ao Pitch e Demonstração da Solução (2-3 min)](INSERIR_LINK_DO_VIDEO_AQUI)**

### 🚀 Link do Protótipo
* ** [[PROTÓTIPO NO GOOGLE AI STUDIO]](https://ai.studio/apps/9ea37196-edb7-4e68-a7bb-1eb4e58e647f))
* ** [Link para acesso ao código no Google Colab](https://colab.research.google.com/drive/1sP1tMtZAtvEmjJgbNS4shjjQGOwb0xvz?usp=sharing)

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
* **Contexto:** O sistema é focado na monitoração e visualização do comportamento térmico de componentes eletrônicos em tempo real. Utiliza visão computacional e telemetria para identificar pontos de calor (hotspots), principalmente em painéis de energia.
* **Problema:** As falhas em painéis elétricos costumam evoluir de forma silenciosa e, muitas vezes, só são percebidas quando já impactam a operação. Esse cenário pode gerar sobreaquecimento, perda de eficiência, desgaste acelerado de componentes, paradas não programadas e aumento do risco à segurança. Além disso, a identificação da origem do problema nem sempre é rápida ou simples, especialmente em painéis energizados, onde o diagnóstico exige tempo, cuidado e alta exposição do operador. Na prática, isso torna a análise de anomalias mais crítica, mais lenta e mais suscetível a falhas de interpretação.
* **Impacto:** O ThermoGrid foi desenvolvido para, utilizando análise térmica, tornar a manutenção de painéis elétricos mais rápida, padronizada e assertiva. De forma geral, a proposta do aplicativo é apoiar a identificação de anomalias de temperatura com mais agilidade, reduzindo a dificuldade de inspeção, a dependência de análises demoradas e a exposição do operador durante o processo. O monitoramento é feito em tempo real, por isso, qualquer distúrbio é rapidamente detectado. A integração com inteligência artificial permite a predição de condições de risco recomendando ao operador ações de contenção antes mesmo que o problema aconteça.

---

### 3. Arquitetura Lógica e Aprendizado
O **Agente ThermoGrid 4.0** utiliza uma arquitetura híbrida para monitoramento eletrônico:

1.  **Módulo Preditivo (RNA):** Uma **Rede Neural** analisa o histórico de dissipação térmica do componente em relação à corrente consumida, prevendo quando a temperatura ultrapassará o limite de segurança operacional (Tjunction).
2.  **Módulo de Controle:** Um sistema de **Lógica Fuzzy** classifica o estado de saúde do componente (Saudável, Alerta, Crítico) cruzando a temperatura atual com a taxa de variação térmica ($\Delta T$).
3.  **Camada Interpretativa:** A **API do Gemini** traduz os mapas térmicos e dados de sensores em diagnósticos rápidos e dá sugestões ao operador (ex: Suspeita de mau contato em terminais ou degradação dielétrica interna, dado que a temperatura atual é elevada para uma carga de apenas 37%).

---

## 4. Modelagem PEAS — ThermoGrid 4.0

| Componente | Descrição |
| :--- | :--- |
| **Performance (P)** | Detectar riscos térmicos com alta precisão utilizando lógica fuzzy e rede neural preditiva (MLPRegressor), prever tendências de aquecimento futuro, minimizar falsos positivos, gerar diagnósticos inteligentes em tempo real e antecipar falhas elétricas em componentes críticos. |
| **Ambiente (E)** | Quadros Gerais de Baixa Tensão (QGBT), painéis elétricos industriais, centros de distribuição elétrica, sistemas de automação industrial, inversores de frequência, bancos de capacitores e ambientes de manutenção preditiva em instalações elétricas industriais. |
| **Atuadores (A)** | Alertas visuais simulados (“lâmpada de aviso”), exibição de relatórios preditivos no terminal, geração automática de diagnósticos técnicos via IA Gemini e recomendações operacionais para manutenção preventiva. |
| **Sensores (S)** | Sensores de temperatura térmica (simulados), sensores de carga elétrica (simulados), dados históricos de operação utilizados pela RNA, entradas monitoradas de temperatura e corrente elétrica, além de variáveis processadas pela lógica fuzzy para cálculo de risco térmico. |

---
## 5. Justificativa da Abordagem

O **ThermoGrid 4.0** utiliza uma arquitetura híbrida baseada em **Redes Neurais Artificiais (RNA)**, **Lógica Fuzzy** e **IA Generativa** para realizar monitoramento térmico inteligente e preditivo em sistemas elétricos industriais.

### Natureza do Problema

Com frequência problemas em painéis elétricos não se manifestam de forma evidente, seus efeitos só aparecem quando a operação já foi prejudicada. Quando isso acontece, podem surgir elevação excessiva de temperatura, queda no rendimento do sistema, deterioração antecipada de peças, interrupções inesperadas no processo e maior exposição a riscos de segurança. Soma-se a isso o fato de que descobrir a verdadeira causa da anomalia pode ser uma tarefa complexa, sobretudo em painéis sob tensão, já que a avaliação exige mais tempo, atenção redobrada e maior vulnerabilidade para quem executa o diagnóstico. 

### Uso da Rede Neural (RNA)

A RNA foi implementada com o modelo `MLPRegressor`, responsável por aprender padrões térmicos a partir de dados históricos.

O sistema utiliza:
- Temperatura atual;
- Percentual de carga elétrica.

Com isso, consegue prever a temperatura futura do componente e antecipar situações de superaquecimento.

Principais vantagens:
- Aprendizado automático;
- Predição de falhas;
- Melhor tomada de decisão preventiva.

### Uso da Lógica Fuzzy

A lógica fuzzy foi utilizada para interpretar os dados de forma semelhante ao raciocínio humano.

O sistema classifica:
- Temperatura: baixa, média ou alta;
- Carga: baixa, média ou alta;
- Risco: baixo, médio ou alto.

A partir dessas regras, o sistema calcula o nível de risco térmico do equipamento.
---
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

<img width="418" height="191" alt="image" src="https://github.com/user-attachments/assets/13c6208f-c3ab-419f-9fa1-da5ac0b1c8d5" />


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
