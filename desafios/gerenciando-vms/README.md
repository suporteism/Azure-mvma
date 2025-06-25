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

### 2. Anexando Disco da Máquina

- Simulação de manutenção via **Portal Azure**
- Anexado manualmente o disco de dados
- Reflete uma tarefa típica de suporte ou ajuste de armazenamento

![AddDisk](./images/adddisk.png)

---

### 3. Desanexando Disco da Máquina

- Simulação de manutenção via **Portal Azure**
- Desanexado manualmente o disco de dados
- Reflete uma tarefa típica de suporte ou ajuste de armazenamento

![DetachDisk](./images/detachdisk.png)

---

### 4. Gerenciamento com Azure CLI

Comandos executados via terminal para controle direto das VMs.


```bash
# Login no Azure
az login
```

![Login no Azure via CLI.](./images/azlogin.png)

```
# (Opcional) Definir assinatura
az account set --subscription "Nome da assinatura"
```

![azccountset](./images/azaccount.png)

```
# Listar todas as VMs com status
az vm list -d -o table
```

![azlistvm](./images/azlistvm.png)

```
# Parar uma VM
az vm stop \
  --name lab01-az104-1 \
  --resource-group rg-az104gmva
```

![stopvm](./images/azstopvm.png)

![stopvmportal](./images/stopvmportal.png)

```
# Iniciar uma VM
az vm start \
  --name lab01-az104-1 \
  --resource-group rg-az104gmva
```

![azstartvm](./images/azstartvm.png)

![startvmportal](./images/startvmportal.png)

```
# Reiniciar uma VM
az vm restart \
  --name lab01-az104-2 \
  --resource-group rg-az104gmva
```
```
# Obter status detalhado da VM
az vm get-instance-view \
  --name lab01-az104-1 \
  --resource-group rg-az104gmva \
  --output table
```
```
# Abrir porta (ex: SSH)
az vm open-port \
  --name lab01-az104-1 \
  --resource-group rg-az104gmva \
  --port 22
```

![aznrgrule](./images/aznrgrule.png)

**Acessando via SSH**

![acessossh](./images/acessossh.png)

```
# Desanexar disco de dados
az vm disk detach \
  --name datadisk01 \
  --vm-name lab01-az104-1 \
  --resource-group rg-az104gmva
```

## Estrutura da Pasta

```
desafios/
└── gerenciando-vms/
    ├── images/
    │   ├── acessossh.png
    │   ├── adddisk.png
    │   ├── azaccount.png
    │   ├── azimp01.png
    │   ├── azimp02.png
    │   ├── azimp03.png
    │   ├── azimp04.png
    │   ├── azlistvm.png
    │   ├── azlogin.png
    │   ├── aznrgrule.png
    │   ├── azstartvm.png
    │   ├── azstopvm.png
    │   ├── azure-vms-criadas-portal.png
    │   ├── detachdisk.png
    │   ├── startvmportal.png
    │   └── stopvmportal.png
    └── README.md
```

## Referências

- [Início Rápido: Criar uma máquina virtual do Linux no portal do Azure](https://learn.microsoft.com/pt-br/azure/virtual-machines/linux/quick-create-portal?tabs=ubuntu)
- [Tutorial Oficial - CLI: Gerenciar VMs no Azure](https://learn.microsoft.com/pt-br/azure/virtual-machines/windows/tutorial-manage-vm)
- [Documentação Oficial do Azure CLI](https://learn.microsoft.com/pt-br/cli/azure/)