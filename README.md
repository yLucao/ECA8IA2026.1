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

thermogrid-4.0/
│
├── thermogrid_agent.py
├── requirements.txt
├── .env.example
├── README.md
│
├── /data
├── /models
├── /scripts
└── /notebooks
---
# 🔥 ThermoGrid 4.0

Agente inteligente para análise térmica em sistemas elétricos industriais utilizando Lógica Fuzzy + IA Generativa.

---

## 🚀 Tecnologias

- Python
- YOLOv8 (Visão Computacional)
- Lógica Fuzzy (scikit-fuzzy)
- Gemini API (IA Generativa)

---

## 🧠 Arquitetura

1. Captura de dados (imagem + consumo)
2. Processamento (YOLO + ML)
3. Inferência fuzzy (risco térmico)
4. Interpretação com IA (Gemini)

---
## 🔍 Exemplos de Execução

Veja abaixo cenários reais simulados do sistema:

[INPUT]
Demanda: 100
Oferta: 10

[PROCESSAMENTO]
✔ Fuzzy disponível: True
✔ Método utilizado: Fuzzy Logic

[OUTPUT NUMÉRICO]
Prioridade calculada: 91.3

[INTERPRETAÇÃO - GEMINI]
"Há um desbalanceamento severo entre demanda e oferta, caracterizando uma situação crítica na rede elétrica. Existe alto risco de falhas ou apagões. Medidas imediatas devem ser tomadas, incluindo cortes seletivos ou ativação de fontes alternativas de energia."

## 🌫️ Sistema Fuzzy

Entradas:
- Temperatura (°C)
- Carga elétrica (kW)

Saída:
[INFO] Temperatura: 85°C
[INFO] Carga: 70 kW
[INFO] Risco: 0.87
[CLASSIFICAÇÃO] CRÍTICO
---

## ⚙️ Como rodar

```bash
pip install -r requirements.txt
python thermogrid_agent.py
