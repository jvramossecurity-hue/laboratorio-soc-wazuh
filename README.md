# Laboratório SOC com Wazuh

Projeto prático de construção de um laboratório doméstico de cibersegurança (SOC — Security Operations Center), utilizando ferramentas gratuitas e open source.

O objetivo é aprender, na prática, como funciona o trabalho de um analista SOC, desde a coleta de logs até a identificação, análise e resposta a incidentes.

## Objetivos do projeto

- Construir um ambiente de monitoramento de segurança.
- Aprender a utilizar o Wazuh.
- Compreender a coleta e análise de logs.
- Desenvolver habilidades de detecção e investigação de ameaças.
- Realizar simulações de segurança controladas.
- Documentar atividades e resultados para fins de portfólio profissional.

## Ambiente utilizado

| Componente | Configuração |
|---|---|
| Sistema principal | Windows 11 |
| Virtualização | Oracle VirtualBox |
| Sistema da VM | Ubuntu Server 24.04 LTS |
| SIEM / Security Monitoring | Wazuh Manager 4.14.10 |
| Memória da VM | 2 GB RAM |
| Processadores virtuais | 2 vCPU |
| Disco virtual | 35 GB |
| Memória do computador principal | 8 GB RAM |

## Arquitetura atual

O laboratório está em construção.

Até o momento, foi criada uma máquina virtual Ubuntu Server e instalado o Wazuh Manager.

O Indexer, o Dashboard e os endpoints monitorados ainda serão adicionados em etapas futuras.

## Atividades concluídas

- [x] Preparação da máquina virtual no VirtualBox.
- [x] Instalação do Ubuntu Server.
- [x] Atualização do sistema operacional.
- [x] Preparação da chave GPG do Wazuh.
- [x] Configuração do repositório oficial.
- [x] Investigação de erro HTTP 403 durante a atualização do repositório APT.
- [x] Download manual do pacote oficial Wazuh Manager 4.14.10.
- [x] Verificação de integridade do pacote utilizando SHA-512 e comparação com o checksum oficial.
- [x] Instalação do Wazuh Manager.
- [x] Inicialização e verificação dos componentes internos do Manager.

## Próximas atividades

- [ ] Documentar a instalação com evidências.
- [ ] Instalar e configurar o Wazuh Indexer.
- [ ] Instalar e configurar o Wazuh Dashboard.
- [ ] Monitorar um endpoint Windows.
- [ ] Configurar coleta de logs.
- [ ] Investigar eventos de segurança.
- [ ] Criar regras de detecção personalizadas.
- [ ] Realizar simulações controladas.
- [ ] Documentar investigações e respostas a incidentes.

## Segurança do laboratório

As atividades práticas serão realizadas em ambiente controlado e isolado, com o objetivo de evitar impactos em sistemas externos ou no computador principal.

Não serão publicados senhas, chaves privadas, tokens ou outros dados sensíveis.

## Aprendizados

Este projeto está sendo desenvolvido progressivamente, com foco no aprendizado prático de:

- Linux e administração de sistemas.
- Monitoramento de segurança.
- Análise de logs.
- SIEM e detecção de ameaças.
- Investigação de incidentes.
- Fundamentos de segurança em nuvem.

## Documentação oficial

- [Wazuh Documentation](https://documentation.wazuh.com/)
- [Wazuh Installation Guide](https://documentation.wazuh.com/current/installation-guide/index.html)
- [Ubuntu Server Documentation](https://documentation.ubuntu.com/server/)
- [GitHub Documentation](https://docs.github.com/)

---

**Status:** Em desenvolvimento.

Este repositório será atualizado conforme novas etapas do laboratório forem concluídas.
