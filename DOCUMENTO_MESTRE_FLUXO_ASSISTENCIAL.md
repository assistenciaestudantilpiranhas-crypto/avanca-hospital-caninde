# Documento Mestre do Fluxo Assistencial do Paciente

Este documento define a regra funcional de referência para o fluxo assistencial do paciente no protótipo GSI Saúde. Antes de qualquer alteração em fluxo assistencial, status do paciente, tempos, indicadores, consulta, triagem, observação, sala de estabilização, transferência, enfermagem, farmácia, exames ou desfechos, este documento deve ser lido obrigatoriamente.

## Princípios

- O sistema é um protótipo visual, sem backend real e sem banco de dados real.
- Todos os dados são fictícios e persistidos em `localStorage` por meio de `GsiApi`.
- Nenhuma mudança deve criar dados reais de pacientes, CNES, CPF, CNS, indicadores oficiais ou informações institucionais não validadas.
- O fluxo assistencial deve preservar rastreabilidade: entrada, triagem, classificação, consulta, observação, estabilização, exames, medicação, transferência e desfecho.
- Status de paciente e tempos assistenciais só devem mudar por ação funcional explícita do usuário ou regra já existente no fluxo.
- Indicadores e relatórios devem usar registros existentes, sem inventar horários ou resultados.

## Entrada do Paciente

O paciente entra no sistema pela recepção/porta de entrada ou pelo cadastro direto.

Campos esperados quando disponíveis:

- `horaChegada`
- `horaChegadaTs`
- identificação fictícia do paciente
- município/origem
- queixa principal
- status inicial, geralmente `Aguardando triagem`

Regra:

- A chegada representa o início da permanência do paciente na unidade.
- A permanência deve ser calculada a partir de `horaChegadaTs` e `horaDesfechoTs`, quando ambos existirem.

## Triagem e Classificação de Risco

A triagem registra sinais vitais, queixa e classificação de risco.

Campos esperados quando disponíveis:

- `horaInicioTriagem`
- `horaInicioTriagemTs`
- `horaFimTriagem`
- `horaFimTriagemTs`
- `sinaisVitais`
- `triagemRisco`
- `classificacao`

Regra:

- A classificação final deve ser registrada por ação de triagem.
- A conclusão da triagem pode encaminhar o paciente para consulta ou outro fluxo previsto.
- Não alterar classificação, status ou horários de triagem fora das ações próprias da triagem.

## Consulta

A consulta atende pacientes classificados e pacientes em avaliação médica.

Campos esperados quando disponíveis:

- `horaChamadaConsulta`
- `horaInicioConsulta`
- `horaInicioConsultaTs`
- `profissionalResponsavel`
- `consultorioAtual`
- `conduta`

Regra:

- Chamar paciente para consulta não deve iniciar consulta automaticamente.
- Iniciar consulta registra início de atendimento médico.
- Registrar conduta pode encaminhar para alta, observação, sala de estabilização, exame, prescrição ou transferência regulada.
- Desfechos definitivos devem registrar `horaDesfecho` e `horaDesfechoTs` quando aplicável.

## Observação Clínica, Pediátrica e Obstétrica

A observação acompanha pacientes que precisam permanecer sob avaliação.

Campos esperados quando disponíveis:

- `observacaoClinica`
- `observacaoPediatrica`
- `observacaoObstetrica`
- `inicio`
- `inicioTimestamp`
- `origem`
- `reavaliacoes`

Regra:

- Paciente em observação permanece na fila correspondente até alta da observação, encaminhamento para estabilização, transferência ou outro desfecho validado.
- Reavaliações devem ser registradas manualmente.
- Alta da observação altera status/desfecho apenas por ação própria.

## Sala de Estabilização

A sala de estabilização acompanha pacientes graves ou instáveis.

Campos esperados quando disponíveis:

- `estabilizacao`
- `checklistEstabilizacao`
- `reavaliacoes`

Regra:

- O checklist de estabilização é individual por paciente.
- Marcar checklist não deve conceder alta, transferir ou alterar desfecho automaticamente.
- Paciente permanece em estabilização até nova conduta profissional.

## Exames

Exames são solicitações vinculadas ao paciente e ao fluxo assistencial.

Campos esperados quando disponíveis:

- `pacienteId`
- `paciente`
- `exame`
- `tipo`
- `origem`
- `solicitante`
- `horario`
- `status`
- `prioridade`
- `resultado`
- `horarioLiberacao`

Regra:

- Solicitar exame não altera o desfecho do paciente automaticamente.
- Resultado crítico deve ser registrado como status próprio quando aplicável.
- Indicadores de exames devem usar horários existentes, sem criar tempos fictícios.

## Farmácia e Prescrição

Prescrições e dispensações apoiam o fluxo assistencial.

Campos esperados quando disponíveis:

- `paciente`
- `medicamento`
- `dose`
- `via`
- `horario`
- `prescritor`
- `status`

Regra:

- Prescrever ou dispensar medicação não deve alterar status assistencial do paciente automaticamente, salvo regra explicitamente definida.
- Falta de medicamento deve ser registrada como status da prescrição/estoque, não como desfecho do paciente.

## Transferências

A transferência representa regulação, preparação, saída e desfecho assistencial.

Campos já usados quando disponíveis:

- `pacienteId`
- `paciente`
- `motivo`
- `destino`
- `status`
- `acompanhante`
- `checklist`
- `saida`
- `tipoTransporte`
- `usouAmbulancia`

Campos recomendados quando for necessário reforçar rastreabilidade:

- `horaSolicitacaoTransferencia`
- `horaSolicitacaoTransferenciaTs`
- `horaAprovacaoVaga`
- `horaAprovacaoVagaTs`
- `horaSaidaTransferencia`
- `horaSaidaTransferenciaTs`

Regra:

- O paciente entra em Transferências quando há solicitação de transferência/regulação.
- Enquanto não houver saída confirmada, a transferência permanece em andamento.
- Aprovar vaga deve alterar apenas o status de regulação, por exemplo `Vaga confirmada`, sem retirar o paciente da lista de andamento.
- Completar checklist deve abrir modal ou caixa de checklist.
- O clique no botão da tabela não deve concluir automaticamente o checklist.
- O checklist só deve ficar `Completo` após confirmação explícita dentro do modal.
- Confirmar saída representa a conclusão real da transferência.
- Ao confirmar saída, o sistema deve registrar horário de saída, atualizar status/desfecho do paciente para `Transferência regulada` ou equivalente validado, retirar da lista de transferências em andamento e manter o registro para histórico, indicadores e relatórios.
- Transferências concluídas não devem aparecer na tabela de transferências em andamento.
- Histórico de transferências deve permanecer nos dados e em relatórios/indicadores já existentes. Não criar nova seção de concluídos sem autorização.

## Desfechos

Desfechos encerram ou redirecionam o atendimento.

Exemplos de desfecho:

- `Alta`
- `Alta da observação`
- `Medicação e alta`
- `Transferência regulada`
- `Evasão/desistência`
- `Óbito`
- `Sala de estabilização`
- `Observação Clínica`
- `Observação Pediátrica`
- `Observação Obstétrica`

Regra:

- Desfecho definitivo deve registrar horário de desfecho quando aplicável.
- Desfechos não devem ser alterados por ações visuais ou por simples navegação de tela.
- Não apagar histórico assistencial ao mudar status.

## Tempos Assistenciais

Tempos devem ser calculados com base em campos existentes.

Tempos principais:

- chegada até triagem
- triagem até consulta
- consulta até desfecho
- permanência na unidade
- solicitação de transferência até saída, quando os campos existirem
- aprovação de vaga até saída, quando os campos existirem

Regra:

- Não inventar horários para completar indicadores.
- Se um campo não existir, exibir `Sem dados suficientes`, `Aguardando registro` ou `a validar`, conforme contexto.
- Campos `Ts` devem ser usados para cálculo quando existirem.

## Indicadores e Relatórios

Indicadores e relatórios devem ler dados já registrados.

Regra:

- Não alterar indicador para compensar falha de fluxo sem corrigir a origem do dado.
- Não remover registros concluídos da base, pois eles alimentam relatórios e indicadores.
- Transferências concluídas devem sair da lista operacional de andamento, mas permanecer disponíveis para relatórios e indicadores.

## Regra de Segurança Para Alterações

Antes de alterar qualquer trecho relacionado a fluxo assistencial, status do paciente, tempos, indicadores, consulta, triagem, observação, sala de estabilização, transferência, enfermagem, farmácia, exames ou desfechos:

1. Ler este documento.
2. Identificar quais status e horários serão afetados.
3. Confirmar se a alteração muda fluxo assistencial ou apenas apresentação visual.
4. Fazer a menor mudança possível.
5. Preservar dados fictícios e compatibilidade com publicação estática.
6. Testar o caminho funcional afetado.
