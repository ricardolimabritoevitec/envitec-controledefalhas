# EnvitecEnergy — Sistema Web de Controle de Falhas

Repositório de acompanhamento do desenvolvimento da EnvitecEnergy.

## Estado atual
- Base operacional de referência: **v1.10** (Supabase + PostgreSQL; HTML/JS).
- **v1.11: revisão técnica PARCIAL, não homologada e não pronta para produção.**
- O pacote de revisão v1.11 foi disponibilizado na conversa do projeto, mas seus arquivos-fonte ainda **não foram publicados neste repositório**.
- Este repositório não representa uma implantação nem alteração do banco Supabase.

## Revisão v1.11 — ajustes preparados localmente
- Correção de colisão de nome que provocava `checkDate is not a function` (melhoria 98).
- Fluxo de retorno ao relatório mensal quando o formulário retroativo tem essa origem (70).
- Seleção de data pendente, destaque Expandir/Recolher (93) e identificação da tecnologia na análise (95).
- Sem validação contra o banco real.

## Ainda pendente para uma v1.11 completa
- Falhas simultâneas de geração e comunicação, com estado/duração/normalização independentes (92).
- Exclusão administrativa definitiva de registros com auditoria e integridade (94).
- Complementos do Administrador sem substituir análises técnicas (96).
- Conferência e implementação de todas as melhorias históricas aprovadas ainda não entregues.
- Testes de RLS, concorrência, relatórios mensais e regressão nos três perfis.

## Regras obrigatórias
- **Administrador:** único perfil com exclusão definitiva de locais e registros do histórico.
- **Administrador e Monitoramento:** podem desativar e reativar tecnologias/locais segundo permissões do banco.
- Local sem tecnologias ativas não aparece no Controle de Falhas, mas permanece cadastrado; reaparece ao adicionar/reativar uma tecnologia ativa.
- Botão **Voltar à tela de origem** para todos os perfis, inclusive Análise Técnica.
- Não inserir senhas, tokens secretos, `service_role` ou credenciais do PostgreSQL em commits.
- Não executar scripts SQL históricos novamente nem modificar a produção antes de homologar e revisar backups.

## Próximos passos
Publicar o código-fonte v1.10 validado e o pacote v1.11 de revisão em branch isolada, conferir a diferença e abrir um PR de desenvolvimento. Até isso acontecer, este README é apenas o registro do projeto.
