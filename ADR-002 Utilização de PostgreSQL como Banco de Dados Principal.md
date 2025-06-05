# ADR-002: Utilização de PostgreSQL como Banco de Dados Principal

## Status

Aceito

## Contexto

O sistema precisa de um banco de dados confiável para armazenar dados transacionais críticos de exportação, com suporte a ACID, capacidades analíticas e que seja adequado para relatórios complexos. É necessário também considerar o conhecimento da equipe e custos operacionais.

## Decisão

Utilizar PostgreSQL como sistema de gerenciamento de banco de dados principal, com schemas separados para cada microsserviço:

- Schema para Processo de Exportação
- Schema para Analytics de Exportação  
- Schema para Custos de Exportação

### Justificativa

PostgreSQL foi escolhido por ser um banco de dados relacional que oferece o melhor equilíbrio entre consistência transacional (ACID) e capacidades analíticas avançadas, essenciais para um sistema de exportação que lida com dados financeiros críticos. A separação em schemas permite isolamento lógico entre os microsserviços mantendo a simplicidade operacional de uma única instância de banco. PostgreSQL também oferece excelente suporte para consultas complexas necessárias para relatórios e dashboards, além de possuir um ecossistema maduro e custo operacional mais baixo que alternativas proprietárias.

## Consequências

**Positivas:**

- ACID compliance para garantir consistência dos dados
- Excelente performance para consultas analíticas
- Suporte robusto a JSON para flexibilidade
- Comunidade ativa e ampla adoção no mercado
- Redução de custos operacionais comparado a soluções proprietárias

**Negativas:**

- Todos os serviços dependem do mesmo SGBD
- Potencial ponto único de falha se não configurado adequadamente
- Necessidade de coordenação para mudanças de schema entre serviços
