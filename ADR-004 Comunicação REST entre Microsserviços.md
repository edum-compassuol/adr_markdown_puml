# ADR-004: Comunicação REST entre Microsserviços

## Status

Aceito

## Contexto

Os microsserviços precisam se comunicar para fornecer funcionalidades completas, especialmente o serviço de Analytics que precisa consumir dados dos serviços de Processo e Custos. É necessário definir um protocolo de comunicação padronizado, simples de implementar e debugar.

## Decisão

Utilizar REST API como protocolo de comunicação síncrona entre os microsserviços, com o serviço de Analytics consumindo dados dos serviços de Processo de Exportação e Custos de Exportação.

### Justificativa

REST foi escolhido por ser um protocolo maduro, amplamente conhecido e padronizado que facilita a integração entre os microsserviços. Para o contexto específico deste sistema, onde o Analytics precisa agregar dados dos outros serviços para geração de relatórios, a comunicação síncrona via REST é apropriada pois garante consistência dos dados no momento da consulta. A simplicidade do REST também facilita debugging, monitoramento e testes, além de ter suporte nativo nos frameworks utilizados (Spring Boot e Angular). Embora existam alternativas como gRPC ou mensageria assíncrona, REST oferece o melhor custo-benefício entre simplicidade de implementação e funcionalidade necessária.

## Consequências

**Positivas:**

- Protocolo amplamente conhecido e padronizado
- Facilita debugging e monitoramento
- Suporte nativo em frameworks web
- Simplicidade de implementação
- Boa integração com ferramentas de teste

**Negativas:**

- Comunicação síncrona pode criar dependências em tempo de execução
- Latência adicional para operações que envolvem múltiplos serviços
- Potencial para criar cascade failures
- Menos eficiente que protocolos binários para alta frequência de chamadas
