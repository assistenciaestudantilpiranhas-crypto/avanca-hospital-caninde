# GSI Documentation Standard

## 1. Objetivo

Este documento registra o padrao oficial de documentacao do GSI ONE / Avanca Hospital.

Toda documentacao tecnica, operacional, institucional, de integracao, seguranca, APIs governamentais e decisoes tecnicas do GSI ONE deve seguir o padrao definido em `GHAES-0009-DOCUMENTATION-STANDARD.md`.

## 2. Escopo

Este padrao se aplica a documentos produzidos, mantidos ou versionados no contexto do GSI ONE e do programa Avanca Hospital, incluindo:

- documentacao tecnica da plataforma;
- documentacao operacional de uso e suporte;
- documentacao institucional do ecossistema;
- documentacao de integracoes;
- documentacao de seguranca, LGPD e auditoria;
- documentacao de APIs governamentais;
- registros de decisoes tecnicas.

Este documento nao cria integracoes, regras clinicas, regras operacionais, modelos de banco, politicas de acesso ou alteracoes de sistema.

## 3. Referencia Ao Padrao GHAES-0009

O padrao oficial de referencia e `GHAES-0009-DOCUMENTATION-STANDARD.md`.

Qualquer documento do GSI ONE deve observar as diretrizes desse padrao antes de ser considerado oficial, aprovado, publicado ou usado como referencia tecnica, operacional ou institucional.

Em caso de conflito entre documentos locais e o padrao GHAES-0009, o conflito deve ser registrado e encaminhado para decisao tecnica antes de qualquer alteracao estrutural.

## 4. Aplicacao No GSI ONE

No GSI ONE, a documentacao deve preservar a arquitetura institucional do ecossistema:

- GSI HealthTech como ecossistema institucional e marca guarda-chuva;
- GSI ONE como plataforma digital de saude;
- Avanca Hospital como programa de implementacao e caso hospitalar;
- este repositorio como fonte de interfaces, telas, logica local e prototipos de fluxos assistenciais.

Documentos devem ser objetivos, rastreaveis e alinhados ao contexto da plataforma. Nenhum documento deve alterar fluxos assistenciais, campos clinicos, auditoria, integracoes ou regras operacionais sem aprovacao explicita.

## 5. Familias Documentais Usadas No Projeto

As familias documentais oficiais usadas no projeto sao:

- `GSI-ONE`: documentacao institucional, tecnica e operacional da plataforma GSI ONE;
- `API`: documentacao de APIs, contratos, payloads, integracoes e comunicacao entre sistemas;
- `SEC`: documentacao de seguranca, privacidade, LGPD, auditoria, rastreabilidade e controles;
- `DB`: referencia externa para documentacao de banco de dados, sem modificacao direta de arquivos de banco neste repositorio;
- `AVH`: documentacao especifica do Avanca Hospital como programa de implementacao e caso hospitalar.

## 6. Estrutura Minima Obrigatoria Dos Documentos

Todo documento oficial deve conter, quando aplicavel:

- titulo claro e identificavel;
- objetivo;
- escopo;
- contexto;
- referencias internas;
- regras ou diretrizes aplicaveis;
- impactos esperados;
- limites e nao escopo;
- status documental;
- responsavel ou area responsavel, quando definido;
- historico ou criterio de revisao, quando aplicavel;
- proximas acoes ou pendencias.

Documentos tecnicos devem explicitar premissas, dependencias, impactos, riscos e pontos pendentes. Documentos operacionais devem separar orientacao, regra vigente e decisao pendente.

## 7. Status Documentais Oficiais

Os status documentais oficiais sao:

- `Draft`: documento em elaboracao, ainda sem aprovacao final;
- `Review`: documento em revisao tecnica, institucional, operacional ou juridica;
- `Approved`: documento aprovado para uso oficial;
- `Deprecated`: documento substituido ou descontinuado, mantido apenas para rastreabilidade;
- `Superseded`: documento substituido por outro documento oficial;
- `Archived`: documento preservado para historico, sem uso operacional vigente.

Documentos sem status explicito devem ser tratados como nao aprovados para uso oficial.

## 8. Regras De Linguagem

A documentacao deve usar linguagem tecnica, institucional e objetiva.

Devem ser evitados:

- ambiguidades;
- promessas comerciais sem base tecnica;
- termos informais em documentos oficiais;
- conclusoes clinicas nao aprovadas;
- regras operacionais nao formalizadas;
- referencias a fontes externas nao adotadas oficialmente;
- marcas de autoria automatizada.

Quando uma informacao depender de decisao futura, o documento deve registrar o ponto como pendente, e nao como regra vigente.

## 9. Regras Para Documentacao De APIs Governamentais

Documentos sobre APIs governamentais devem registrar apenas informacoes verificadas, aprovadas ou explicitamente pendentes.

Esses documentos devem conter, quando aplicavel:

- nome da API ou servico;
- orgao ou fonte responsavel;
- finalidade da integracao;
- status da integracao;
- requisitos de autenticacao e autorizacao, quando conhecidos;
- dados trafegados;
- limites de uso;
- riscos operacionais;
- dependencias externas;
- pendencias de validacao;
- impacto sobre privacidade, seguranca e auditoria.

Nenhum documento deve afirmar que uma integracao governamental existe, esta homologada ou esta em producao sem confirmacao formal.

## 10. Regras Para Documentacao De Seguranca, LGPD E Auditoria

Documentos de seguranca, LGPD e auditoria devem preservar rastreabilidade, minimizacao de dados, controle de acesso e responsabilidade institucional.

Devem ser documentados, quando aplicavel:

- finalidade do tratamento de dados;
- categorias de dados envolvidas;
- perfis ou areas com acesso;
- controles de seguranca;
- eventos auditaveis;
- retencao e descarte, quando definidos;
- riscos conhecidos;
- medidas de mitigacao;
- pendencias juridicas, tecnicas ou operacionais.

Nenhum documento deve remover, reduzir ou omitir requisitos de auditoria, rastreabilidade, privacidade ou seguranca previamente definidos sem aprovacao explicita.

## 11. Regras Para Decisoes Tecnicas

Decisoes tecnicas devem ser documentadas de forma rastreavel, incluindo:

- contexto;
- problema;
- alternativas consideradas;
- decisao adotada;
- justificativa;
- impactos;
- riscos;
- dependencias;
- pontos pendentes;
- criterio de revisao.

Quando a decisao afetar fluxos assistenciais, dados de pacientes, autenticacao, permissoes, banco de dados, auditoria, seguranca ou integracoes, o documento deve indicar a necessidade de aprovacao explicita antes de implementacao.

## 12. Proximas Acoes

As proximas acoes para consolidacao deste padrao sao:

- alinhar novos documentos ao padrao `GHAES-0009-DOCUMENTATION-STANDARD.md`;
- classificar documentos existentes conforme as familias documentais oficiais;
- adicionar status documental aos documentos que ainda nao possuem status;
- registrar pendencias de documentacao sem transforma-las em regra vigente;
- revisar documentacao sensivel antes de qualquer uso operacional oficial.
