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
smartgrid-fuzzy/
│
├── README.md
├── requirements.txt
├── .env.example
├── .gitignore
│
├── notebook/
│   └── SmartGrid.ipynb   
│
└── src/
    ├── _init_.py
    ├── fuzzy_logic.py
    ├── fallback.py
    └── ai_interpreter.py
---
# ThermoGrid 4.0

Agente inteligente para análise térmica em sistemas elétricos industriais utilizando Lógica Fuzzy + IA Generativa.

---

## Tecnologias

- Python
- YOLOv8 (Visão Computacional)
- Lógica Fuzzy (scikit-fuzzy)
- Gemini API (IA Generativa)

---

## Arquitetura

1. Captura de dados (imagem + consumo)
2. Processamento (YOLO + ML)
3. Inferência fuzzy (risco térmico)
4. Interpretação com IA (Gemini)

---
## Exemplos de Execução

Veja abaixo cenários reais simulados do sistema:

[INPUT]
Demanda: 100
Oferta: 10

[PROCESSAMENTO]
Fuzzy disponível: True
Método utilizado: Fuzzy Logic

[OUTPUT NUMÉRICO]
Prioridade calculada: 91.3

[INTERPRETAÇÃO - GEMINI]
"Há um desbalanceamento severo entre demanda e oferta, caracterizando uma situação crítica na rede elétrica. Existe alto risco de falhas ou apagões. Medidas imediatas devem ser tomadas, incluindo cortes seletivos ou ativação de fontes alternativas de energia."

## Sistema Fuzzy

Entradas:
- Temperatura (°C)
- Carga elétrica (kW)

Saída:
[INFO] Temperatura: 85°C
[INFO] Carga: 70 kW
[INFO] Risco: 0.87
[CLASSIFICAÇÃO] CRÍTICO
---

Monitoramento Preditivo
Abordagem Escolhida: Rede Neural Artificial (RNA)
Optamos pelo uso de Redes Neurais Artificiais (Multi-Layer Perceptron) em vez de Algoritmos Evolutivos para esta etapa do projeto. O motivo principal é que a RNA apresenta maior precisão na regressão de variáveis contínuas (temperatura) com base em múltiplas entradas (carga e histórico). Enquanto algoritmos evolutivos são excelentes para otimização, a RNA permite que o agente "aprenda" o comportamento térmico do sistema e antecipe falhas antes que elas ocorram na Lógica Fuzzy.

Desempenho do Modelo
O gráfico abaixo demonstra a convergência do modelo durante o treinamento. A redução constante da função de perda (Loss) indica que o agente aprendeu com sucesso a relação entre a carga aplicada e o aquecimento resultante.
E através disso escolhemos a abordagem em RNA, a opção de uso de redes neurais em nosso contexto tornou o TermoGrid em um sistema preditivo, dessa forma, o sistema não diz somente que um componente está superaquecendo, mas prevê tendência a superaquecer.
<img width="859" height="473" alt="image" src="https://github.com/user-attachments/assets/3ef7a8c9-d4e7-438f-a3a9-57e5eb54171d" />

## Como rodar

```bash
pip install -r requirements.txt
python thermogrid_agent.py
pip install scikit-fuzzy
pip install google-genai
pip install matplotlib scikit-learn
