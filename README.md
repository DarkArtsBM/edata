# 📦 E-commerce Logistics & Performance Audit

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Pandas](https://img.shields.io/badge/Pandas-2.0-150458)
![Status](https://img.shields.io/badge/Status-Concluído-success)
![Focus](https://img.shields.io/badge/Focus-Data%20Cleaning%20%26%20Analytics-orange)

> **Resumo:** Este projeto simula a atuação de um Time de Dados investigando a operação de um e-commerce brasileiro. O objetivo foi auditar os dados brutos, sanear inconsistências e entregar um diagnóstico confiável sobre Receita e Eficiência Logística.

---

## 🎯 O Desafio de Negócio
A diretoria precisava de respostas sobre por que as reclamações de clientes aumentaram, apesar do faturamento recorde. As perguntas chave eram:
1. O nosso faturamento é real ou inflado por cancelamentos?
2. O frete "Same-Day" (Expresso) está a cumprir a promessa?
3. O atraso na entrega é um problema regional ou sistémico?

## 🛠️ O Pipeline de Dados
O projeto seguiu um fluxo rigoroso de Engenharia e Análise de Dados:

1.  **Ingestão:** Consolidação de 5 tabelas relacionais (`Orders`, `Customer`, `Delivery`, `Products`, `Shopping`).
2.  **Data Quality & Cleaning:**
    * Detecção de **"Time Travelers"**: Pedidos entregues *antes* da data da compra.
    * Remoção de **Inconsistências**: Pedidos cancelados financeiramente mas marcados como entregues.
    * *Impacto:* 22,5% da base bruta foi descartada para garantir a integridade da análise.
3.  **Feature Engineering:** Cálculo de Lead Time (Dias corridos), Flag de Atraso e Share de Frete.
4.  **Storytelling:** Geração de relatórios executivos e dashboards estáticos.

---

## 📊 Principais Insights (O "Diagnóstico")

### 1. O Paradoxo do Crescimento
A empresa fatura bem (**Ticket Médio de R$ 2.583**), mas opera no caos.
A taxa de atraso global é de **82,8%**.

![Trend]<img width="1600" height="800" alt="fig1" src="https://github.com/user-attachments/assets/2d18f851-cb9c-4e03-82c7-732bfd3bd8f0" />

*Evolução Mensal: O aumento da receita (barras) não resolveu o problema do atraso (linha vermelha).*

### 2. A "Ilusão" do Frete Expresso
O cliente paga 87% mais caro pelo serviço *Same-Day*, mas recebe o produto no mesmo prazo do serviço *Standard*.

| Serviço | Preço Médio | Tempo Real de Entrega | Taxa de Atraso |
| :--- | :--- | :--- | :--- |
| **Same-Day** | R$ 42,90 | **37,5 dias** | 82,9% |
| **Standard** | R$ 22,90 | **38,8 dias** | 81,3% |

### 3. Geografia do Colapso
O atraso não é concentrado em áreas remotas. É um problema sistémico de expedição.
* **Melhor Estado (PE):** 72% de atraso.
* **Pior Estado (PA):** 92% de atraso.

![Geo]<img width="1600" height="667" alt="fig2" src="https://github.com/user-attachments/assets/ecf3dbc0-8149-4f71-84e1-79ddc87523c9" />


## 🛠️ Metodologia Técnica e Engenharia de Dados

Para garantir a confiabilidade dos KPIs apresentados, o projeto seguiu um pipeline rigoroso de tratamento de dados ("Bronze" para "Silver"), focado na integridade relacional e consistência temporal.

### 1. Arquitetura e Modelagem (Star Schema)
Os dados foram modelados centralizando as transações na tabela fato (`FACT_Orders`) e enriquecendo-a com tabelas dimensão.


---
## 📄 Download do Relatório

[![PDF][Relatório Analítico.pdf](https://github.com/user-attachments/files/23830241/Relatorio.Analitico.pdf)


---

## 📂 Estrutura do Projeto

```text
ecommerce_analytics/
│
├── data/
│   ├── raw/                  # Arquivos CSV originais (Imutáveis)
│   └── processed/            # Dados saneados e prontos para análise
│
├── notebooks/
│   ├── 01_data_cleaning.ipynb    # Limpeza, Saneamento e Engenharia de Features
│   └── 02_deep_dive_eda.ipynb    # Análise Exploratória e Geração de Gráficos
│
├── sql/
│   └── 01_monitoramento_logistica.sql  # Query para implementação em Data Warehouse
│
├── reports/
│   ├── figures/              # Imagens geradas pelos notebooks
│   └── Relatorio_Final.md    # Texto executivo para a diretoria
│
└── requirements.txt          # Dependências do projeto




