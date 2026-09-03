# Requisitos Funcionais — Share+

## RF-001 — Cadastrar Assinatura

**Título:**
Cadastro de assinatura compartilhada.

**Descrição:**
O sistema deve permitir que o Administrador cadastre uma nova assinatura informando nome do serviço, valor, periodicidade, dia de vencimento e número de vagas disponíveis.

**Objetivo:**
Criar o grupo e viabilizar o compartilhamento de uma assinatura entre membros.

**Stakeholders:**
Administrador do Grupo.

**Ator principal:**
Administrador do Grupo.

**Pré-condições:**
Usuário autenticado com papel de Administrador.

**Entradas:**
Nome do serviço, valor total, periodicidade, dia de vencimento, número de vagas disponíveis.

**Processamento esperado:**
O sistema deve validar os dados informados e criar o registro da Assinatura associado a um novo Grupo com status "Ativo".

**Saídas/Resultados:**
Assinatura e grupo criados; grupo pronto para receber convites.

**Pós-condições:**
Grupo existe com status "Ativo" e vinculado ao Administrador (ID_Administrador).

**Fluxos alternativos/exceções:**
- Dados obrigatórios ausentes.
- Valor total inválido (≤ 0).

**Regras de negócio relacionadas:**
RN-004

**Prioridade:**
Crítica

**Status:**
Aprovado

**Critérios de aceite:**
- Não permitir cadastro sem nome do serviço, valor total e dia de vencimento.
- Grupo criado com status "Ativo" por padrão.
- Administrador definido automaticamente como o usuário que realizou o cadastro.

**Casos de uso relacionados:**
UC-001

**Tarefas relacionadas:**
TASK-001

**Casos de teste relacionados:**
CT-001

---

## RF-002 — Convidar Membros

**Título:**
Convite de membros para o grupo.

**Descrição:**
O sistema deve permitir que o Administrador gere um link único de convite ou envie convite por e-mail para preencher as vagas disponíveis do grupo.

**Objetivo:**
Viabilizar o ingresso de novos membros no grupo.

**Stakeholders:**
Administrador do Grupo, Membro do Grupo.

**Ator principal:**
Administrador do Grupo.

**Pré-condições:**
Grupo cadastrado; vagas disponíveis maiores que zero (RN-001).

**Entradas:**
E-mail do convidado (opcional) ou solicitação de geração de link.

**Processamento esperado:**
O sistema deve validar a disponibilidade de vagas (RN-001) e gerar um link único de convite ou disparar um e-mail de convite.

**Saídas/Resultados:**
Link de convite gerado ou e-mail de convite enviado.

**Pós-condições:**
Convite disponível para uso até o preenchimento da vaga correspondente.

**Fluxos alternativos/exceções:**
- Grupo sem vagas disponíveis (RN-001).
- E-mail informado em formato inválido.

**Regras de negócio relacionadas:**
RN-001, RN-004

**Prioridade:**
Alta

**Status:**
Aprovado

**Critérios de aceite:**
- Não gerar convite quando não houver vagas disponíveis.
- Link de convite deve ser único por grupo.
- Ao aceitar o convite, o membro é automaticamente vinculado ao grupo.

**Casos de uso relacionados:**
UC-002

**Tarefas relacionadas:**
TASK-002

**Casos de teste relacionados:**
CT-002

---

## RF-003 — Calcular Divisão

**Título:**
Cálculo automático do valor individual.

**Descrição:**
O sistema deve calcular automaticamente o valor individual devido por cada membro, com base no valor total da assinatura e no número de membros ativos.

**Objetivo:**
Garantir a divisão automática e transparente dos custos entre os membros do grupo.

**Stakeholders:**
Administrador do Grupo, Membro do Grupo.

**Ator principal:**
Sistema (processo automático).

**Pré-condições:**
Grupo com ao menos um membro ativo.

**Entradas:**
Valor total da assinatura, número de membros ativos.

**Processamento esperado:**
O sistema deve recalcular o valor individual (RN-002) sempre que o número de membros ativos ou o valor total da assinatura for alterado.

**Saídas/Resultados:**
Valor individual atualizado, exibido para cada membro do grupo.

**Pós-condições:**
Os valores individuais refletem a composição atual do grupo.

**Fluxos alternativos/exceções:**
- Grupo sem membros ativos.
  
**Regras de negócio relacionadas:**
RN-002

**Prioridade:**
Crítica

**Status:**
Aprovado

**Critérios de aceite:**
- Recalcular automaticamente o valor individual ao entrar ou sair um membro.
- Exibir o valor individual atualizado para todos os membros do grupo.
- Impedir divisão por zero quando não houver membros ativos.

**Casos de uso relacionados:**
UC-003

**Tarefas relacionadas:**
TASK-003

**Casos de teste relacionados:**
CT-003

---

## RF-004 — Registrar Pagamento

**Título:**
Registro de pagamento pelo membro.

**Descrição:**
O sistema deve permitir que o Membro registre o pagamento da sua cota, anexando o comprovante correspondente.

**Objetivo:**
Formalizar a quitação da cota individual e disponibilizá-la para validação pelo Administrador.

**Stakeholders:**
Membro do Grupo, Administrador do Grupo.

**Ator principal:**
Membro do Grupo.

**Pré-condições:**
Membro vinculado a um grupo ativo com cota individual definida.

**Entradas:**
Comprovante de pagamento (arquivo), valor pago, data do pagamento.

**Processamento esperado:**
O sistema deve registrar uma nova Transação com status "Pendente de validação", associada ao membro (RN-005).

**Saídas/Resultados:**
Transação registrada com status "Pendente de validação".

**Pós-condições:**
Transação disponível para análise do Administrador.

**Fluxos alternativos/exceções:**
- Tentativa de registro sem comprovante anexado (RN-005).

**Regras de negócio relacionadas:**
RN-005

**Prioridade:**
Alta

**Status:**
Proposto

**Critérios de aceite:**
- Não permitir registro de pagamento sem comprovante anexado.
- Transação criada com status "Pendente de validação".
- Registrar data e valor informados pelo membro.

**Casos de uso relacionados:**
UC-004

**Tarefas relacionadas:**
TASK-004

**Casos de teste relacionados:**
CT-004

---

## RF-005 — Validar Pagamento

**Título:**
Validação de pagamento pelo administrador.

**Descrição:**
O sistema deve permitir que o Administrador analise o comprovante enviado e confirme ou rejeite o pagamento, liberando o status "em dia" do membro quando aprovado.

**Objetivo:**
Garantir controle e transparência sobre a situação de pagamento de cada membro do grupo.

**Stakeholders:**
Administrador do Grupo, Membro do Grupo.

**Ator principal:**
Administrador do Grupo.

**Pré-condições:**
Existência de uma transação com status "Pendente de validação".

**Entradas:**
Decisão do Administrador (aprovar ou rejeitar).

**Processamento esperado:**
O sistema deve atualizar o status da transação e do membro conforme a decisão do Administrador (RN-003, RN-004).

**Saídas/Resultados:**
Status do membro atualizado para "em dia" (aprovado) ou "pendente"/"rejeitado".

**Pós-condições:**
Situação financeira do membro refletida no grupo.

**Fluxos alternativos/exceções:**
- Comprovante rejeitado pelo Administrador.
- Comprovante inválido ou ilegível.

**Regras de negócio relacionadas:**
RN-003, RN-004

**Prioridade:**
Crítica

**Status:**
Aprovado

**Critérios de aceite:**
- Apenas o Administrador do grupo pode validar transações do grupo.
- O status do membro só muda para "em dia" após validação explícita.
- Registrar histórico da validação (quem validou e quando).

**Casos de uso relacionados:**
UC-005

**Tarefas relacionadas:**
TASK-005

**Casos de teste relacionados:**
CT-005
