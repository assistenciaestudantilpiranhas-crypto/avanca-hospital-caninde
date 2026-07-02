# Guia Pratico de Interface para Agentes de IA

Este documento resume as regras objetivas do GSI Design System para alteracoes futuras de interface no GSI ONE e no Avanca Hospital.

## Regras gerais

- Preserve fluxo funcional, IDs, classes estruturais, funcoes, eventos, atributos de dados, Supabase, localStorage e integracoes.
- Altere apenas a camada visual quando a tarefa for visual.
- Mantenha a identidade existente: azul-petroleo/navy, verde institucional/teal, neutros frios e estados clinicos claros.
- Evite refatoracoes amplas, reescrita de arquivos grandes e mudancas globais sem necessidade.
- Nao altere regra de negocio, persistencia, autenticacao, permissao, auditoria ou fluxo assistencial sem autorizacao explicita.

## Cores

- Primaria institucional: navy/azul-petroleo.
- Acao positiva ou confirmacao: verde institucional/teal.
- Neutros: fundos claros, bordas frias, texto escuro de alto contraste.
- Alertas clinicos: vermelho, laranja, amarelo, verde e azul devem manter significado consistente.
- Nunca use cor como unico indicador de estado.

## Tipografia

- Fonte preferencial: Inter, Segoe UI, Arial, Helvetica, sans-serif.
- Titulos devem ser objetivos e hierarquicos.
- Texto clinico deve priorizar leitura rapida, legibilidade e contraste.
- Evite tamanhos muito pequenos em informacoes assistenciais.

## Espacamento

- Use escala consistente: 4, 8, 12, 16, 20, 24, 32 e 40 px.
- Agrupe informacoes por proximidade visual.
- Preserve densidade adequada para ambiente hospitalar, sem excesso de espaco editorial.

## Cards

- Use cards para itens repetidos, resumos, pacientes, indicadores e paineis.
- Radius moderado, borda discreta e sombra suave.
- Informacao critica deve aparecer no topo ou na area de maior leitura.
- Nao coloque cards dentro de cards quando uma secao simples resolver.

## Botoes

- Primario: acao principal da tela.
- Secundario: acoes alternativas.
- Perigoso: exclusao, cancelamento critico ou acao irreversivel.
- Desabilitado: contraste reduzido, sem parecer clicavel.
- Todo botao deve ter rotulo claro, estado de foco e area de toque adequada.

## Tabelas

- Cabecalhos fixos quando houver muita rolagem.
- Linhas com boa altura, separadores discretos e estados de foco/hover.
- Dados criticos devem ser escaneaveis em poucos segundos.
- Evite truncar identificacao, risco, tempo de espera e status clinico.

## Formularios

- Labels sempre visiveis.
- Erros proximos ao campo.
- Campos obrigatorios claramente indicados.
- Inputs, selects e textareas devem manter foco visivel e contraste adequado.
- Nao remova campos clinicos, administrativos ou de auditoria sem autorizacao explicita.

## Modais

- Use modais para decisao, confirmacao ou edicao contextual.
- Evite modais para fluxos longos.
- Sempre inclua fechamento acessivel, foco inicial coerente e retorno de foco ao elemento de origem.

## Badges

- Badges devem indicar status, risco, fila, prioridade, tipo de atendimento ou etapa.
- Mantenha texto curto e cor semantica.
- Combine cor com texto ou icone para nao depender apenas da cor.

## Responsividade

- Interfaces devem funcionar em notebooks, tablets, monitores antigos e TVs.
- A leitura clinica deve permanecer clara entre sidebar, tabelas, cards e paineis.
- Em telas menores, priorize identificacao do paciente, risco, status, tempo e proxima acao.
- Em paineis e TVs, aumente legibilidade sem esconder status, fila, risco ou indicadores relevantes.
