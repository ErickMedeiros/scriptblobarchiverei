
# ☁️ Script de Reidratação de Blobs no Azure Storage

Este script em PowerShell realiza a reidratação de blobs que estão na camada **Archive** para a camada **Hot** em uma conta de armazenamento do Azure. O processo é automatizado para todos os containers existentes na conta, e gera um log completo em CSV com os resultados de cada operação.

## 🚀 Funcionalidades

- 🔍 Varre todos os containers dentro de uma conta de armazenamento no Azure.
- 📦 Identifica todos os blobs que estão na camada **Archive**.
- ♻️ Executa a reidratação de cada blob para a camada **Hot**.
- 📑 Gera um log detalhado em CSV contendo:
  - Data e hora
  - Nome do container
  - Nome do blob
  - Blob Tier anterior
  - Status da operação (Sucesso ou erro)

## 🧰 Pré-requisitos

- PowerShell 5.x ou superior
- Azure PowerShell Module instalado

### Instalação do módulo Azure:

```powershell
Install-Module -Name Az -Scope CurrentUser -Repository PSGallery -Force
```

### Login no Azure:

```powershell
Connect-AzAccount
```

## ⚙️ Como utilizar

1. Configure as variáveis no início do script conforme seu ambiente:

```powershell
$resourceGroup = "SeuResourceGroup"
$storageAccount = "NomeDoSeuStorageAccount"
```

2. Execute o script no PowerShell:

```powershell
.\ReidratarBlobs.ps1
```

3. O log será salvo automaticamente no diretório:

```
C:\Temp\Reidratacao-Log-[DATA_HORA].csv
```

## 📄 Estrutura do Log CSV

| Data | Container | Blob | BlobTierAnterior | Status |
|------|-----------|------|------------------|--------|
| 2025-05-25 15:32 | container1 | arquivo.zip | Archive | Reidratação Solicitada |
| 2025-05-25 15:33 | container2 | backup.bak | Archive | Erro: [Mensagem do erro] |

## 🚨 Observações importantes

- A reidratação de blobs da camada **Archive** para **Hot** não é instantânea. Pode levar horas, dependendo do tamanho e quantidade de arquivos.
- Este script apenas inicia o processo de reidratação. Consulte o status do blob posteriormente para confirmar a mudança de tier.
- Certifique-se de que a conta usada tem permissões suficientes para gerenciamento do Storage Account.

## 🛠️ Tecnologias e ferramentas

- PowerShell
- Azure PowerShell Module
- Azure Blob Storage

## 🧑‍💻 Autor

Erick Bezerra de Medeiros  
[LinkedIn](https://www.linkedin.com/in/erickbmedeiros) • [Blog](https://erickbmedeiros.com.br)

## 📜 Licença

Este projeto está licenciado sob a licença MIT - veja o arquivo [LICENSE](LICENSE) para mais detalhes.









