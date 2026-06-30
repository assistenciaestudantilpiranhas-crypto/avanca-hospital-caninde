# CNS-CADSUS-INTEGRATION-DESIGN.md

## Cabeçalho documental

| Campo | Valor |
|---|---|
| Código documental | API-003 |
| Projeto | GSI ONE / Avança Hospital |
| Documento | Desenho técnico da integração CNS/CADSUS |
| Versão | 0.1 |
| Status | Draft |
| Data | 2026 |
| Responsável | GSI HealthTech |
| Padrão documental | GSI-DOCUMENTATION-STANDARD.md; GHAES-0009-DOCUMENTATION-STANDARD.md |

## 1. Objetivo

Este documento descreve a arquitetura futura prevista para consulta cadastral CNS/CADSUS no GSI ONE, com foco em apoio à identificação segura do paciente.

O documento tem caráter técnico, institucional e exploratório. Ele não implementa a integração, não cria endpoints, não define payload final e não autoriza uso em produção.

## 2. Escopo

O escopo deste desenho técnico inclui a consulta cadastral CNS/CADSUS para apoiar:

- identificação segura do paciente na recepção;
- conferência de dados no cadastro de pacientes;
- apoio à qualificação de informações no prontuário;
- redução de duplicidade cadastral;
- rastreabilidade assistencial vinculada ao atendimento.

Este documento descreve componentes, fluxo lógico, dados previstos, requisitos de segurança, auditoria, ambientes, tratamento de erros e pendências para validação oficial.

## 3. Não escopo

Este documento não:

- cria integração real;
- altera cadastro no CADSUS;
- cria novo cadastro CNS;
- cria backend;
- cria endpoint;
- cria chamadas HTTP reais;
- autoriza uso em produção;
- define credenciais, certificados, tokens, senhas ou chaves;
- inclui CPF real, CNS real ou dados sensíveis;
- altera código, banco de dados, migrations, RLS, autenticação, usuários ou permissões.

## 4. Contexto institucional

O GSI ONE é a plataforma digital de saúde do ecossistema GSI HealthTech, aplicada no programa Avança Hospital. No contexto do Avança Hospital, a identificação segura do paciente é relevante para recepção, cadastro de pacientes, prontuário, atendimento e rastreabilidade assistencial.

A futura integração CNS/CADSUS poderá apoiar o operador na conferência de dados cadastrais do usuário SUS, reduzindo risco de duplicidade e inconsistência. Essa consulta não deve substituir a conferência humana, nem alterar automaticamente dados sem validação operacional definida.

## 5. Base documental

Este desenho técnico considera como base documental:

- `GOV-BR-API-ROADMAP.md`;
- `GOV-BR-API-ACCESS-CHECKLIST.md`;
- Manual de Integração PDQ CNS;
- Manual de Solicitação de Credenciais CNS.

Os detalhes técnicos finais, incluindo endpoints, payloads, requisitos de certificado, regras de autenticação e critérios de produção, devem ser tratados como `A validar no Portal de Serviços DATASUS`.

## 6. Finalidade da integração CNS/CADSUS

A integração futura CNS/CADSUS tem como finalidade prevista:

- consultar dados cadastrais do usuário SUS;
- apoiar conferência pelo operador;
- reduzir duplicidade de cadastro;
- melhorar segurança da identificação do paciente;
- apoiar rastreabilidade assistencial.

A consulta deve ocorrer apenas quando houver finalidade assistencial, administrativa ou operacional justificável no contexto do atendimento.

## 7. Limites da integração

A integração CNS/CADSUS não deve:

- alterar cadastro do cidadão via API;
- criar novo cadastro CNS;
- substituir conferência humana;
- expor dados no front-end além do mínimo necessário;
- armazenar credenciais no navegador;
- armazenar token no navegador;
- armazenar certificado no repositório;
- registrar segredo, senha, token ou certificado em logs;
- ser usada sem vínculo assistencial ou justificativa operacional.

## 8. Arquitetura recomendada

O fluxo recomendado para integração futura é:

```text
GSI ONE front-end
↓
Backend seguro da GSI ONE
↓
Módulo de autenticação governamental
↓
Certificado digital ICP-Brasil
↓
EHR-Auth / token temporário
↓
Consulta PDQ/CADSUS
↓
Tratamento da resposta
↓
Conferência pelo operador
↓
Registro de auditoria interna
```

O front-end deve apenas solicitar a consulta ao backend seguro da GSI ONE. Toda comunicação com serviços governamentais deve ocorrer no backend ou em camada intermediária autorizada, com custódia segura de credenciais e registro de auditoria.

## 9. Componentes previstos

Os componentes previstos para uma implementação futura são:

- front-end GSI ONE;
- backend intermediário;
- serviço de autenticação;
- cache seguro de token temporário;
- serviço de consulta CNS/CADSUS;
- módulo de auditoria;
- camada de tratamento de erros;
- controle de acesso por perfil.

Esses componentes são conceituais neste documento e não representam implementação existente.

## 10. Dados de entrada previstos

Com base nos manuais analisados, os dados de entrada previstos podem incluir:

- CNS;
- CPF;
- nome;
- nome da mãe;
- NIS;
- dados demográficos quando CPF ou CNS não estiverem disponíveis.

Campos obrigatórios, combinações permitidas, regras de busca, validações, payload final e parâmetros técnicos devem ser tratados como `A validar no Portal de Serviços DATASUS`.

Nenhum CPF real, CNS real, NIS real ou dado sensível deve ser registrado neste repositório.

## 11. Dados de saída previstos

Os dados retornados pela consulta CNS/CADSUS devem ser tratados como dados pessoais sensíveis ou protegidos, conforme natureza e contexto de uso.

A estrutura exata da resposta, campos retornados, códigos de status, mensagens de erro e metadados técnicos devem ser validados na documentação técnica oficial vigente e tratados como `A validar no Portal de Serviços DATASUS`.

O front-end deve exibir apenas o retorno mínimo necessário para conferência pelo operador, evitando exposição excessiva de dados.

## 12. Segurança e LGPD

A integração futura deve observar:

- finalidade da consulta;
- minimização de dados;
- controle por perfil;
- registro do usuário solicitante;
- data e hora da consulta;
- finalidade operacional;
- não exposição de token;
- não armazenamento de certificado no repositório;
- não consulta sem vínculo assistencial justificável;
- proteção de dados em trânsito e em repouso;
- separação entre homologação e produção;
- política de retenção de logs.

Credenciais, tokens, certificados, senhas e chaves devem permanecer fora do front-end, fora do Git e sob custódia segura.

## 13. Auditoria

A implementação futura deve prever log interno com:

- usuário do sistema;
- perfil;
- paciente pesquisado;
- parâmetro usado;
- data e hora;
- resultado geral da consulta;
- motivo ou finalidade;
- erro, se houver.

O log não deve registrar:

- token;
- certificado;
- senha;
- segredo;
- chave privada;
- resposta completa quando contiver dado sensível além do necessário para auditoria.

## 14. Ambientes

### Homologação

O ambiente de homologação deve ser usado para validação técnica, evidências, testes de autenticação, testes de consulta e avaliação de tratamento de erros.

Dados reais de pacientes não devem ser utilizados em homologação sem autorização institucional expressa, finalidade definida e controles adequados.

### Produção

O uso em produção depende de:

- aprovação formal;
- evidências de testes;
- credencial válida;
- certificado válido, quando exigido;
- controle de acesso por perfil;
- auditoria ativa;
- backend intermediário seguro;
- validação dos requisitos oficiais vigentes.

Nenhuma API deve ser considerada homologada ou em produção apenas por constar neste documento.

## 15. Tratamento de erros

A implementação futura deve prever tratamento para:

- paciente não encontrado;
- múltiplos resultados;
- token expirado;
- certificado inválido;
- acesso negado;
- indisponibilidade do serviço;
- resposta incompleta;
- falha de auditoria.

Erros devem ser apresentados ao operador de forma objetiva, sem expor detalhes sensíveis, segredos técnicos ou dados além do necessário.

## 16. Regras para o front-end

O front-end do GSI ONE deve:

- não chamar DATASUS diretamente;
- não armazenar token;
- não receber certificado;
- apenas solicitar consulta ao backend;
- exibir retorno mínimo necessário;
- exigir conferência do operador;
- não persistir dados retornados sem regra aprovada;
- não expor detalhes técnicos de autenticação.

## 17. Regras para backend futuro

O backend futuro deve:

- custodiar credenciais com segurança;
- gerar e reutilizar token durante validade;
- registrar auditoria;
- aplicar controle de acesso;
- tratar erros;
- proteger dados em trânsito e em repouso;
- permitir configuração por ambiente;
- impedir uso sem finalidade operacional justificável;
- impedir vazamento de certificado, senha, token ou segredo em logs.

## 18. Riscos

Os principais riscos previstos são:

- uso indevido de dados pessoais;
- consulta sem finalidade;
- exposição de credenciais;
- falha de auditoria;
- dependência de serviço externo;
- dados divergentes;
- bloqueio por uso atípico;
- retorno de múltiplos registros e seleção inadequada;
- uso em produção sem homologação formal.

## 19. Pendências

As pendências abaixo devem ser tratadas como `A validar no Portal de Serviços DATASUS`:

- endpoints atuais;
- payload final;
- formato de resposta;
- requisitos de certificado;
- evidências exigidas;
- limites de consumo;
- requisitos de produção;
- requisitos de IP público;
- dados obrigatórios por tipo de consulta.

Também permanecem pendentes validações institucionais sobre perfis autorizados, política de auditoria, retenção de logs e fluxo operacional de conferência.

## 20. Próximas ações

As próximas ações recomendadas são:

- validar documentação oficial atual no Portal de Serviços DATASUS;
- confirmar CNES/CNPJ e gestor responsável;
- confirmar certificado digital;
- definir backend;
- definir política de auditoria;
- definir perfis autorizados;
- criar plano de homologação;
- criar checklist de evidências.

## 21. Histórico de revisão

| Versão | Data | Responsável | Alteração | Status |
|---|---|---|---|---|
| 0.1 | 2026 | GSI HealthTech | Draft inicial do desenho técnico CNS/CADSUS | Draft |
