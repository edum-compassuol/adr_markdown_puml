# ADR-001: Adoção de Arquitetura de Microsserviços

## Status

Aceito

## Contexto

O sistema de Controle de Exportação precisa atender diferentes domínios de negócio (processos de exportação, analytics/relatórios e custos), cada um com suas próprias regras de negócio, ciclos de vida e necessidades de escalabilidade. Existe a necessidade de permitir que diferentes equipes trabalhem independentemente em cada domínio, além de facilitar a manutenção e evolução do sistema.

## Decisão

Adotar uma arquitetura baseada em microsserviços, separando as responsabilidades em três serviços principais:

- **Processo de Exportação**: Gerencia o ciclo de vida dos processos (criar, editar, cancelar, gerenciar saldos)
- **Analytics de Exportação**: Responsável por dashboards e relatórios
- **Custos de Exportação**: Gerencia cálculos e registro de custos

### Justificativa

Esta separação em três microsserviços distintos é justificada pelo principio de Single Responsibility e pela necessidade de desacoplamento entre domínios de negócio que possuem ciclos de vida independentes. O domínio de Processo de Exportação é operacional e transacional, Analytics tem características de read-heavy com complexas agregações de dados, e Custos possui lógicas específicas de cálculos financeiros. Cada serviço pode ser desenvolvido, testado, implantado e escalado independentemente, permitindo que equipes especializadas trabalhem em paralelo sem dependências cruzadas.

## Consequências

**Positivas:**

- Maior autonomia das equipes de desenvolvimento
- Escalabilidade independente por domínio
- Facilita deployment independente
- Melhor isolamento de falhas
- Permite uso de tecnologias específicas para cada domínio

**Negativas:**

- Maior complexidade operacional
- Necessidade de gerenciar comunicação entre serviços
- Overhead de infraestrutura
- Complexidade adicional para transações distribuídas
