# Motion

Motion no GDS deve ser discreto, funcional e seguro. Em contexto clinico, animacoes existem para orientar atencao, indicar mudanca de estado e reduzir desorientacao, nunca para decorar.

## Quando usar

- Abertura e fechamento de modais.
- Entrada de alertas.
- Mudanca de status.
- Destaque temporario de paciente critico.
- Confirmacao visual de acao executada.
- Transicao curta entre paineis ou filtros.

## Quando evitar

- Animacoes longas ou repetitivas.
- Efeitos que atrasem acao clinica.
- Movimento que dispute atencao com pacientes criticos.
- Parallax, excesso de escala, giro ou efeitos decorativos.
- Animacoes em tabelas densas que prejudiquem leitura.

## Duracao

- Microinteracoes: 120 a 180 ms.
- Transicoes de superficies: 180 a 240 ms.
- Modais e overlays: ate 260 ms.
- Destaque critico: curto, claro e sem loop infinito por padrao.

## Modais

Modais podem usar fade e deslocamento leve. O movimento deve ajudar a entender origem e hierarquia, sem atrasar confirmacao ou cancelamento.

## Alertas

Alertas devem aparecer de forma perceptivel. Alertas criticos podem receber destaque inicial, mas nao devem piscar continuamente.

## Mudanca de status

Mudancas de status podem usar transicao de cor ou realce temporario. O estado final deve permanecer claro sem depender da animacao.

## Pacientes criticos

Destaques para pacientes criticos devem ser usados com criterio. O objetivo e chamar atencao para risco real, mantendo legibilidade e evitando fadiga visual.

