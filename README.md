# 📊 Azure Observabilidade: Guia Técnico de Monitoramento

[![Azure](https://img.shields.io/badge/Microsoft-Azure-0089D6?style=flat-square&logo=microsoft-azure&logoColor=white)](https://azure.microsoft.com/)
[![KQL](https://img.shields.io/badge/Language-KQL-orange?style=flat-square)](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/)

Este repositório contém o guia padrão para configuração de monitoramento, coleta de telemetria e criação de alertas inteligentes no Microsoft Azure. O foco é a utilização do **Azure Monitor**, **Log Analytics** e a linguagem **KQL (Kusto Query Language)**.

## 🚀 Sumário
1. [Configuração de Insights](#-configuração-de-insights)
2. [Análise de Dados com KQL](#-análise-de-dados-com-kql)
3. [Gestão de Alertas](#-gestão-de-alertas)
4. [Visualização e Dashboards](#-visualização-e-dashboards)

---

## 🛠 1. Configuração de Insights
Para obter visibilidade total (Guest-level metrics), é necessário habilitar a coleta de dados detalhada nos recursos.

- **Azure Monitor Agent (AMA):** O guia foca na implementação do novo agente AMA para coleta de métricas e logs.
- **Habilitação:** 1. No Portal do Azure, acesse **Monitor** > **Insights** > **Máquinas Virtuais**.
  2. Selecione o recurso e clique em **Habilitar**.
  3. Vincule o recurso a um **Log Analytics Workspace** centralizado.

---

## 🔍 2. Análise de Dados com KQL
A análise é dividida em métricas quantitativas (tempo real) e logs qualitativos (histórico).

### Métricas (Performance)
Acompanhamento de performance em tempo real através do namespace de métricas do recurso:
* `Percentage CPU`
* `Available Memory`
* `Disk Write Operations/Sec`

### Logs (Diagnóstico Avançado)
Exemplo de query KQL para filtrar eventos de erro críticos no log do Windows nas últimas 24 horas:

```kusto
Event
| where TimeGenerated > ago(24h)
| where EventLevelName == "Error"
| summarize TotalErros = count() by Computer, RenderedDescription
| order by TotalErros desc
