# EnvitecEnergy — Pacote de melhorias v1.11 (candidata)

## Regra operacional confirmada

- **Administrador:** único perfil autorizado a excluir locais e registros operacionais definitivamente.
- **Administrador e Monitoramento:** podem cadastrar/desativar/reativar tecnologias conforme controles e RLS.
- **Local sem tecnologia ativa:** não aparece no Controle de Falhas, mas permanece no cadastro e conserva histórico.
- **Nova tecnologia ativa ou reativação:** o mesmo local reaparece no Controle de Falhas, sem recadastramento.
- **Voltar (70):** retorna à janela de origem nos três perfis (Administrador, Monitoramento e Análise Técnica).

## Incorporações a partir da v1.10

| Nº | Melhoria | Perfis | Estado no código candidato |
|---|---|---|---|
| 13/61/83 | Gerenciamento, desativação e reativação de locais/tecnologias | ADM/MON | Filtros e cadastro de local inativo ajustados; validação RLS pendente |
| 27/58 | Continuidade de falha com formulário, observação e confirmação | ADM/MON | Preservada e integrada ao novo registro por canal |
| 70/88 | Voltar à janela de origem | Todos | Registro retroativo corrigido; regressão completa de navegação pendente |
| 73/90 | Dias pendentes: somente datas exigíveis e registros reais | ADM/MON | Código existente preservado; conferência de competência/histórico pendente |
| 92 | Falhas simultâneas geração/comunicação e duração própria | Todos | Novas tabelas, RPC e telas implementadas; reconciliação histórica e homologação pendentes |
| 93 | Realce Expandir/Recolher | Todos | Implementado |
| 94 | Exclusão administrativa definitiva do histórico | ADM | Seleção, confirmação, RPC e auditoria implementadas; casos com vínculos protegidos ainda bloqueados |
| 95 | Identificação de local, planta e fabricante na análise | ADM/TEC | Implementada |
| 96 | Complemento administrativo sem substituir análise técnica | ADM; leitura por perfis autorizados | Tabela, RPC e interface implementados; testes RLS pendentes |
| 97 | Relatórios por local no Monitoramento | ADM/MON | Interface existente preservada |
| 98 | Erro `checkDate` e retorno de registro retroativo | ADM/MON | Corrigido no código; teste real de RPC pendente |

## Melhorias históricas preservadas da base v1.10

- 01–04 e 36–38: indicadores, planos, vigências e filtros contratuais.
- 06–10: potência instalada, visualização do histórico, horários e anexos.
- 11–23: cadastros de clientes/tecnologias, contratos, perfil e gerenciamento de usuários.
- 24–35: registro, normalização, continuidade, histórico, calendário e revisões técnicas.
- 40–47: relatórios por local, plataforma de monitoramento, confirmações e contas.
- 49–69: indicadores operacionais, filtros, confirmações, comunicação, pendências, anexos e relatórios.
- 71–91: navegação, tratamento de dados, proteção de formulários, contas, histórico e melhorias de apresentação.

*Preservadas* significa que estes componentes continuam na base do código. Não equivale a homologação integral de cada número após a v1.11.

## Melhoria 92 — comportamento

1. Uma tecnologia pode manter simultaneamente uma falha de geração e uma falha de comunicação.
2. Cada canal tem data de abertura, duração, atualização e resolução próprias.
3. A recuperação de comunicação não encerra automaticamente a falha de geração.
4. Os indicadores por cliente não somam o mesmo cliente duas vezes.
5. O relatório mensal inclui eventos classificados por comunicação e geração.
6. Registros antigos são conciliados inicialmente por ocorrência aberta; ambiguidades exigem revisão humana.

## Melhoria 94 — integridade

A exclusão é permanente nas tabelas operacionais e gera auditoria administrativa separada (IDs, autor, horário, motivo e quantidades). Por proteção, o RPC bloqueia exclusão com anexos no Storage, complementos administrativos ou ocorrências vinculadas a canais independentes; exige tratamento prévio. Isso não é ocultação de registros: quando autorizada, a exclusão elimina as linhas operacionais e recalcula o estado atual.

## Pendências antes de produção

- Aplicar migração apenas em uma base de **homologação com backup restaurável**.
- Testar todas as permissões reais com as três contas, incluindo tentativas indevidas.
- Validar simultaneidade, filtros, duração, normalização independente, análise específica por ocorrência.
- Testar envio/visualização de fotos e o tratamento administrativo dos vínculos que impedem exclusão.
- Comparar o PDF gerado ao modelo fornecido; validar meses incompletos e períodos de desativação.
- Revisar todas as melhorias históricas que continuem parcialmente atendidas.

## Fora do escopo aprovado para esta implantação

- 48 — Foto de Perfil: adiada.
- 82 — Integração WhatsApp Web: adiada.
