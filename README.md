1. Acesso e Início
Acesse o Portal do Azure e faça login.

No menu, pesquise “Monitorar”

2. Escolha o Recurso a Ser Monitorado
Dentro do Azure Monitor, vá até a seção “Insights” ou clique em “VM Insights”.

Exemplo: selecione uma máquina virtual, banco de dados, App Service, etc.

3. Habilite a Coleta de Dados
Para máquinas virtuais (por exemplo):

Vá em "Monitor" > "Máquinas Virtuais"

Selecione a VM que deseja monitorar.

Clique em "Habilitar Monitoramento"

Isso instala o agente de monitoramento (AMA ou Log Analytics Agent).

Conecte a VM a um workspace do Log Analytics.

4. Configure Métricas e Logs
Para métricas:

Vá em "Métricas"

Selecione o recurso, a métrica (como CPU, memória), e configure gráficos personalizados.

Para logs:

Vá em "Logs"

Escolha a tabela correta (como Syslog para Linux, Event para Windows).

Escreva consultas KQL (Kusto Query Language) para filtrar os dados.

5. Criar Alertas
Vá em "Alertas" > "Nova Regra"

Passos:

Selecionar o recurso (ex: VM, App, etc.)

Definir a condição (ex: CPU > 80% por 5 minutos)

Selecionar o grupo de ação (quem será notificado: e-mail, SMS, webhook, runbook, etc.)

Nomear a regra e revisar.

Clique em “Criar Alerta”

6. (Opcional) Visualizar com Dashboards
Vá para "Dashboard" > "+ Novo painel"

Adicione gráficos de métricas, status de alertas, logs, etc.

(Também é possível): 
Criar alertas automatizados via código (ARM, Bicep, Terraform)

Usar Workbooks para dashboards interativos

Integrar com ferramentas como Power BI, Grafana ou ServiceNow
