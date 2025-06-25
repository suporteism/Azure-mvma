# Desafio: Monitoramento de Máquinas Virtuais no Azure (Em andamento)

## Objetivo

Este repositório foi criado como parte do desafio prático da formação AZ-104 na DIO, com foco em configuração e gerenciamento de monitoramento no Azure. O projeto demonstra como aplicar conceitos de observabilidade em máquinas virtuais para detectar eventos críticos como a exclusão de uma VM.

## Aprendizados e Habilidades Desenvolvidas

- Configuração de alertas no Azure Monitor
- Uso de Log Analytics e consultas com KQL
- Criação de Action Groups para envio de e-mails
- Implantação de regras de processamento
- Documentação técnica com GitHub e Markdown

## Cenário do Laboratório

- Recurso monitorado: `az104-11-vm0`
- Grupo de Recursos: `az104-rg11`
- Evento monitorado: Exclusão da VM
- Ação: Envio de alerta por e-mail
- Consulta: Log query para rastrear atividade de deleção

## Etapas do Projeto

### Task 1 – Criar a VM `az104-11-vm0`
Provisionamento da máquina virtual Linux/Windows para testes.

### Task 2 – Criar alerta para deleção da VM
Configuração de um alerta com base no Activity Log.

### Task 3 – Criar Action Group
Envio de e-mail automático quando o alerta for disparado.

### Task 4 – Disparar o alerta
Simulação da exclusão da VM para validação da regra.

### Task 5 – Adicionar regra de processamento
Aplicar filtros ou supressões conforme necessidade.

### Task 6 – Consultar logs com KQL
Visualização dos eventos em Log Analytics usando consultas personalizadas.

## Captura de Tela do Fluxo

Imagem disponível na pasta `/images`:
- `fluxo-monitoramento.png`

## Dicas e Notas

- Documentação oficial:  
  https://learn.microsoft.com/pt-br/azure/azure-monitor/vm/vminsights-overview

- Exemplo de consulta KQL para identificar deleção de VM:

```kql
AzureActivity
| where OperationNameValue == "Microsoft.Compute/virtualMachines/delete"
| sort by TimeGenerated desc