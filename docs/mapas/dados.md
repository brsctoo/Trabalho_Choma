# Mapa de Dados

**Projeto:** Share+

---

## Entidades e responsabilidades

- **Usuário** — conta, identificação, contato, dados de pagamento e reputação.
- **Serviço/Plano** — nome do serviço, plano, periodicidade, limite de membros e regras de compatibilidade.
- **Grupo** — administrador, plano associado, status, vagas, valor total e configurações da divisão.
- **Participação** — relação entre usuário e grupo, cota, estado, datas de entrada/saída e confirmação de acesso.
- **Transação** — membro, grupo, valor, vencimento, data de pagamento, comprovante e status.
- **Incidente** — tipo do problema, participante, grupo, descrição, estado, histórico, ações tomadas e resolução.
- **Avaliação/Reputação** — nota, histórico de ocorrências e indicadores avaliativos do grupo/administrador.

## Relações (em linguagem natural)

- Um Usuário pode administrar vários Grupos.
- Cada Grupo possui um único Administrador principal.
- Um Grupo tem muitas Participações.
- Uma Participação pertence a um Usuário e a um Grupo.
- Um Serviço/Plano pode estar associado a vários Grupos.
- Um Grupo está vinculado a um Serviço/Plano, herdando suas regras de compatibilidade.
- Um Grupo tem muitas Transações.
- Uma Transação pertence a um Membro (Usuário) e a um Grupo.
- Um Grupo tem muitos Incidentes.
- Um Incidente pertence a um Grupo e a um Participante.
- Uma Avaliação/Reputação está associada a um Usuário (podendo refletir a saúde do Grupo que ele administra).
