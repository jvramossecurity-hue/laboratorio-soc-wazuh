# Instalação do Wazuh Manager 4.14.10

## 1. Objetivo

Este documento registra o processo de instalação do Wazuh Manager em uma máquina virtual Ubuntu Server 24.04 LTS.

A atividade faz parte da construção de um laboratório doméstico de SOC (Security Operations Center), com finalidade educacional e profissional.

O objetivo desta etapa foi instalar o componente responsável por receber e analisar eventos de segurança dos agentes monitorados.

## 2. Ambiente utilizado

| Componente | Configuração |
|---|---|
| Sistema principal | Windows 11 |
| Virtualização | Oracle VirtualBox |
| Sistema da máquina virtual | Ubuntu Server 24.04 LTS |
| Wazuh Manager | 4.14.10-1 |
| Memória RAM da VM | 2 GB |
| Processadores virtuais | 2 vCPU |
| Disco virtual | 35 GB |

**Observação:** a máquina virtual possui recursos limitados. Por isso, nesta etapa foi instalado somente o Wazuh Manager. O Indexer e o Dashboard serão avaliados em etapas futuras.

## 3. Preparação do sistema

Após instalar o Ubuntu Server, foram realizadas atualizações do sistema operacional utilizando o gerenciador de pacotes APT.

Comando utilizado:

```bash
sudo apt-get update
```

Esse comando atualiza a lista de pacotes disponíveis nos repositórios configurados no Ubuntu.

Também foram verificadas as ferramentas necessárias para baixar e verificar o pacote:

```bash
command -v gpg
command -v curl
```

- `gpg`: ferramenta utilizada para operações com chaves e assinaturas criptográficas.
- `curl`: ferramenta utilizada para transferir arquivos e consultar endereços na internet.
- `command -v`: verifica se o comando está disponível no sistema.

## 4. Configuração da chave GPG

Foi preparada a chave pública de assinatura do Wazuh.

A chave pública permite verificar a autenticidade de pacotes e informações assinadas pelo fornecedor.

O processo utilizou o endereço oficial:

https://packages.wazuh.com/key/GPG-KEY-WAZUH

A chave foi importada para o sistema de chaves GPG e utilizada na configuração do repositório.

## 5. Problema encontrado: erro HTTP 403

Durante a configuração, o comando `apt-get update` apresentou:

```text
403 Forbidden
```

O erro indicava que o servidor não estava permitindo a obtenção do índice do repositório Wazuh pelo APT naquele momento.

Foram realizadas verificações de conectividade, resolução DNS e respostas HTTP.

O domínio `packages.wazuh.com` foi resolvido para endereços IPv4, e consultas diretas ao servidor retornaram respostas HTTP 200 em determinados testes.

Mesmo assim, a atualização do índice do repositório pelo APT continuou retornando HTTP 403.

## 6. Download manual do pacote

Para continuar a instalação, foi realizado o download direto do pacote oficial Wazuh Manager.

Arquivo utilizado:

`wazuh-manager_4.14.10-1_amd64.deb`

O download foi feito com `curl`, salvando o arquivo na pasta pessoal do usuário.

O pacote baixado tinha aproximadamente 594 MB.

## 7. Verificação de integridade SHA-512

Antes da instalação, foi calculado o hash SHA-512 do pacote:

```bash
sha512sum "$HOME/wazuh-manager.deb"
```

O SHA-512 gera uma impressão digital do conteúdo do arquivo.

Em seguida, foi obtido o checksum publicado pelo fornecedor e realizada a comparação dos valores.

**Resultado:** conforme a verificação realizada durante o laboratório, o hash calculado localmente coincidiu com o checksum oficial consultado.

Essa verificação ajuda a identificar alterações ou corrupção do arquivo durante a transferência.

## 8. Instalação do Wazuh Manager

O pacote foi instalado com:

```bash
sudo dpkg -i "$HOME/wazuh-manager.deb"
```

Explicação:

- `sudo`: executa o comando com privilégios administrativos.
- `dpkg`: ferramenta de gerenciamento de pacotes Debian.
- `-i`: opção utilizada para instalar um pacote.
- `$HOME`: representa a pasta pessoal do usuário.

A instalação foi concluída sem apresentar erro no processo de configuração do pacote.

Versão instalada: **Wazuh Manager 4.14.10-1**.

## 9. Inicialização do serviço

Após a instalação, o serviço foi iniciado:

```bash
sudo systemctl start wazuh-manager
```

Em seguida, foi consultado seu estado:

```bash
sudo systemctl status wazuh-manager
```

O resultado apresentou:

```text
Active: active (running)
```

Isso confirmou que o serviço estava em execução naquele momento.

## 10. Verificação dos componentes internos

Para verificar os processos internos do Wazuh, foi executado:

```bash
sudo /var/ossec/bin/wazuh-control status
```

Os principais componentes apresentados como `running` foram:

- wazuh-modulesd
- wazuh-monitord
- wazuh-logcollector
- wazuh-remoted
- wazuh-syscheckd
- wazuh-analysisd
- wazuh-execd
- wazuh-db
- wazuh-authd
- wazuh-apid

Alguns componentes apareceram como `not running`. Isso não foi tratado isoladamente como falha, pois nem todos os componentes precisam estar ativos em uma instalação independente do Manager.

## 11. Resultado

A instalação do Wazuh Manager 4.14.10-1 foi concluída.

O serviço foi iniciado e os principais componentes internos foram verificados como em execução.

Nesta etapa, ainda não foram instalados:

- Wazuh Indexer.
- Wazuh Dashboard.
- Agentes Windows ou Linux.

Esses componentes serão trabalhados em etapas futuras do laboratório.

## 12. Aprendizados

Durante esta atividade foram praticados:

- Administração básica do Ubuntu Server.
- Utilização do APT e do DPKG.
- Uso de ferramentas de transferência com `curl`.
- Conceitos de chaves públicas GPG.
- Verificação de integridade com SHA-512.
- Investigação de problemas de conectividade HTTP.
- Gerenciamento de serviços com `systemctl`.
- Verificação de processos internos do Wazuh.

## 13. Referências oficiais

- [Wazuh Documentation](https://documentation.wazuh.com/)
- [Wazuh Installation Guide](https://documentation.wazuh.com/current/installation-guide/index.html)
- [Wazuh Packages](https://packages.wazuh.com/)
- [Ubuntu Server Documentation](https://documentation.ubuntu.com/server/)

---

**Projeto:** Laboratório SOC com Wazuh

**Status:** Em desenvolvimento.
