# GOV-BR-API-ROADMAP.md

## Cabeçalho documental

| Campo | Valor |
|---|---|
| Código documental | API-001 |
| Projeto | GSI ONE / Avança Hospital |
| Documento | Roadmap de APIs governamentais |
| Versão | 0.1 |
| Status | Draft |
| Data | 2026 |
| Responsável | GSI HealthTech |
| Padrão documental | GSI-DOCUMENTATION-STANDARD.md; GHAES-0009-DOCUMENTATION-STANDARD.md |

## 1. Objetivo

Este documento é um roadmap técnico inicial, de caráter exploratório e institucional, sobre integrações futuras entre o GSI ONE, como plataforma digital de saúde implantada no programa Avança Hospital sob o ecossistema GSI HealthTech, e APIs ou sistemas governamentais ligados à saúde pública brasileira.

Este documento não autoriza o início de qualquer integração técnica real. Antes de qualquer implementação:

- credenciais de acesso devem ser solicitadas formalmente aos órgãos competentes;
- processos de homologação devem ser concluídos;
- eventuais convênios, termos de uso ou termos de cooperação entre município, secretaria, hospital e DATASUS ou Ministério da Saúde devem estar formalizados;
- autorização institucional expressa da direção hospitalar e/ou secretaria municipal de saúde deve preceder qualquer solicitação de acesso técnico.

Onde não houver confirmação documental oficial, o conteúdo deve ser tratado como `A validar no Portal de Serviços DATASUS`.

## 2. Escopo

Este roadmap cobre documentação preliminar, avaliação institucional e organização de fases para possível integração futura com APIs e sistemas governamentais.

Estão no escopo:

- identificação de APIs e sistemas prioritários;
- módulos do GSI ONE potencialmente impactados;
- critérios gerais de acesso;
- arquitetura segura recomendada;
- riscos de segurança, LGPD e auditoria;
- fases sugeridas para avaliação futura;
- pendências de validação oficial.

Ficam fora do escopo:

- implementação de integrações reais;
- criação de credenciais, certificados, tokens ou chaves;
- alteração de APIs, endpoints ou requisitos técnicos oficiais;
- alteração de banco de dados, migrations, RLS, autenticação, usuários ou permissões;
- confirmação de homologação ou produção de qualquer API.

## 3. Contexto

O GSI ONE poderá, em fases futuras e mediante autorização institucional, avaliar integrações com sistemas governamentais de saúde para apoiar cadastro, faturamento, regulação, farmácia, vigilância, indicadores e interoperabilidade clínica.

Toda integração com sistemas governamentais deve respeitar LGPD, sigilo assistencial, rastreabilidade, auditoria, controle de acesso por perfil e validação formal em ambiente de homologação antes de qualquer uso em produção.

O front-end do GSI ONE não deve chamar APIs governamentais diretamente. Qualquer integração futura deve usar backend intermediário seguro, responsável por autenticação, autorização, guarda de credenciais, logs, auditoria e comunicação com sistemas externos.

## 4. APIs priorizadas

### 4.1 CNS/CADSUS

- Finalidade provável: validação e consulta do Cartão Nacional de Saúde do paciente, apoiando o cadastro único de usuários do SUS.
- Módulo do GSI ONE impactado: Cadastro de Pacientes.
- Fase recomendada de integração: Fase 2, validações cadastrais, após autorização institucional.
- Tipo de dado envolvido: dado pessoal identificável, como nome, CNS, data de nascimento e filiação.
- Sensibilidade/LGPD: alta, por envolver dado pessoal associado à identificação em saúde; exige base legal e finalidade explícita.
- Critérios prováveis de acesso: cadastro institucional do hospital ou município, credenciamento e possivelmente certificado digital, a validar no Portal de Serviços DATASUS.
- Pendências de confirmação: endpoint técnico, protocolo de autenticação e SLA de disponibilidade, a validar no Portal de Serviços DATASUS.

### 4.2 CNES

- Finalidade provável: consulta de dados cadastrais do estabelecimento de saúde, incluindo leitos, serviços e profissionais vinculados.
- Módulo do GSI ONE impactado: Cadastro de Pacientes, Indicadores e Auditoria.
- Fase recomendada de integração: Fase 1, dados públicos ou de baixa sensibilidade, conforme disponibilidade confirmada.
- Tipo de dado envolvido: dado institucional e administrativo, em geral de caráter público.
- Sensibilidade/LGPD: baixa, por se tratar predominantemente de dados de estabelecimento, não de paciente.
- Critérios prováveis de acesso: consulta pública ou cadastro, a validar no Portal de Serviços DATASUS.
- Pendências de confirmação: formato de exportação ou API disponível e periodicidade de atualização, a validar no Portal de Serviços DATASUS.

### 4.3 SIGTAP

- Finalidade provável: consulta da tabela de procedimentos, medicamentos, órteses, próteses e materiais do SUS, para apoio a faturamento e codificação de procedimentos.
- Módulo do GSI ONE impactado: Consulta, Exames, Farmácia, Indicadores e Relatórios de faturamento SUS.
- Fase recomendada de integração: Fase 1, tabela de referência pública.
- Tipo de dado envolvido: dado tabular de referência, não associado a paciente individual.
- Sensibilidade/LGPD: baixa.
- Critérios prováveis de acesso: download de tabela ou consulta pública, a validar no Portal de Serviços DATASUS.
- Pendências de confirmação: existência de API formal versus disponibilização apenas por arquivo de competência mensal, a validar no Portal de Serviços DATASUS.

### 4.4 SISREG/e-SUS Regulação

- Finalidade provável: apoio à regulação de leitos, encaminhamentos e transferências entre unidades de saúde.
- Módulo do GSI ONE impactado: Transferências/Regulação, Atendimento/Recepção e Indicadores.
- Fase recomendada de integração: Fase 3, somente após pactuação formal com a gestão regional ou estadual da regulação.
- Tipo de dado envolvido: dado pessoal de saúde, incluindo condição clínica e justificativa de transferência.
- Sensibilidade/LGPD: alta, por envolver dado sensível de saúde vinculado a decisão assistencial.
- Critérios prováveis de acesso: pactuação com gestor de regulação municipal ou estadual, possivelmente com vínculo de unidade solicitante ou executante, a validar no Portal de Serviços DATASUS.
- Pendências de confirmação: modelo de integração disponível, API, webservice ou interface web institucional, a validar no Portal de Serviços DATASUS.

### 4.5 SI-BNAFAR

- Finalidade provável: apoio ao controle de estoque, dispensação e gestão da assistência farmacêutica no âmbito do SUS.
- Módulo do GSI ONE impactado: Farmácia, Indicadores e Auditoria.
- Fase recomendada de integração: Fase 4, após validação de requisitos de assistência farmacêutica municipal.
- Tipo de dado envolvido: dado de movimentação de insumos e medicamentos, podendo se vincular a dispensação individual a paciente.
- Sensibilidade/LGPD: média a alta, dependendo do nível de vinculação a paciente identificado.
- Critérios prováveis de acesso: cadastro da farmácia ou unidade no sistema nacional, a validar no Portal de Serviços DATASUS.
- Pendências de confirmação: disponibilidade de integração via API versus alimentação manual, a validar no Portal de Serviços DATASUS.

### 4.6 OBM

- Finalidade provável: apoio a indicadores de mortalidade ou morbidade para fins de observatório de saúde pública.
- Módulo do GSI ONE impactado: Observatório, Indicadores e Relatórios.
- Fase recomendada de integração: Fase 6.
- Tipo de dado envolvido: dado estatístico ou epidemiológico, possivelmente agregado.
- Sensibilidade/LGPD: variável, conforme nível de agregação dos dados, individualizado ou agregado/anonimizado.
- Critérios prováveis de acesso: a validar no Portal de Serviços DATASUS, pois a sigla ou sistema específico exige confirmação documental oficial.
- Pendências de confirmação: identificação exata do sistema ou API correspondente, a validar no Portal de Serviços DATASUS.

### 4.7 RNDS/SUS Digital

- Finalidade provável: interoperabilidade de dados clínicos em saúde, incluindo registros de atendimento, resultados de exames e histórico assistencial, no padrão da Rede Nacional de Dados em Saúde.
- Módulo do GSI ONE impactado: Consulta, Exames, Observação Clínica, Observação Pediátrica, Observação Obstétrica, Triagem e Auditoria.
- Fase recomendada de integração: Fase 5, somente com maturidade comprovada de segurança da informação.
- Tipo de dado envolvido: dado clínico sensível, podendo incluir diagnóstico, evolução clínica, exames e prescrições.
- Sensibilidade/LGPD: muito alta, por envolver dado de saúde individualizado e exigir controles reforçados de segurança e auditoria.
- Critérios prováveis de acesso: certificação de conformidade técnica, adesão formal à RNDS e possivelmente certificado digital institucional, a validar no Portal de Serviços DATASUS.
- Pendências de confirmação: requisitos técnicos de certificação, padrão FHIR ou correlato, e processo de habilitação institucional, a validar no Portal de Serviços DATASUS.

### 4.8 REL

- Finalidade provável: a validar no Portal de Serviços DATASUS, pois a sigla não está confirmada com precisão suficiente neste documento para descrição de finalidade específica.
- Módulo do GSI ONE impactado: Relatórios e Indicadores, hipótese sujeita a confirmação.
- Fase recomendada de integração: Fase 6, condicionada à confirmação da finalidade real do sistema.
- Tipo de dado envolvido: a validar no Portal de Serviços DATASUS.
- Sensibilidade/LGPD: a validar no Portal de Serviços DATASUS.
- Critérios prováveis de acesso: a validar no Portal de Serviços DATASUS.
- Pendências de confirmação: identificação exata do sistema correspondente à sigla, a validar no Portal de Serviços DATASUS.

### 4.9 e-SUS Notifica/Sinan

- Finalidade provável: notificação compulsória de agravos e doenças, apoiando vigilância epidemiológica.
- Módulo do GSI ONE impactado: Triagem, Consulta, Observatório e Indicadores.
- Fase recomendada de integração: Fase 6.
- Tipo de dado envolvido: dado clínico sensível associado a notificação compulsória, podendo incluir identificação do paciente conforme protocolo de vigilância.
- Sensibilidade/LGPD: alta, por envolver dado de saúde com finalidade de interesse público em vigilância epidemiológica e exigir base legal específica.
- Critérios prováveis de acesso: cadastro de unidade notificante e fluxo de vigilância municipal ou estadual, a validar no Portal de Serviços DATASUS.
- Pendências de confirmação: modelo de integração, formulário web, API ou arquivo de lote, a validar no Portal de Serviços DATASUS.

### 4.10 RIA/Vacinação

- Finalidade provável: registro e consulta de histórico vacinal do paciente, Registro Informatizado de Vacinação ou correlato.
- Módulo do GSI ONE impactado: Consulta, Cadastro de Pacientes e Indicadores.
- Fase recomendada de integração: Fase 6.
- Tipo de dado envolvido: dado de saúde individualizado, histórico de imunização.
- Sensibilidade/LGPD: alta, por envolver dado de saúde vinculado a paciente identificado.
- Critérios prováveis de acesso: cadastro de sala de vacina ou unidade no sistema correspondente, a validar no Portal de Serviços DATASUS.
- Pendências de confirmação: identificação exata do sistema vigente e seu modelo de integração, a validar no Portal de Serviços DATASUS.

## 5. Critérios gerais de acesso

Os critérios de acesso devem ser confirmados nas fontes oficiais antes de qualquer solicitação ou desenvolvimento.

Critérios gerais a validar:

- cadastro institucional do hospital, município ou secretaria;
- vínculo do estabelecimento no CNES, quando exigido;
- responsável institucional formalmente designado;
- responsável técnico identificado;
- certificado digital institucional, quando exigido;
- ambiente de homologação segregado;
- autorização formal para solicitação de acesso;
- política de segurança, logs e auditoria;
- aderência à LGPD e ao sigilo assistencial.

Nenhuma API deve ser considerada homologada, aprovada ou em produção sem confirmação oficial documentada.

## 6. Arquitetura segura recomendada

As diretrizes abaixo devem orientar qualquer implementação futura, quando autorizada:

- o front-end do GSI ONE não deve chamar APIs governamentais diretamente do navegador;
- deve existir backend intermediário seguro, responsável por toda comunicação com sistemas governamentais;
- credenciais de acesso devem permanecer fora do navegador, armazenadas apenas no backend ou em cofre de segredos apropriado;
- tokens, chaves, certificados, senhas e credenciais não devem ser versionados em repositório de código;
- todo acesso a dados governamentais deve ser auditado, com registro de usuário, data/hora, finalidade da consulta e resultado;
- logs devem preservar rastreabilidade sem expor dado sensível além do estritamente necessário;
- homologação deve preceder produção em todos os casos;
- produção só deve ocorrer após autorização institucional formal;
- a integração deve respeitar LGPD, sigilo assistencial e controle de acesso por perfil de usuário.

## 7. Segurança, LGPD e auditoria

Toda integração futura deve considerar:

- finalidade específica e documentada;
- base legal aplicável, a validar institucionalmente;
- minimização de dados;
- controle de acesso por perfil;
- segregação entre homologação e produção;
- trilha de auditoria preservada;
- logs sem exposição indevida de dados sensíveis;
- política de retenção de logs;
- resposta a incidentes;
- revisão pelo responsável LGPD/DPO ou equivalente, quando aplicável.

## 8. Roadmap por fases

- Fase 0: documentação, levantamento de requisitos, autorização institucional e avaliação de impacto à proteção de dados.
- Fase 1: tabelas de referência pública ou baixa sensibilidade, como CNES e SIGTAP, se disponíveis em formato de integração confirmado.
- Fase 2: validações cadastrais, como CNS/CADSUS, apenas após autorização institucional formal.
- Fase 3: regulação e transferência, como SISREG/e-SUS Regulação, após pactuação com gestão regional ou estadual.
- Fase 4: farmácia e assistência farmacêutica, como SI-BNAFAR, após validação de requisitos junto à gestão municipal.
- Fase 5: RNDS/SUS Digital e demais dados clínicos sensíveis, somente com maturidade comprovada de segurança da informação.
- Fase 6: notificações compulsórias, vacinação e observatórios, como e-SUS Notifica/Sinan, RIA/Vacinação, OBM e REL, conforme autorização e finalidade específica.

## 9. Módulos impactados do GSI ONE

| Módulo | APIs/sistemas relacionados |
|---|---|
| Cadastro de Pacientes | CNS/CADSUS, CNES |
| Atendimento/Recepção | SISREG/e-SUS Regulação |
| Triagem | e-SUS Notifica/Sinan |
| Consulta | SIGTAP, RNDS/SUS Digital, RIA/Vacinação |
| Exames | SIGTAP, RNDS/SUS Digital |
| Farmácia | SI-BNAFAR, SIGTAP |
| Transferências/Regulação | SISREG/e-SUS Regulação |
| Indicadores | CNES, SIGTAP, OBM, REL, a validar no Portal de Serviços DATASUS |
| Auditoria | RNDS/SUS Digital, SI-BNAFAR |
| Observatório | OBM, e-SUS Notifica/Sinan |
| Relatórios | SIGTAP, REL, a validar no Portal de Serviços DATASUS |

## 10. Riscos e cuidados

- Tratamento de dados sensíveis de saúde sem base legal ou finalidade adequada.
- Uso indevido, vazamento ou exposição de credenciais de acesso a sistemas governamentais.
- Exposição de dados sensíveis diretamente no navegador, caso a arquitetura recomendada não seja respeitada.
- Dependência de disponibilidade e estabilidade de sistemas externos fora do controle do GSI ONE.
- Inconsistência entre dados mantidos localmente e dados oficiais governamentais.
- Mudança de regras de acesso, autenticação ou disponibilidade por parte dos sistemas governamentais sem aviso prévio.
- Integração realizada sem processo de homologação formal.
- Auditoria insuficiente sobre o uso de dados obtidos de sistemas governamentais.
- Responsabilidade institucional e legal do hospital ou município pelo uso inadequado de dados integrados.

## 11. Pendências

| Item | Pendência | Status |
|---|---|---|
| 1 | Validar documentação oficial atualizada de cada API ou sistema no Portal de Serviços DATASUS | Pendente |
| 2 | Confirmar endpoints, protocolos, autenticação, certificados e requisitos de homologação | Pendente |
| 3 | Confirmar responsável institucional por solicitações de acesso | Pendente |
| 4 | Confirmar responsável técnico pela futura camada de integração | Pendente |
| 5 | Confirmar exigências de LGPD, auditoria e segurança da informação | Pendente |
| 6 | Confirmar se cada sistema possui API formal, webservice, arquivo de lote ou apenas interface web | Pendente |
| 7 | Confirmar ambiente de homologação e critérios para produção | Pendente |

## 12. Próximas ações

- Levantar documentação oficial e atualizada no Portal de Serviços DATASUS para cada API ou sistema listado.
- Identificar o responsável institucional pela solicitação formal de acesso a cada sistema.
- Verificar se município, secretaria de saúde ou hospital já possui autorização, convênio ou cadastro prévio junto ao DATASUS ou Ministério da Saúde.
- Mapear o encarregado de proteção de dados ou responsável equivalente para avaliação de impacto à proteção de dados antes de qualquer integração.
- Definir ambiente de homologação segregado do ambiente de produção.
- Definir arquitetura do backend intermediário seguro responsável pela comunicação com sistemas governamentais.
- Definir política de logs e auditoria para acessos a dados governamentais.
- Definir matriz de permissões por perfil de usuário para consulta e uso desses dados.
- Priorizar APIs de menor risco e menor sensibilidade antes de avançar para APIs clínicas sensíveis.

## 13. Histórico de revisão

| Versão | Data | Responsável | Alteração | Status |
|---|---|---|---|---|
| 0.1 | 2026 | GSI HealthTech | Padronização documental inicial conforme GSI-DOCUMENTATION-STANDARD.md e GHAES-0009-DOCUMENTATION-STANDARD.md | Draft |

## 14. Alinhamento ao padrão oficial de documentação

Este documento segue a estrutura documental mínima definida para documentação técnica do GSI ONE, com identificação documental, objetivo, escopo, contexto, riscos, pendências, próximas ações e histórico de revisão.

Documento de caráter exploratório. Não constitui autorização para implementação técnica. Pendências marcadas como `A validar no Portal de Serviços DATASUS` devem ser resolvidas junto às fontes oficiais antes de qualquer decisão de arquitetura ou desenvolvimento.
