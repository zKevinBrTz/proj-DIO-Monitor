# 📊 Guia de Observabilidade: Azure Monitor & Alertas

Este guia estabelece o padrão para configuração de monitoramento, coleta de logs e criação de alertas inteligentes para recursos no Microsoft Azure, utilizando o **Azure Monitor** e **Log Analytics**.

### Sumário
1. [Configuração de Insights (VM & Apps)](#1-configuração-de-insights)
2. [Análise de Dados com KQL (Logs)](#2-análise-de-dados-com-kql)
3. [Gestão de Alertas e Resposta](#3-gestão-de-alertas-e-resposta)
4. [Visualização e Dashboards](#4-visualização-e-dashboards)

---

## 1. Configuração de Insights

Para obter visibilidade total, é necessário habilitar a coleta de dados detalhada (Guest-level metrics).

1.  **Acesso:** No Portal do Azure, pesquise por **Monitor**.
2.  **VM Insights:** Vá em *Insights* > *Máquinas Virtuais*.
3.  **Habilitação:** Selecione o recurso desejado e clique em **Habilitar**.
    * *Nota:* Este processo instala o **Azure Monitor Agent (AMA)**.
4.  **Workspace:** Conecte o recurso a um **Log Analytics Workspace** para centralização dos dados.

---

## 2. Métricas e Logs (KQL)

A análise de performance é dividida em métricas quantitativas e logs qualitativos.

### Métricas (Performance em Tempo Real)
* Navegue até o recurso > **Métricas**.
* Selecione o namespace e a métrica (ex: `Percentage CPU`, `Available Memory`).
* Configure a agregação (Média, Máximo ou Mínimo) para visualização em gráficos.

### Logs (Análise Histórica e Diagnóstico)
Utilize a **Kusto Query Language (KQL)** no menu **Logs** para extrair inteligência dos dados:

```kusto
// Exemplo: Filtrar eventos de erro no log do Windows nas últimas 24h
Event
| where TimeGenerated > ago(24h)
| where EventLevelName == "Error"
| summarize count() by Computer, RenderedDescription
