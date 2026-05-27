# Projeto: Agente ThermoGrid 4.0

![Google Colab](https://img.shields.io/badge/Colab-F9AB00?style=for-the-badge&logo=googlecolab&color=525252)
![Gemini API](https://img.shields.io/badge/Gemini%20API-8E75B2?style=for-the-badge&logo=googlebard&logoColor=white)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)

### Demonstração do Projeto
**[Assista ao Pitch e Demonstração da Solução](https://youtu.be/6lf67Dy74aE)**

### Link do Protótipo
*  [PROTÓTIPO NO GOOGLE AI STUDIO](https://ai.studio/apps/bd2b0bae-a07b-4e41-a177-541e3f3b4c48?fullscreenApplet=true)

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
<img width="4060" height="7183" alt="Untitled diagram-2026-05-27-131842" src="https://github.com/user-attachments/assets/aa6d7978-14ba-4d91-88ba-4f5148cb2492" />

O Agente ThermoGrid 4.0 utiliza uma arquitetura híbrida para monitoramento e diagnóstico preditivo:
1.	Módulo Preditivo (RNA): Uma Rede Neural Artificial (MLPRegressor) analisa o histórico das variáveis de entrada para calcular a tendência térmica, estimando a temperatura futura do componente.
2.	Módulo de Controle (Lógica Fuzzy): Sistema especialista que cruza os dados de Temperatura (Baixa, Média, Alta) e Carga (Baixa, Média, Alta) para inferir o nível de Risco (Baixo, Médio, Alto). O cálculo avalia tanto o cenário presente quanto o preditivo, acionando um alerta visual (lâmpada) caso o risco futuro ultrapasse o valor permitido.
3.	Camada Interpretativa (IA Generativa): A API do Gemini 3.1 Flash-Lite consome os dados dos sensores e as saídas fuzzy para gerar um diagnóstico textual direto para o operador, estruturado rigidamente em: Estado da Instalação, Diagnóstico Rápido e Ação Imediata.

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

## 6. Pipeline ETL
<img width="8192" height="1884" alt="image" src="https://github.com/user-attachments/assets/42926f38-2380-4008-860d-67fc23f577d4" />

---
## 7. Evidências Visuais e Desempenho

A convergência do modelo garante que o erro na predição de temperatura seja mínimo, permitindo uma visualização "no futuro" do comportamento do componente:

<img width="859" height="473" alt="image" src="https://github.com/user-attachments/assets/3ef7a8c9-d4e7-438f-a3a9-57e5eb54171d" />

> A curva de perda (MSE) parte de ~1850 e converge para próximo de zero após ~100 épocas de treinamento.

### Saída do Sistema — Exemplo Real
<img width="1125" height="317" alt="image" src="https://github.com/user-attachments/assets/1ff8c664-7f5c-4bbd-a691-b256fe3cb2ae" />
É demonstrada a saída do sistema em decorrência a interpretação dos dados simulados com a API do Gemini. O sistema mostra o componente que está sendo analisado, a temperatura e carga, vê histórico do componente, condição atual e com isso dispõe uma tendência térmica com demontração visual (lâmpada). Em seguida temos a interpretação do Gemini com estado atual da instalação, um possível diagnóstico para nortear o operador e sugestões de intervenções. 

### Protótipo em Google AI Studio
<img width="1424" height="713" alt="image" src="https://github.com/user-attachments/assets/112269b4-ac7c-4100-a7fc-907ce0a2e872" />
Nosso protótipo em Google AI Studio tem como objetivo simular uma IHM real, de forma a mostrar para o operador o status de diferentes componentes do QGBT assim como sua assinatura térmica. De forma rápida e visual é possível identificar componentes superaquecidos, tendência térmica e risco atual. Para efeito de simulação nosso código gera valores aleatórios (dentro de um universo razoável), sendo também possível ao usuário setar valores manualmente para verificar o funcionamento do sistema.

---

### 8. Estrutura do Repositório
```
text
termogrid/
│
├── README.md                  # Documentação principal do projeto
├── requirements.txt           # Dependências: skfuzzy, sklearn, matplotlib, google-generativeai
├── .env.example               # Exemplo: GOOGLE_API_KEY=sua_chave_aqui
├── .gitignore                 # Ignora .env, __pycache__, *.pyc
│
├── assets/
│   └── loss_curve.png         # Curva de perda gerada pelo treinamento da RNA
│
├── notebooks/
│   └── ThermoGrid_Final.ipynb       # Notebook principal executável no Google Colab
│
└── src/
    ├── __init__.py
    ├── fuzzy_engine.py        # Universos, funções de pertinência e regras Fuzzy
    ├── neural_model.py        # MLPRegressor: treinamento, scaler e predição de temperatura
    ├── gemini_diagnosis.py    # Geração do prompt e chamada à API Gemini
    └── thermogrid.py          # Orquestrador principal: executa_sistema_preditivo()
```
---

### 9. Instruções para Execução

1. Clone o repositório do projeto:
bash
   git clone [URL_DO_REPOSITORIO]

2. Acesse a pasta do projeto:
bash
   cd termogrid

3. Abra o notebook:
text
   /notebooks/ThermoGrid_Final.ipynb

4. Instale as dependências:
bash
   !pip install scikit-fuzzy google-generativeai matplotlib scikit-learn python-dotenv

5. Configure a API Gemini no arquivo .env:
env
   GOOGLE_API_KEY=sua_chave_aqui

   Ou diretamente no código:
python
   genai.configure(api_key="sua_chave_aqui")
   model = genai.GenerativeModel('gemini-3.1-flash-lite')

---

## 10. Apêndice de IA

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
