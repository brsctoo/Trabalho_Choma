# Requisitos Não Funcionais — Share+

## RNF-001 — Segurança de Dados Sensíveis

**Categoria:**
Segurança

**Descrição:**
O sistema deve proteger os dados bancários e a chave Pix dos usuários por meio de criptografia em repouso e em trânsito.

**Justificativa:**
Dados financeiros/bancários são sensíveis e exigem proteção contra acesso não autorizado.

**Métrica/Critério mensurável:**
Dados armazenados com criptografia (ex.: AES-256) e comunicação via HTTPS/TLS 1.2 ou superior; ausência de dados sensíveis em logs de aplicação.

**Escopo:**
Todo o sistema, em especial os dados de Usuário e Transação.

**Prioridade:**
Crítica

**Status:**
Proposto

**Requisitos relacionados:**
RF-001, RF-004, RF-005

**Casos de teste relacionados:**
CT-006

---

## RNF-002 — Desempenho no Cálculo de Rateio

**Categoria:**
Desempenho

**Descrição:**
O sistema deve recalcular e apresentar o valor individual do rateio em até 2 segundos após qualquer alteração no grupo.

**Justificativa:**
Garantir uma experiência fluida para o usuário ao consultar sua cota.

**Métrica/Critério mensurável:**
Tempo de resposta menor ou igual a 2 segundos para 95% das requisições de cálculo de rateio.

**Escopo:**
Funcionalidade de Divisão de Custos (RF-003).

**Prioridade:**
Alta

**Status:**
Proposto

**Requisitos relacionados:**
RF-003

**Casos de teste relacionados:**
CT-007

---

## RNF-003 — Disponibilidade do Sistema

**Categoria:**
Disponibilidade

**Descrição:**
O sistema deve estar disponível para acesso dos usuários em, no mínimo, 99% do tempo mensal.

**Justificativa:**
Membros precisam acessar o sistema para registrar pagamentos dentro do prazo de vencimento, evitando prejuízo à continuidade do serviço compartilhado.

**Métrica/Critério mensurável:**
Uptime mensal maior ou igual a 99%, monitorado por ferramenta de observabilidade.

**Escopo:**
Todo o sistema.

**Prioridade:**
Alta

**Status:**
Proposto

**Requisitos relacionados:**
RF-004, RF-005

**Casos de teste relacionados:**
CT-008

---

## RNF-004 — Usabilidade do Fluxo de Convite

**Categoria:**
Usabilidade

**Descrição:**
O processo de convite e ingresso de um novo membro no grupo deve ser concluído em no máximo 3 passos, sem necessidade de treinamento prévio.

**Justificativa:**
Facilitar a adesão de novos membros e reduzir a taxa de abandono no ingresso ao grupo.

**Métrica/Critério mensurável:**
Testes de usabilidade indicando conclusão do fluxo em até 3 passos por, no mínimo, 90% dos usuários testados.

**Escopo:**
Funcionalidade de Convite de Membros (RF-002).

**Prioridade:**
Média

**Status:**
Proposto

**Requisitos relacionados:**
RF-002

**Casos de teste relacionados:**
CT-009

---

## RNF-005 — Confiabilidade no Registro de Transações

**Categoria:**
Confiabilidade

**Descrição:**
O sistema não deve perder ou duplicar registros de transações de pagamento, mesmo em caso de falha durante o envio do comprovante.

**Justificativa:**
A integridade do histórico financeiro é essencial para a confiança entre os membros do grupo.

**Métrica/Critério mensurável:**
Zero divergências entre comprovantes enviados e transações registradas em testes de carga e de falha simulada.

**Escopo:**
Funcionalidades de Pagamento e Validação (RF-004, RF-005).

**Prioridade:**
Crítica

**Status:**
Proposto

**Requisitos relacionados:**
RF-004, RF-005

**Casos de teste relacionados:**
CT-010
