# Mapa de Fluxos

**Projeto:** Share+

---

### "Cadastrar assinatura"

**Administrador**
1. Cadastrar serviço e plano
2. Informar valor, periodicidade e vencimento
3. Definir quantidade de vagas
4. Escolher como os membros entrarão (convite direto, link privado ou marketplace)

---

### "Entrar no grupo"

**Membro**
1. Receber convite ou encontrar vaga disponível
2. Verificar condições do grupo, valor da divisão e regras do serviço
3. Confirmar entrada

> **Exceções:**
> - Convite expirado
> - Vaga já preenchida
> - Serviço com restrição de compatibilidade

---

### "Dividir custos"

**Sistema**
1. Identificar o valor total do grupo
2. Calcular a cota individual com base no número de participantes
3. Recalcular a cota automaticamente quando o número de participantes do grupo mudar

> **Exceções:**
> - Grupo sem membros ativos suficientes para a divisão

---

### "Realizar pagamento"

**Membro**
1. Visualizar a cobrança
2. Realizar o pagamento
3. Enviar o comprovante
4. Aguardar confirmação de ativação

> **Exceções:**
> - Cobrança indevida
> - Comprovante não enviado
> - Pagamento em atraso (pendente)

---

### "Confirmar acesso"

**Membro**
1. Receber o convite/acesso ao serviço
2. Confirmar que conseguiu utilizá-lo
3. Ter o estado da participação atualizado para "ativo"

> **Exceções:**
> - Falha de acesso (gera um incidente)

---

### "Registrar incidente"

**Administrador / Membro**
1. Identificar o problema (falha de acesso, remoção, convite expirado, cobrança indevida, indisponibilidade)
2. Registrar o incidente
3. Manter as ações tomadas no histórico até a resolução

> **Exceções:**
> - Nenhuma adicional identificada
