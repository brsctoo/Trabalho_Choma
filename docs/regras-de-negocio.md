# Regras de Negócio — Share+

## RN-001 — Limite de Vagas do Grupo

**Título:**
Limite de vagas disponíveis por grupo.

**Descrição:**
O número de membros que ocupam um grupo não pode ultrapassar o número de vagas disponíveis definido no cadastro da assinatura.

**Origem:**
Mapa de Fluxos — Cadastro de Assinatura (documento Share+).

**Stakeholders envolvidos:**
Administrador do Grupo, Membro do Grupo.

**Condição:**
Aplicada sempre que um novo membro tentar ingressar no grupo por meio de um convite.

**Regra:**
O ingresso de um novo membro só pode ocorrer se o número de vagas disponíveis for maior que o número de membros ativos atuais.

**Exceções:**
Nenhuma identificada até o momento.

**Dados envolvidos:**
Grupo (vagas disponíveis), Membros ativos.

**Prioridade:**
Alta

**Status:**
Proposto

**Requisitos relacionados:**
RF-002

**Observações:**
O número de vagas é definido pelo Administrador no momento do cadastro da assinatura.

---

## RN-002 — Cálculo do Rateio

**Título:**
Divisão automática do valor da assinatura.

**Descrição:**
O valor individual a ser pago por cada membro é obtido dividindo o valor total da assinatura pelo número de membros ativos no grupo.

**Origem:**
Mapa de Fluxos — Divisão de Custos (documento Share+).

**Stakeholders envolvidos:**
Administrador do Grupo, Membro do Grupo.

**Condição:**
Recalculada sempre que houver alteração no número de membros ativos ou no valor total da assinatura.

**Regra:**
`valor_individual = valor_total / número_de_membros_ativos`.

**Exceções:**
Nenhuma exceção (rateio proporcional/diferenciado) identificada na especificação atual.

**Dados envolvidos:**
Assinatura (valor total), Grupo (membros ativos).

**Prioridade:**
Crítica

**Status:**
Proposto

**Requisitos relacionados:**
RF-003

**Observações:**
Caso o grupo fique sem membros ativos, a divisão fica indefinida — ver RF-003 (critérios de aceite).

---

## RN-003 — Validação de Pagamento pelo Administrador

**Título:**
Confirmação obrigatória do Administrador.

**Descrição:**
O status "em dia" de um membro só é liberado após o Administrador validar o comprovante de pagamento enviado.

**Origem:**
Mapa de Fluxos — Pagamento (documento Share+).

**Stakeholders envolvidos:**
Administrador do Grupo, Membro do Grupo.

**Condição:**
Aplicada após o envio de um comprovante de pagamento por um membro.

**Regra:**
O status da transação só pode ser alterado para "em dia" mediante ação explícita de validação do Administrador; não há confirmação automática.

**Exceções:**
Nenhuma identificada.

**Dados envolvidos:**
Transação (comprovante, status), Membro.

**Prioridade:**
Crítica

**Status:**
Proposto

**Requisitos relacionados:**
RF-005

**Observações:**
—

---

## RN-004 — Exclusividade de Gestão do Grupo

**Título:**
Ações restritas ao Administrador.

**Descrição:**
Somente o Administrador do Grupo pode cadastrar a assinatura, convidar membros e validar pagamentos.

**Origem:**
Seção 1 — Usuários (Personas), documento Share+.

**Stakeholders envolvidos:**
Administrador do Grupo, Membro do Grupo.

**Condição:**
Aplicada em toda operação de gestão do grupo e da assinatura.

**Regra:**
As ações de cadastro de assinatura, convite de membros e validação de pagamento são restritas ao usuário com papel de Administrador do grupo (ID_Administrador).

**Exceções:**
Nenhuma identificada.

**Dados envolvidos:**
Usuário (papel), Grupo (ID_Administrador).

**Prioridade:**
Alta

**Status:**
Proposto

**Requisitos relacionados:**
RF-001, RF-002, RF-005

**Observações:**
—

---

## RN-005 — Comprovante Obrigatório para Registro de Pagamento

**Título:**
Anexo de comprovante obrigatório.

**Descrição:**
Um Membro deve anexar comprovante de pagamento para que sua transação seja considerada para validação.

**Origem:**
Mapa de Fluxos — Pagamento (documento Share+).

**Stakeholders envolvidos:**
Membro do Grupo, Administrador do Grupo.

**Condição:**
Aplicada sempre que um membro registra o pagamento de sua cota.

**Regra:**
A transação não pode ser submetida para validação sem um comprovante (URL/Arquivo) anexado.

**Exceções:**
Nenhuma identificada.

**Dados envolvidos:**
Transação (Comprovante).

**Prioridade:**
Alta

**Status:**
Proposto

**Requisitos relacionados:**
RF-004

**Observações:**
—
