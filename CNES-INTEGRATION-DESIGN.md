# CNES-INTEGRATION-DESIGN.md

## Cabeçalho documental

| Campo | Valor |
|---|---|
| Código documental | API-004 |
| Projeto | GSI ONE / Avança Hospital |
| Documento | Desenho técnico da integração CNES |
| Versão | 0.1 |
| Status | Draft |
| Data | 2026 |
| Responsável | GSI HealthTech |
| Padrão documental | GSI-DOCUMENTATION-STANDARD.md; GHAES-0009-DOCUMENTATION-STANDARD.md |

## 1. Objetivo

Este documento descreve a arquitetura futura prevista para consulta e validação de dados CNES no GSI ONE, com foco em uso seguro de informações institucionais do estabelecimento de saúde.

O documento tem caráter técnico, institucional e exploratório. Ele não implementa integração, não cria endpoints, não define payload final e não autoriza uso em produção.

## 2. Escopo

O escopo deste desenho técnico inclui o uso futuro de dados CNES para:

- identificação do estabelecimento de saúde;
- validação de dados institucionais;
- validação de unidade de saúde;
- apoio a relatórios técnicos e gerenciais;
- apoio a faturamento SUS futuro;
- apoio a auditoria;
- apoio a integrações governamentais futuras.

Este documento descreve componentes, fluxo lógico, dados previstos, requisitos de segurança, auditoria, ambientes, tratamento de erros, uso previsto no GSI ONE e pendências para validação oficial.

## 3. Não escopo

Este documento não:

- cria integração real;
- altera dados do CNES;
- cria backend;
- cria endpoint;
- cria chamadas HTTP reais;
- autoriza uso em produção;
- define credenciais, certificados, tokens, senhas ou chaves;
- inclui CNPJ real, CPF real ou dados sensíveis;
- altera código, banco de dados, migrations, RLS, autenticação, usuários ou permissões.

## 4. Contexto institucional

O GSI ONE é a plataforma digital de saúde do ecossistema GSI HealthTech, aplicada no programa Avança Hospital. No contexto do Avança Hospital e do Hospital Municipal, dados institucionais do estabelecimento são relevantes para gestão hospitalar, faturamento SUS, auditoria, relatórios, indicadores e governança.

A futura integração CNES poderá apoiar a conferência de informações institucionais da unidade de saúde e reduzir inconsistências entre cadastro local e fonte oficial. Essa consulta não deve substituir validação institucional, nem alterar automaticamente dados do sistema sem confirmação autorizada.

## 5. Base documental

Este desenho técnico considera como base documental:

- `GOV-BR-API-ROADMAP.md`;
- `GOV-BR-API-ACCESS-CHECKLIST.md`;
- `GSI-DOCUMENTATION-STANDARD.md`;
- `GHAES-0009-DOCUMENTATION-STANDARD.md`;
- documentação oficial CNES/DATASUS, quando validada futuramente.

Os detalhes técnicos finais, incluindo API oficial disponível, endpoints, autenticação, payloads, formato de resposta e critérios de produção, devem ser tratados como `A validar no Portal de Serviços DATASUS`.

## 6. Finalidade da integração CNES

A integração futura CNES tem como finalidade prevista:

- consultar dados do estabelecimento de saúde;
- validar CNES da unidade;
- apoiar configuração institucional do sistema;
- apoiar relatórios técnicos e gerenciais;
- apoiar faturamento SUS e auditoria;
- apoiar futuras integrações com CNS/CADSUS, SIGTAP, BNAFAR, SISREG/e-SUS Regulação e RNDS.

O uso desses dados deve ocorrer apenas quando houver finalidade institucional, administrativa, técnica ou operacional justificável.

## 7. Limites da integração

A integração CNES não deve:

- alterar cadastro CNES;
- substituir validação institucional;
- expor dados sensíveis no front-end;
- armazenar credenciais no navegador;
- usar dados CNES sem confirmação da fonte oficial;
- considerar integração ativa sem homologação ou autorização formal;
- registrar segredo, senha, token ou certificado em logs.

## 8. Arquitetura recomendada

O fluxo recomendado para integração futura é:

```text
GSI ONE front-end
↓
Backend seguro da GSI ONE
↓
Módulo de integração governamental
↓
Consulta CNES
↓
Tratamento da resposta
↓
Validação institucional
↓
Uso em configuração, relatórios e auditoria
↓
Registro de auditoria interna
```

O front-end deve apenas solicitar a consulta ao backend seguro da GSI ONE. Toda comunicação com serviços governamentais deve ocorrer no backend ou em camada intermediária autorizada, com controle de acesso, tratamento de erros e auditoria.

## 9. Componentes previstos

Os componentes previstos para uma implementação futura são:

- front-end GSI ONE;
- backend intermediário;
- serviço de consulta CNES;
- módulo de configuração institucional;
- módulo de auditoria;
- camada de tratamento de erros;
- controle de acesso por perfil;
- integração futura com relatórios e faturamento.

Esses componentes são conceituais neste documento e não representam implementação existente.

## 10. Dados de entrada previstos

Os dados de entrada previstos devem ser tratados como `A validar no Portal de Serviços DATASUS` e podem incluir:

- CNES;
- CNPJ;
- município/UF;
- nome do estabelecimento;
- tipo de unidade;
- outros parâmetros permitidos pela API oficial.

Campos obrigatórios, combinações permitidas, regras de busca, validações, payload final e parâmetros técnicos devem ser validados na documentação oficial vigente.

Nenhum CNPJ real, CPF real ou dado sensível deve ser registrado neste repositório.

## 11. Dados de saída previstos

Os dados de saída previstos devem ser tratados como `A validar no Portal de Serviços DATASUS` e podem incluir:

- identificação do estabelecimento;
- CNES;
- CNPJ, quando disponível e autorizado;
- endereço institucional;
- município/UF;
- tipo de estabelecimento;
- natureza jurídica, quando disponível;
- serviços, habilitações e equipes, quando disponíveis pela fonte oficial;
- situação cadastral, quando disponível.

A estrutura exata da resposta, campos retornados, códigos de status, mensagens de erro e metadados técnicos devem ser validados na documentação técnica oficial vigente.

## 12. Segurança e LGPD

A integração futura deve observar:

- finalidade institucional da consulta;
- minimização de dados;
- controle de acesso por perfil;
- registro do usuário solicitante;
- data e hora da consulta;
- finalidade operacional;
- não exposição de token;
- não armazenamento de credenciais no repositório;
- uso apenas para configuração, auditoria, relatórios e integração autorizada;
- proteção de dados em trânsito e em repouso;
- separação entre homologação e produção, se aplicável.

Credenciais, tokens, certificados, senhas e chaves devem permanecer fora do front-end, fora do Git e sob custódia segura.

## 13. Auditoria

A implementação futura deve prever log interno com:

- usuário do sistema;
- perfil;
- CNES ou parâmetro pesquisado;
- data e hora;
- resultado geral da consulta;
- finalidade;
- erro, se houver.

O log não deve registrar:

- token;
- senha;
- certificado;
- segredo;
- chave privada;
- credenciais de acesso.

## 14. Ambientes

### Homologação, se aplicável

O ambiente de homologação, quando exigido, deve ser usado para validação técnica, evidências, testes de consulta, avaliação de tratamento de erros e confirmação de comportamento antes de qualquer uso operacional.

### Produção, se aplicável

O uso em produção depende de:

- aprovação formal;
- documentação oficial vigente;
- credenciais válidas, quando exigidas;
- testes aceitos;
- controle de acesso por perfil;
- auditoria ativa;
- backend intermediário seguro;
- validação dos requisitos oficiais vigentes.

Nenhuma API deve ser considerada homologada ou em produção apenas por constar neste documento.

## 15. Tratamento de erros

A implementação futura deve prever tratamento para:

- CNES não encontrado;
- múltiplos resultados;
- serviço indisponível;
- acesso negado;
- parâmetro inválido;
- resposta incompleta;
- divergência entre cadastro local e fonte oficial;
- falha de auditoria;
- limite de consumo ou bloqueio por uso atípico.

Erros devem ser apresentados ao operador de forma objetiva, sem expor detalhes sensíveis, segredos técnicos ou dados além do necessário.

## 16. Regras para o front-end

O front-end do GSI ONE deve:

- não chamar DATASUS diretamente;
- não armazenar token;
- não receber certificado;
- apenas solicitar consulta ao backend;
- exibir retorno mínimo necessário;
- destacar dados `A validar` quando houver divergência;
- não permitir alteração automática de dados institucionais sem confirmação;
- não expor detalhes técnicos de autenticação.

## 17. Regras para backend futuro

O backend futuro deve:

- custodiar credenciais com segurança;
- aplicar controle de acesso;
- registrar auditoria;
- tratar erros;
- proteger dados em trânsito e em repouso;
- permitir configuração por ambiente;
- isolar integração governamental da interface do usuário;
- evitar consultas desnecessárias ou repetitivas;
- impedir vazamento de certificado, senha, token ou segredo em logs.

## 18. Uso previsto no GSI ONE

O uso futuro de dados CNES no GSI ONE pode apoiar:

- Configurações da unidade;
- Relatórios;
- Indicadores;
- Faturamento SUS futuro;
- Auditoria;
- Integrações governamentais;
- Identidade institucional do estabelecimento.

O uso efetivo depende de validação técnica, institucional e documental.

## 19. Riscos

Os principais riscos previstos são:

- uso de dado institucional desatualizado;
- divergência entre cadastro local e CNES;
- consulta sem finalidade;
- exposição indevida de credenciais;
- falha de auditoria;
- dependência de serviço externo;
- bloqueio por uso atípico;
- interpretação incorreta de serviços ou habilitações;
- uso em produção sem homologação ou autorização formal.

## 20. Pendências

As pendências abaixo devem ser tratadas como `A validar no Portal de Serviços DATASUS`:

- API oficial disponível;
- endpoints atuais;
- autenticação exigida;
- payload final;
- formato de resposta;
- limites de consumo;
- requisitos de homologação;
- requisitos de produção;
- requisitos de IP público;
- campos disponíveis;
- frequência recomendada de atualização.

Também permanecem pendentes validações institucionais sobre perfis autorizados, política de auditoria, retenção de logs, fluxo de validação institucional e uso em relatórios ou faturamento.

## 21. Próximas ações

As próximas ações recomendadas são:

- validar documentação oficial atual no Portal de Serviços DATASUS;
- confirmar CNES/CNPJ do estabelecimento;
- confirmar responsável institucional;
- definir backend intermediário;
- definir política de auditoria;
- definir perfis autorizados;
- criar plano de homologação;
- criar checklist de evidências;
- alinhar com `GOV-BR-API-ROADMAP.md` e `GOV-BR-API-ACCESS-CHECKLIST.md`.

## 22. Histórico de revisão

| Versão | Data | Responsável | Alteração | Status |
|---|---|---|---|---|
| 0.1 | 2026 | GSI HealthTech | Draft inicial do desenho técnico CNES | Draft |
