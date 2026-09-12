# Casos de Uso — Share+

## UC-001 — Cadastrar Assinatura
 
**Objetivo:**
Permitir que o Administrador crie uma assinatura compartilhada, gerando o grupo correspondente.
 
**Ator principal:**
Administrador do Grupo.
 
**Atores secundários:**
Não apresenta.
 
**Pré-condições:**
Usuário autenticado com nível de Administrador.
 
**Pós-condições:**
Grupo criado com status "Ativo", vinculado ao Administrador, por meio de um ID.
 
**Gatilho:**
Administrador decide cadastrar uma nova assinatura compartilhada.
 
**Fluxo principal:**
1. Administrador informa nome do serviço, valor total, periodicidade, dia de vencimento e número de vagas disponíveis.
2. Sistema valida os dados informados.
3. Sistema cria o registro da nova assinatura.
4. Sistema cria o Grupo associado, com apenas o Administrador como membro, com status "Ativo" e Administrador vinculado automaticamente.
5. Sistema confirma o cadastro e disponibiliza o grupo para receber convites e permite o Administrado compartilhar convites do grupo.
**Fluxos alternativos:**
—
 
**Fluxos de exceção:**
FE01 — Dados obrigatórios ausentes
1. Sistema identifica campo obrigatório não preenchido (nome do serviço, valor total ou dia de vencimento).
2. Sistema informa o erro e não cria a assinatura.
FE02 — Valor total inválido
1. Sistema identifica valor total menor ou igual à 0.
2. Sistema informa o erro e não cria a assinatura.

**Regras de negócio relacionadas:**
RN-004
 
**Requisitos relacionados:**
RF-001
 
---

## UC-002 — Convidar Membros
 
**Objetivo:**
Permitir que o Administrador convide usuários para ocupar vagas disponíveis do grupo.
 
**Ator principal:**
Administrador do Grupo.
 
**Atores secundários:**
Membro do Grupo (destinatário do convite); Serviço de E-mail (quando o envio é por e-mail).
 
**Pré-condições:**
Grupo cadastrado; vagas disponíveis maiores que zero (RN-001).
 
**Pós-condições:**
Convite disponível para uso até o preenchimento da vaga correspondente, ou tempo do convite expirar.
 
**Gatilho:**
Administrador decide convidar usuários para o grupo.
 
**Fluxo principal:**
1. Administrador cria um convite (gerar link ou enviar por e-mail).
2. Sistema valida a disponibilidade de vagas (RN-001).
3. Sistema gera um link único de convite (com tempo até expirar) ou manda um e-mail com um convite para o usuário selecionado.
4. Sistema disponibiliza o convite ao Administrador (caso tenha selecionado para gerar um link).
**Fluxos alternativos:**
—
 
**Fluxos de exceção:**
FE01 — Grupo sem vagas disponíveis
1. Sistema identifica que não há vagas disponíveis (RN-001).
2. Sistema impede a geração do convite e informa o erro.
FE02 — E-mail informado em formato inválido
1. Sistema identifica formato de e-mail inválido.
2. Sistema informa o erro e solicita a correção.

**Regras de negócio relacionadas:**
RN-001, RN-004
 
**Requisitos relacionados:**
RF-002
 
---

## UC-003 — Confirmar Entrada no Grupo
 
**Objetivo:**
Permitir que o Membro convidado avalie as condições e a saúde do grupo e confirme sua entrada.
 
**Ator principal:**
Membro do Grupo (Convidado).
 
**Atores secundários:**
—
 
**Pré-condições:**
Convite válido e não expirado; vaga disponível no grupo.
 
**Pós-condições:**
Membro vinculado ao grupo; vagas disponíveis decrementadas; valor individual recalculado.
 
**Gatilho:**
Membro acessa o link de convite ou encontra uma vaga disponível em um grupo de interesse.
 
**Fluxo principal:**
1. Membro acessa o link de convite, ou acessa o grupo.
2. Sistema apresenta as condições e saúde do grupo.
3. Membro confirma a entrada.
4. Sistema cria a Participação, vinculando o Membro ao Grupo.
5. Sistema decrementa as vagas disponíveis no grupo.
6. Sistema recalcula o valor individual da divisão.

**Fluxos alternativos:**
—
 
**Fluxos de exceção:**
FE01 — Convite expirado
1. Sistema identifica que o convite expirou.
2. Sistema impede a confirmação e informa o erro.
FE02 — Vaga já preenchida
1. Sistema identifica que a vaga já foi ocupada por outro usuário.
2. Sistema impede a confirmação e informa o erro.

**Regras de negócio relacionadas:**
RN-001, RN-006
 
**Requisitos relacionados:**
RF-003
  
---

## UC-004 — Calcular Divisão
 
**Objetivo:**
Calcular automaticamente o valor individual para cada membro ativo do grupo.
 
**Ator principal:**
Sistema.
 
**Atores secundários:**
—
 
**Pré-condições:**
Grupo pelo menos um membro ativo.
 
**Pós-condições:**
Valores individuais para todos os membros do grupo.
 
**Gatilho:**
Criação do grupo, alteração no número de membros ativos ou no valor total da assinatura.
 
**Fluxo principal:**
1. Sistema identifica o valor total da assinatura do grupo.
2. Sistema identifica o número total de membros ativos no momento da divisão.
3. Sistema calcula o valor individual.
4. Sistema atualiza o valor para cada membro do grupo.

**Fluxos alternativos:**
—
 
**Fluxos de exceção:**
FE01 — Grupo sem membros ativos
1. Sistema identifica a ausência de membros ativos.
2. Sistema impede o cálculo e mantém a divisão indefinida.

**Regras de negócio relacionadas:**
RN-002
 
**Requisitos relacionados:**
RF-004
 
---

## UC-005 — Registrar Pagamento
 
**Objetivo:**
Permitir que o Membro registre o pagamento da sua parte, anexando o comprovante correspondente.
 
**Ator principal:**
Membro do Grupo.
 
**Atores secundários:**
—
 
**Pré-condições:**
Membro vinculado a um grupo ativo, com valor individual definido.
 
**Pós-condições:**
Transação disponível para análise posterior do Administrador.
 
**Gatilho:**
Membro decide pagar sua parte do valor da assniatura referente ao um período.
 
**Fluxo principal:**
1. Membro acessa a cobrança da sua cota.
2. Membro informa o valor pago e a data do pagamento.
3. Membro anexa o comprovante de pagamento.
4. Sistema registra a Transação com status "Pendente de validação".
5. Sistema disponibiliza a transação para análise do Administrador.

**Fluxos alternativos:**
—
 
**Fluxos de exceção:**
FE01 — Comprovante não anexado
1. Sistema identifica a ausência de comprovante.
2. Sistema impede o registro e solicita o anexo (RN-005).

**Regras de negócio relacionadas:**
RN-005
 
**Requisitos relacionados:**
RF-005
 
---

## UC-006 — Validar Pagamento
 
**Objetivo:**
Permitir que o Administrador analise e valide um pagamento registrado.
 
**Ator principal:**
Administrador do Grupo.
 
**Atores secundários:**
Membro do Grupo (Membro que realizou o pagamento).
 
**Pré-condições:**
Existência de uma transação de algum membro com status "Pendente de validação".
 
**Pós-condições:**
Situação financeira do membro (em dia, pendente ou rejeitado) atualizada; histórico de validação registrado.
 
**Gatilho:**
Administrador é notificado de uma transação pendente ou acessa a lista de pendências.
 
**Fluxo principal:**
1. Administrador acessa a transação pendente e o comprovante anexado.
2. Administrador analisa o comprovante.
3. Administrador aprova o pagamento.
4. Sistema atualiza o status da transação e do membro para "em dia".
5. Sistema registra o histórico da validação (quem validou e quando).

**Fluxos alternativos:**
FA01 — Rejeitar pagamento
1. Administrador rejeita o pagamento.
2. Sistema atualiza o status da transação para "rejeitado" e o status do membro para "pendente".
3. Sistema registra o histórico da rejeição.

**Fluxos de exceção:**
—
 
**Regras de negócio relacionadas:**
RN-003, RN-004
 
**Requisitos relacionados:**
RF-006
 
---

## UC-007 — Confirmar Acesso
 
**Objetivo:**
Permitir que o Membro confirme que conseguiu acessar e utilizar o serviço compartilhado após ter seu pagamento validado.
 
**Ator principal:**
Membro do Grupo.
 
**Atores secundários:**
—
 
**Pré-condições:**
Membro com status "em dia".
 
**Pós-condições:**
Participação do Membro atualizada para "ativo".
 
**Gatilho:**
Membro tenta utilizar o serviço compartilhado após a validação do pagamento.
 
**Fluxo principal:**
1. Membro acessa/utiliza o serviço compartilhado.
2. Membro confirma no sistema que conseguiu utilizá-lo.
3. Sistema registra a confirmação.
4. Sistema atualiza o estado da Participação para "ativo".

**Fluxos alternativos:**
—
 
**Fluxos de exceção:**
—

**Regras de negócio relacionadas:**
RN-007
 
**Requisitos relacionados:**
RF-007
 
---

## UC-008 — Registrar Incidente
 
**Objetivo:**
Permitir que o Administrador ou o Membro registrem um incidente ocorrido no grupo, mantendo histórico até a resolução.
 
**Ator principal:**
Administrador do Grupo ou Membro do Grupo.
 
**Atores secundários:**
—
 
**Pré-condições:**
Usuário autenticado e vinculado ao grupo.
 
**Pós-condições:**
Incidente registrado e vinculado ao grupo, com histórico de ações tomadas e estado.
 
**Gatilho:**
Ocorrência de um problema no ambiente do grupo ou no sistema.
 
**Fluxo principal:**
1. Ator identifica o problema ocorrido.
2. Ator informa o tipo do problema, a descrição, o grupo e o(s) participante(s) envolvido(s).
3. Sistema valida os dados informados.
4. Sistema cria o registro do Incidente com estado "aberto".
5. Sistema mantém o histórico das ações até a resolução.
6. Quando for solucionado, sistema atualiza o estado do incidente para "fechado".

**Fluxos alternativos:**
—
 
**Fluxos de exceção:**
FE01 — Dados inválidos ou tipo de problema não informado
1. Sistema identifica a ausência do tipo de problema ou dados inválidos.
2. Sistema impede o registro e solicita a correção.

**Regras de negócio relacionadas:**
RN-008

**Requisitos relacionados:**
RF-008
 
---
