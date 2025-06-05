# Controle de Exportação

## Fluxos

- Usuário contador visualiza e exporta em pdf, xls ou csv relatório mensal dos ganhos obtidos para área contábil;
- Usuários contador e operacional visualizam e exportam em pdf, xls ou csv relatório das exportações aprovadas vs ocorridas (fechamento anual);
- Usuários contador e operacional visualizam e exportam em pdf, xls ou csv relatório das exportações em aberto, fechadas e em andamento;
- Usuários contador e operacional visualizam dashboard com o andamento das exportações e dos ganhos obtidos até o momento.

## Desenho Arquitetural

![Controle de Exportação](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/edum-compassuol/adr_markdown_puml/main/controle_export.puml)

## ADRs

### [ADR-001: Adoção de Arquitetura de Microsserviços](./adrs/ADR-001%20Adoção%20de%20Arquitetura%20de%20Microsserviços.md)

Justifica a separação por domínios de negócio e princípio de Single Responsibility.

**No contexto** do sistema de Controle de Exportação que precisa atender diferentes domínios de negócio (processos, analytics e custos), **diante do fato** de que cada domínio possui regras de negócio específicas, ciclos de vida independentes e necessidades de escalabilidade distintas, **decidimos** adotar uma arquitetura baseada em microsserviços separando em três serviços (Processo de Exportação, Analytics de Exportação e Custos de Exportação) **para obter** autonomia das equipes, escalabilidade independente e isolamento de falhas, **aceitando** maior complexidade operacional e overhead de infraestrutura.

### [ADR-002: Utilização de PostgreSQL como Banco de Dados Principal](./adrs/ADR-002%20Utilização%20de%20PostgreSQL%20como%20Banco%20de%20Dados%20Principal.md)

Explica o equilíbrio entre consistência transacional e capacidades analíticas do PostgreSQL.

**No contexto** de um sistema que precisa armazenar dados transacionais críticos de exportação com necessidade de relatórios complexos, **diante do fato** de que é necessário garantir consistência ACID e capacidades analíticas avançadas, **decidimos** utilizar PostgreSQL com schemas separados para cada microsserviço **para obter** confiabilidade transacional, performance analítica e redução de custos operacionais, **aceitando** dependência de todos os serviços no mesmo SGBD e necessidade de coordenação para mudanças de schema.

### [ADR-003: Implementação de Single Page Application (SPA) com Angular](./adrs/ADR-003%20Implementação%20de%20Single%20Page%20Application%20SPA%20com%20Angular.md)

Fundamenta a necessidade de interface rica para dashboards e relatórios interativos.

**No contexto** de usuários que precisam de dashboards interativos, relatórios dinâmicos e exportação de dados em múltiplos formatos, **diante do fato** de que é necessária uma experiência de usuário rica e responsiva, **decidimos** implementar uma SPA com TypeScript e Angular **para obter** interface moderna, dashboards interativos e melhor manutenibilidade com tipagem estática, **aceitando** maior tempo de carregamento inicial e dependência de JavaScript no cliente.

### [ADR-004: Comunicação REST entre Microsserviços](./adrs/ADR-004%20Comunicação%20REST%20entre%20Microsserviços.md)

Justifica REST como protocolo adequado para o padrão de comunicação necessário.

**No contexto** de microsserviços que precisam se comunicar para fornecer funcionalidades completas, especialmente Analytics que consome dados de Processo e Custos, **diante do fato** de que é necessário um protocolo padronizado e simples para integração, **decidimos** utilizar REST API para comunicação síncrona entre os serviços **para obter** simplicidade de implementação, facilidade de debugging e suporte nativo nos frameworks, **aceitando** dependências em tempo de execução e latência adicional para operações distribuídas.

### [ADR-005: Separação de Responsabilidades por Perfis de Usuário](./adrs/ADR-005%20Separação%20de%20Responsabilidades%20por%20Perfis%20de%20Usuário.md)

Explica a importância da segregação para compliance e segurança

**No contexto** de usuários com perfis distintos (Contador e Operacional) que possuem necessidades específicas de informação, **diante do fato** de que é necessário garantir segregação de responsabilidades e compliance entre áreas da empresa, **decidimos** separar funcionalidades por perfil com acesso exclusivo para Contadores aos relatórios financeiros e acesso compartilhado aos relatórios operacionais **para obter** melhor segurança, facilitar auditorias e interfaces focadas por função, **aceitando** necessidade de controle de acesso granular e possível duplicação de componentes.

### [ADR-006: Adoção de Java com Spring Boot para Microsserviços Backend](./adrs/ADR-006%20Adoção%20de%20Java%20com%20Spring%20Boot%20para%20Microsserviços%20Backend.md)

Fundamenta a escolha Java/Spring Boot baseada em maturidade e padronização

**No contexto** de microsserviços que precisam implementar lógicas de negócio complexas, operações críticas de exportação e integrações com banco de dados, **diante do fato** de que é necessária uma plataforma robusta, madura e com boa disponibilidade de desenvolvedores no mercado, **decidimos** utilizar Java com Spring Boot para todos os microsserviços backend **para obter** ecossistema maduro, excelente integração com PostgreSQL e padronização tecnológica, **aceitando** maior consumo de memória e verbosidade da linguagem comparado a alternativas mais leves.
