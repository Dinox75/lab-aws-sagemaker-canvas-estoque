# 📊 Previsão Inteligente de Estoque com Amazon SageMaker Canvas

Este repositório contém minha solução para o desafio da DIO utilizando o **Amazon SageMaker Canvas** para construir um modelo de previsão de estoque de forma **no-code**.

O objetivo foi treinar um modelo de séries temporais capaz de prever níveis futuros de estoque com base em dados históricos.

---

## 📂 Dataset Utilizado

O dataset contém 500 linhas e 4 colunas:

- `data` – Data da observação  
- `quantidade_estoque` – Quantidade disponível no dia  
- `flag_promocao` – Indica se havia promoção (0/1)  
- `holiday_br` – Indica feriado nacional  

O dataset foi importado diretamente no SageMaker Canvas.

---

## 🧠 Treinamento do Modelo no SageMaker Canvas

Passos realizados no Canvas:

1. Importei o dataset na aba **Datasets**.  
2. Criei um modelo do tipo **Time Series Forecasting**.  
3. Defini:
   - **Target:** `QUANTIDADE_ESTOQUE`
   - **Timestamp:** `data`
4. Executei o treinamento automático (modo Build).  
5. Avaliei o desempenho do modelo na aba **Analyze**.  

---

## 📊 Métricas Obtidas

O modelo apresentou os seguintes resultados:

- **MAPE:** 0.291 (29,1%)  
- **WAPE:** 0.151 (15,1%)  
- **RMSE:** 1.527  
- **MASE:** 0.178  
- **Avg. WQL:** 0.084  

### 🎯 Interpretação

- **MAPE 29,1%:** O erro percentual médio é moderado, mas ainda captura bem tendências.  
- **WAPE 15,1%:** Erro percentual ajustado relativamente baixo.  
- **RMSE 1.527:** Desvios maiores permanecem sob controle.  
- **MASE 0.178:** Excelente — o modelo supera com folga o forecast ingênuo.  

📌 *Conclusão:* o modelo se mostra eficiente para séries temporais simples, com bom equilíbrio entre variabilidade e precisão.

---

## 🔎 Análise de Impacto das Variáveis

O *Column Impact* identificou:

- `Holiday_BR` → 1.98%  
- `Flag_promocao` → 0%  

Interpretação:

- Feriados exercem leve influência sobre o comportamento do estoque.  
- Promoções não impactaram significativamente no conjunto de dados utilizado.

---

## 📉 Limitação Encontrada no AWS Canvas (Erro de Previsão)

Durante a geração de previsões em lote, ocorreu o erro:

