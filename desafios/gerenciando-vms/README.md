# Desafio: Gerenciando Máquinas Virtuais no Azure

Este desafio faz parte da formação **AZ-104: Azure Administrator Associate** na plataforma DIO. O objetivo é praticar a criação, gerenciamento e operação de máquinas virtuais no Azure, utilizando tanto o **Portal Azure** quanto a **Azure CLI**.

---

## Objetivo

Criar e gerenciar máquinas virtuais Linux no Azure, explorando operações essenciais como:

- Implantação de VMs
- Início e parada da VM
- Acesso remoto via SSH
- Gerenciamento de disco (desanexar)
- Verificação de status e conectividade

---

## Etapas Realizadas

### 1. Implantação de Máquinas Virtuais (Portal)

- Criadas duas VMs com imagem **Ubuntu**
- Tamanho: `Standard_B1s`
- Local: `Brazil South`
- Grupo de recursos: `rg-az104gmva`

![tela 01-01](./images/azimp01.png)

![tela 01-02](./images/azimp02.png)

![tela 01-03](./images/azimp03.png)

![tela 01-04](./images/azimp04.png)

**Visualização no portal VMs iniciadas:**

![VMs no portal Azure](./images/azure-vms-criadas-portal.png)

---

### 2. Desanexando Disco da Máquina

- Simulação de manutenção via **Portal Azure**
- Desanexado manualmente o disco de dados
- Reflete uma tarefa típica de suporte ou ajuste de armazenamento

---

### 3. Gerenciamento com Azure CLI

Comandos executados via terminal para controle direto das VMs.

azlogin

![Login no Azure via CLI.](./images/azlogin.png)

az account set

![azccountset](./images/azaccount.png)

az vm list -d -o table

![azlistvm](./images/azlistvm.png)

```bash
# Login no Azure
az login

# (Opcional) Definir assinatura
az account set --subscription "Nome da assinatura"

# Listar todas as VMs com status
az vm list -d -o table

# Parar uma VM
az vm stop \
  --name lab01-az104-1 \
  --resource-group rg-az104gmva

# Iniciar uma VM
az vm start \
  --name lab01-az104-1 \
  --resource-group rg-az104gmva

# Reiniciar uma VM
az vm restart \
  --name lab01-az104-2 \
  --resource-group rg-az104gmva

# Obter status detalhado da VM
az vm get-instance-view \
  --name lab01-az104-1 \
  --resource-group rg-az104gmva \
  --output table

# Abrir porta (ex: SSH)
az vm open-port \
  --name lab01-az104-1 \
  --resource-group rg-az104gmva \
  --port 22

# Desanexar disco de dados
az vm disk detach \
  --name datadisk01 \
  --vm-name lab01-az104-1 \
  --resource-group rg-az104gmva
