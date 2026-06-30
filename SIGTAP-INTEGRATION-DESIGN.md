# SIGTAP-INTEGRATION-DESIGN.md

## Cabeçalho documental

| Campo | Valor |
|---|---|
| Código documental | API-005 |
| Projeto | GSI ONE / Avança Hospital |
| Documento | Desenho técnico da integração SIGTAP |
| Versão | 0.1 |
| Status | Draft |
| Data | 2026 |
| Responsável | GSI HealthTech |
| Padrão documental | GSI-DOCUMENTATION-STANDARD.md; GHAES-0009-DOCUMENTATION-STANDARD.md |

## 1. Objetivo

Este documento descreve a arquitetura futura prevista para consulta e validação de procedimentos SUS via SIGTAP no GSI ONE, com foco em uso seguro da tabela de procedimentos no contexto assistencial, administrativo, auditorial e gerencial.

O documento tem caráter técnico, institucional e exploratório. Ele não implementa integração, não cria endpoints, não define payload final, não cria faturamento real e não autoriza uso em produção.

## 2. Escopo

O escopo deste desenho técnico inclui o uso futuro do SIGTAP para:

- consulta de procedimentos SUS;
- apoio a faturamento SUS futuro;
- apoio a BPA/AIH futuro;
- auditoria hospitalar;
- exames;
- consultas;
- produção hospitalar;
- relatórios;
- indicadores;
- governança.

Este documento descreve componentes, fluxo lógico, dados previstos, requisitos de segurança, auditoria, ambientes, tratamento de erros, uso previsto no GSI ONE e pendências para validação oficial.

## 3. Não escopo

Este documento não:

- cria integração real;
- altera tabela SIGTAP;
- cria backend;
- cria endpoint;
- cria chamadas HTTP reais;
- cria faturamento real;
- autoriza uso em produção;
- define credenciais, certificados, tokens, senhas ou chaves;
- inclui CPF, CNS, CNPJ real ou dados sensíveis;
- altera código, banco de dados, migrations, RLS, autenticação, usuários ou permissões.

## 4. Contexto institucional

O GSI ONE é a plataforma digital de saúde do ecossistema GSI HealthTech, aplicada no programa Avança Hospital. No contexto do Avança Hospital e do Hospital Municipal, a padronização de procedimentos SUS é relevante para faturamento SUS, auditoria hospitalar, produção ambulatorial e hospitalar, relatórios e sustentabilidade financeira.

A futura integração SIGTAP poderá apoiar a conferência técnica de códigos de procedimentos, a organização de catálogos internos e a melhoria da consistência de registros assistenciais e administrativos. Essa consulta não deve substituir regra oficial de faturamento, auditoria humana ou validação institucional.

## 5. Base documental

Este desenho técnico considera como base documental:

- `GOV-BR-API-ROADMAP.md`;
- `GOV-BR-API-ACCESS-CHECKLIST.md`;
- `GSI-DOCUMENTATION-STANDARD.md`;
- `GHAES-0009-DOCUMENTATION-STANDARD.md`;
- documentação oficial SIGTAP/DATASUS, quando validada futuramente.

Os detalhes técnicos finais, incluindo API oficial disponível, endpoints, autenticação, payloads, formato de resposta, forma de atualização por competência e critérios de uso em faturamento, devem ser tratados como `A validar no Portal de Serviços DATASUS`.

## 6. Finalidade da integração SIGTAP

A integração futura SIGTAP tem como finalidade prevista:

- consultar procedimentos SUS;
- validar códigos de procedimentos;
- apoiar padronização de exames, consultas, atendimentos e procedimentos;
- apoiar faturamento SUS futuro;
- apoiar BPA/AIH futuro;
- apoiar auditoria hospitalar;
- reduzir risco de subnotificação ou registro inadequado;
- apoiar relatórios gerenciais.

O uso desses dados deve ocorrer apenas quando houver finalidade institucional, técnica, assistencial, administrativa ou auditorial justificável.

## 7. Limites da integração

A integração SIGTAP não deve:

- alterar tabela SIGTAP;
- substituir regra oficial de faturamento;
- substituir auditoria humana;
- autorizar cobrança ou faturamento automaticamente;
- expor credenciais no front-end;
- considerar integração ativa sem homologação ou autorização formal;
- afirmar compatibilidade com BPA/AIH sem validação técnica posterior;
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
Consulta SIGTAP
↓
Tratamento da resposta
↓
Validação técnica do procedimento
↓
Uso em atendimento, exames, relatórios, auditoria e faturamento futuro
↓
Registro de auditoria interna
```

O front-end deve apenas solicitar a consulta ao backend seguro da GSI ONE. Toda comunicação com serviços governamentais deve ocorrer no backend ou em camada intermediária autorizada, com controle de acesso, tratamento de erros e auditoria.

## 9. Componentes previstos

Os componentes previstos para uma implementação futura são:

- front-end GSI ONE;
- backend intermediário;
- serviço de consulta SIGTAP;
- módulo de catálogo local/cache controlado, se aprovado futuramente;
- módulo de auditoria;
- camada de tratamento de erros;
- controle de acesso por perfil;
- integração futura com relatórios, exames, atendimentos e faturamento.

Esses componentes são conceituais neste documento e não representam implementação existente.

## 10. Dados de entrada previstos

Os dados de entrada previstos devem ser tratados como `A validar no Portal de Serviços DATASUS` e podem incluir:

- código do procedimento;
- nome ou descrição do procedimento;
- grupo, subgrupo ou forma de organização, se disponível;
- competência ou vigência, se aplicável;
- tipo de financiamento, se disponível;
- outros parâmetros permitidos pela API oficial.

Campos obrigatórios, combinações permitidas, regras de busca, validações, payload final e parâmetros técnicos devem ser validados na documentação oficial vigente.

Nenhum CPF, CNS, CNPJ real ou dado sensível deve ser registrado neste repositório.

## 11. Dados de saída previstos

Os dados de saída previstos devem ser tratados como `A validar no Portal de Serviços DATASUS` e podem incluir:

- código do procedimento;
- descrição;
- grupo;
- subgrupo;
- forma de organização;
- competência/vigência;
- valor, se disponível e autorizado;
- complexidade, se disponível;
- modalidade ou instrumento de registro, se disponível;
- compatibilidades e restrições, se disponíveis;
- situação ativa/inativa, se disponível.

A estrutura exata da resposta, campos retornados, códigos de status, mensagens de erro e metadados técnicos devem ser validados na documentação técnica oficial vigente.

## 12. Segurança e LGPD

Em regra, a consulta SIGTAP envolve dados de procedimentos e não dados pessoais de pacientes. Porém, seu uso dentro do GSI ONE pode se vincular a atendimentos, exames, produção assistencial, auditoria e faturamento futuro.

Por esse motivo, a integração futura deve observar:

- controle de acesso por perfil;
- registro do usuário solicitante;
- data e hora da consulta ou validação;
- finalidade operacional;
- não exposição de token;
- não armazenamento de credenciais no repositório;
- uso apenas para apoio técnico, auditoria, relatórios e faturamento autorizado;
- proteção de dados em trânsito e em repouso;
- separação entre homologação e produção, se aplicável.

Credenciais, tokens, certificados, senhas e chaves devem permanecer fora do front-end, fora do Git e sob custódia segura.

## 13. Auditoria

A implementação futura deve prever log interno com:

- usuário do sistema;
- perfil;
- código ou termo pesquisado;
- data e hora;
- resultado geral da consulta;
- módulo de origem;
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

- documentação oficial vigente;
- credenciais válidas, quando exigidas;
- testes aceitos;
- autorização formal, quando exigida;
- controle de acesso por perfil;
- auditoria ativa;
- backend intermediário seguro;
- validação dos requisitos oficiais vigentes.

Nenhuma API deve ser considerada homologada ou em produção apenas por constar neste documento.

## 15. Tratamento de erros

A implementação futura deve prever tratamento para:

- procedimento não encontrado;
- múltiplos resultados;
- procedimento inativo ou fora de vigência;
- serviço indisponível;
- acesso negado;
- parâmetro inválido;
- resposta incompleta;
- divergência entre catálogo local e fonte oficial;
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
- não permitir faturamento automático sem validação;
- não transformar procedimento consultado em produção faturável sem regra aprovada;
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
- controlar atualização de cache local, se houver aprovação futura;
- impedir vazamento de certificado, senha, token ou segredo em logs.

## 18. Uso previsto no GSI ONE

O uso futuro de dados SIGTAP no GSI ONE pode apoiar:

- Atendimentos;
- Consulta médica;
- Exames;
- Relatórios;
- Indicadores;
- Faturamento SUS futuro;
- Auditoria;
- Produção hospitalar;
- Sustentabilidade financeira;
- Integrações governamentais.

O uso efetivo depende de validação técnica, institucional e documental.

## 19. Riscos

Os principais riscos previstos são:

- uso de procedimento desatualizado;
- divergência entre catálogo local e SIGTAP;
- interpretação incorreta de código;
- faturamento indevido;
- subnotificação por código inadequado;
- exposição indevida de credenciais;
- falha de auditoria;
- dependência de serviço externo;
- bloqueio por uso atípico;
- uso de dado fora da competência vigente.

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
- forma correta de atualização por competência;
- possibilidade de cache local;
- critérios oficiais para uso em faturamento.

Também permanecem pendentes validações institucionais sobre perfis autorizados, política de auditoria, retenção de logs, estratégia de cache, uso em relatórios e uso em faturamento futuro.

## 21. Próximas ações

As próximas ações recomendadas são:

- validar documentação oficial atual no Portal de Serviços DATASUS;
- confirmar forma oficial de consumo do SIGTAP;
- definir backend intermediário;
- definir política de auditoria;
- definir perfis autorizados;
- definir estratégia de cache ou consulta sob demanda;
- criar plano de homologação;
- criar checklist de evidências;
- alinhar com `GOV-BR-API-ROADMAP.md` e `GOV-BR-API-ACCESS-CHECKLIST.md`.

## 22. Histórico de revisão

| Versão | Data | Responsável | Alteração | Status |
|---|---|---|---|---|
| 0.1 | 2026 | GSI HealthTech | Draft inicial do desenho técnico SIGTAP | Draft |
