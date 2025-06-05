# ADR-005: Separação de Responsabilidades por Perfis de Usuário

## Status

Aceito

## Contexto

O sistema atende dois perfis distintos de usuários com necessidades diferentes:

- **Contador**: Foco em relatórios financeiros e dados contábeis mensais
- **Operacional**: Foco em acompanhamento de processos e status operacionais
Cada perfil possui necessidades específicas de informação e níveis de acesso distintos.

## Decisão

Implementar separação clara de funcionalidades por perfil de usuário:

- **Contador**: Acesso exclusivo a relatórios de ganhos mensais para área contábil
- **Operacional + Contador**: Acesso compartilhado a relatórios de exportações (aprovadas vs ocorridas, status geral) e dashboards

### Justificativa

A separação por perfis é justificada pela necessidade de compliance e segregação de responsabilidades entre áreas da empresa. Contadores precisam de acesso específico a informações financeiras para fechamento contábil mensal, enquanto operacionais focam no acompanhamento de processos. Esta segregação melhora a segurança do sistema, facilita auditorias e garante que cada usuário tenha acesso apenas às informações relevantes para sua função. A decisão de permitir acesso compartilhado a determinados relatórios operacionais reconhece a necessidade de colaboração entre as áreas para o acompanhamento geral dos processos de exportação.

## Consequências

**Positivas:**

- Interface mais focada nas necessidades específicas de cada usuário
- Melhor segurança através de segregação de acesso
- Facilita compliance e auditoria
- Reduz complexidade da interface por perfil

**Negativas:**

- Necessidade de implementar controle de acesso granular
- Possível duplicação de código/componentes entre perfis
- Complexidade adicional para testes de permissões
- Manutenção de múltiplas views/funcionalidades
