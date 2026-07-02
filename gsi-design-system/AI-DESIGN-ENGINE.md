# AI Design Engine

O AI Design Engine define como agentes de IA devem usar o GSI Design System para criar, revisar ou adaptar interfaces do GSI ONE e do Avanca Hospital.

## Regra principal

Quando a tarefa for visual, o agente deve alterar somente a camada visual. E proibido modificar fluxo funcional, regra de negocio, integracao, Supabase, localStorage, autenticacao, permissoes ou auditabilidade sem autorizacao explicita.

## Antes de alterar uma tela

O agente deve identificar:

- objetivo da mudanca;
- arquivos afetados;
- componentes envolvidos;
- impacto em UX clinica;
- impacto em acessibilidade;
- risco para fluxo assistencial;
- validacao possivel.

## Criacao de novas telas

Novas telas devem:

- seguir tokens do GDS;
- usar componentes padronizados;
- priorizar informacao clinica e operacional;
- manter densidade adequada para ambiente hospitalar;
- prever responsividade;
- prever foco visivel e navegacao por teclado;
- documentar qualquer lacuna funcional.

## Preservacao obrigatoria

Agentes devem preservar:

- IDs existentes;
- nomes de funcoes;
- eventos;
- seletores usados por JavaScript;
- classes estruturais;
- atributos de dados;
- regras de negocio;
- fluxos assistenciais;
- integracoes;
- Supabase;
- localStorage;
- auditabilidade.

## Revisao de consistencia

Ao revisar telas, o agente deve comparar cores, tipografia, espacamento, cards, botoes, formularios, tabelas, badges, modais, estados e responsividade com o GDS.

## Saida esperada

Toda entrega deve informar arquivos alterados, impacto visual, impacto em workflow, impacto em banco/integracoes, validacao realizada, riscos e status de commit/push.

