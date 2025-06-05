# ADR-006: Adoção de Java com Spring Boot para Microsserviços Backend

## Status

Aceito

## Contexto

Os microsserviços do sistema (Processo de Exportação, Analytics de Exportação e Custos de Exportação) precisam de uma plataforma de desenvolvimento robusta e madura para implementar lógicas de negócio complexas. O sistema lida com operações críticas de exportação, cálculos financeiros, processamento de relatórios e integrações com banco de dados. É necessário considerar fatores como performance, maturidade do ecossistema, disponibilidade de desenvolvedores no mercado, facilidades para integração com PostgreSQL e capacidades para desenvolvimento de APIs REST.

## Decisão

Utilizar Java como linguagem de programação principal com Spring Boot como framework para implementação de todos os microsserviços backend:

- Processo de Exportação: Java + Spring Boot
- Analytics de Exportação: Java + Spring Boot  
- Custos de Exportação: Java + Spring Boot

### Justificativa

Java com Spring Boot foi escolhido por oferecer a combinação ideal de maturidade, performance e produtividade para o desenvolvimento de microsserviços empresariais. O ecossistema Java é extremamente maduro para aplicações que lidam com transações financeiras e integrações complexas, oferecendo bibliotecas consolidadas para todas as necessidades do sistema. Spring Boot reduz significativamente o boilerplate e acelera o desenvolvimento com sua configuração automática, enquanto Spring Data JPA facilita a integração com PostgreSQL. A padronização em uma única stack tecnológica para todos os microsserviços simplifica operação, monitoramento e manutenção, além de facilitar a mobilidade de desenvolvedores entre os diferentes serviços.

## Consequências

**Positivas:**

- Ecossistema maduro e estável para aplicações empresariais
- Spring Boot oferece configuração automática e reduz boilerplate
- Excelente integração com PostgreSQL via Spring Data JPA
- Grande disponibilidade de desenvolvedores Java no mercado
- Performance adequada para operações transacionais e analíticas
- Ampla gama de bibliotecas e ferramentas de terceiros
- Facilita implementação de APIs REST com Spring Web
- Suporte robusto para testes automatizados
- Ferramentas consolidadas de monitoramento e observabilidade

**Negativas:**

- Maior consumo de memória comparado a linguagens mais leves
- Tempo de startup relativamente alto para microsserviços
- Verbosidade da linguagem pode impactar produtividade inicial
- Necessidade de JVM em todos os ambientes de execução
- Potencial overhead para operações simples comparado a linguagens interpretadas
