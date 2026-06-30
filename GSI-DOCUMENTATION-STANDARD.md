# GSI Documentation Standard

## 1. Objetivo

Este documento registra o padrão oficial de documentação do GSI ONE / Avança Hospital.

Toda documentação técnica, operacional, institucional, de integração, segurança, APIs governamentais e decisões técnicas do GSI ONE deve seguir o padrão definido em `GHAES-0009-DOCUMENTATION-STANDARD.md`.

## 2. Escopo

Este padrão se aplica a documentos produzidos, mantidos ou versionados no contexto do GSI ONE e do programa Avança Hospital, incluindo:

- documentação técnica da plataforma;
- documentação operacional de uso e suporte;
- documentação institucional do ecossistema;
- documentação de integrações;
- documentação de segurança, LGPD e auditoria;
- documentação de APIs governamentais;
- registros de decisões técnicas.

Este documento não cria integrações, regras clínicas, regras operacionais, modelos de banco, políticas de acesso ou alterações de sistema.

## 3. Referência ao Padrão GHAES-0009

O padrão oficial de referência é `GHAES-0009-DOCUMENTATION-STANDARD.md`.

Qualquer documento do GSI ONE deve observar as diretrizes desse padrão antes de ser considerado oficial, aprovado, publicado ou usado como referência técnica, operacional ou institucional.

Em caso de conflito entre documentos locais e o padrão GHAES-0009, o conflito deve ser registrado e encaminhado para decisão técnica antes de qualquer alteração estrutural.

## 4. Aplicação no GSI ONE

No GSI ONE, a documentação deve preservar a arquitetura institucional do ecossistema:

- GSI HealthTech como ecossistema institucional e marca guarda-chuva;
- GSI ONE como plataforma digital de saúde;
- Avança Hospital como programa de implementação e caso hospitalar;
- este repositório como fonte de interfaces, telas, lógica local e protótipos de fluxos assistenciais.

Documentos devem ser objetivos, rastreáveis e alinhados ao contexto da plataforma. Nenhum documento deve alterar fluxos assistenciais, campos clínicos, auditoria, integrações ou regras operacionais sem aprovação explícita.

## 5. Famílias Documentais Usadas no Projeto

As famílias documentais oficiais usadas no projeto são:

- `GSI-ONE`: documentação institucional, técnica e operacional da plataforma GSI ONE;
- `API`: documentação de APIs, contratos, payloads, integrações e comunicação entre sistemas;
- `SEC`: documentação de segurança, privacidade, LGPD, auditoria, rastreabilidade e controles;
- `DB`: referência externa para documentação de banco de dados, sem modificação direta de arquivos de banco neste repositório;
- `AVH`: documentação específica do Avança Hospital como programa de implementação e caso hospitalar.

## 6. Estrutura Mínima Obrigatória dos Documentos

Todo documento oficial deve conter, quando aplicável:

- título claro e identificável;
- objetivo;
- escopo;
- contexto;
- referências internas;
- regras ou diretrizes aplicáveis;
- impactos esperados;
- limites e não escopo;
- status documental;
- responsável ou área responsável, quando definido;
- histórico ou critério de revisão, quando aplicável;
- próximas ações ou pendências.

Documentos técnicos devem explicitar premissas, dependências, impactos, riscos e pontos pendentes. Documentos operacionais devem separar orientação, regra vigente e decisão pendente.

## 7. Status Documentais Oficiais

Os status documentais oficiais são:

- `Draft`: documento em elaboração, ainda sem aprovação final;
- `Em revisão`: documento em revisão técnica, institucional, operacional ou jurídica;
- `Aprovado`: documento aprovado para uso oficial;
- `Em uso`: documento vigente e utilizado como referência oficial;
- `Substituído`: documento substituído por outro documento oficial, mantido para rastreabilidade;
- `Arquivado`: documento preservado para histórico, sem uso operacional vigente.

Documentos sem status explícito devem ser tratados como não aprovados para uso oficial.

## 8. Regras de Linguagem

A documentação deve usar linguagem técnica, institucional e objetiva.

Devem ser evitados:

- ambiguidades;
- promessas comerciais sem base técnica;
- termos informais em documentos oficiais;
- conclusões clínicas não aprovadas;
- regras operacionais não formalizadas;
- referências a fontes externas não adotadas oficialmente;
- marcas de autoria automatizada.

Quando uma informação depender de decisão futura, o documento deve registrar o ponto como pendente, e não como regra vigente.

## 9. Regras para Documentação de APIs Governamentais

Documentos sobre APIs governamentais devem registrar apenas informações verificadas, aprovadas ou explicitamente pendentes.

Esses documentos devem conter, quando aplicável:

- nome da API ou serviço;
- órgão ou fonte responsável;
- finalidade da integração;
- status da integração;
- requisitos de autenticação e autorização, quando conhecidos;
- dados trafegados;
- limites de uso;
- riscos operacionais;
- dependências externas;
- pendências de validação;
- impacto sobre privacidade, segurança e auditoria.

Nenhum documento deve afirmar que uma integração governamental existe, está homologada ou está em produção sem confirmação formal.

## 10. Regras para Documentação de Segurança, LGPD e Auditoria

Documentos de segurança, LGPD e auditoria devem preservar rastreabilidade, minimização de dados, controle de acesso e responsabilidade institucional.

Devem ser documentados, quando aplicável:

- finalidade do tratamento de dados;
- categorias de dados envolvidas;
- perfis ou áreas com acesso;
- controles de segurança;
- eventos auditáveis;
- retenção e descarte, quando definidos;
- riscos conhecidos;
- medidas de mitigação;
- pendências jurídicas, técnicas ou operacionais.

Nenhum documento deve remover, reduzir ou omitir requisitos de auditoria, rastreabilidade, privacidade ou segurança previamente definidos sem aprovação explícita.

## 11. Regras para Decisões Técnicas

Decisões técnicas devem ser documentadas de forma rastreável, incluindo:

- contexto;
- problema;
- alternativas consideradas;
- decisão adotada;
- justificativa;
- impactos;
- riscos;
- dependências;
- pontos pendentes;
- critério de revisão.

Quando a decisão afetar fluxos assistenciais, dados de pacientes, autenticação, permissões, banco de dados, auditoria, segurança ou integrações, o documento deve indicar a necessidade de aprovação explícita antes de implementação.

## 12. Próximas Ações

As próximas ações para consolidação deste padrão são:

- alinhar novos documentos ao padrão `GHAES-0009-DOCUMENTATION-STANDARD.md`;
- classificar documentos existentes conforme as famílias documentais oficiais;
- adicionar status documental aos documentos que ainda não possuem status;
- registrar pendências de documentação sem transformá-las em regra vigente;
- revisar documentação sensível antes de qualquer uso operacional oficial.
