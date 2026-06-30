# GOV-BR-API-ACCESS-CHECKLIST.md

## Cabeçalho documental

| Campo | Valor |
|---|---|
| Código documental | API-002 |
| Projeto | GSI ONE / Avança Hospital |
| Documento | Checklist de acesso a APIs governamentais |
| Versão | 0.1 |
| Status | Draft |
| Data | 2026 |
| Responsável | GSI HealthTech |
| Padrão documental | GSI-DOCUMENTATION-STANDARD.md; GHAES-0009-DOCUMENTATION-STANDARD.md |

## 1. Objetivo

Este documento organiza as informações institucionais, técnicas, operacionais e de segurança necessárias antes de solicitar acesso a APIs governamentais, iniciando pelo CNS/CADSUS, em complemento ao roadmap `GOV-BR-API-ROADMAP.md`.

Este checklist:

- não autoriza integração imediata;
- não substitui manuais oficiais do DATASUS ou gov.br;
- exige confirmação de requisitos específicos no Portal de Serviços DATASUS;
- não deve conter credenciais, certificados, tokens, senhas, chaves ou dados sensíveis;
- reforça que o front-end do GSI ONE não deve chamar APIs governamentais diretamente;
- exige backend intermediário seguro para qualquer integração futura.

Onde não houver confirmação documental oficial, o conteúdo deve ser tratado como `A validar no Portal de Serviços DATASUS`.

## 2. Escopo

Estão no escopo deste checklist:

- dados institucionais necessários para solicitação de acesso;
- identificação de responsável institucional e técnico;
- requisitos de certificado digital, quando aplicável;
- dados do sistema solicitante;
- finalidade prevista da integração;
- homologação;
- produção;
- segurança, LGPD e auditoria;
- pendências de validação oficial.

Ficam fora do escopo:

- criação de integração real;
- chamada a APIs governamentais;
- criação ou armazenamento de credenciais;
- inclusão de tokens, certificados, senhas ou chaves;
- alteração de APIs, endpoints ou requisitos técnicos oficiais;
- alteração de banco de dados, migrations, RLS, autenticação, usuários ou permissões;
- afirmação de que qualquer API esteja homologada ou em produção.

## 3. Checklist institucional

### 3.1 Identificação institucional

| Campo | Valor | Status | Observação |
|---|---|---|---|
| Nome do estabelecimento | | Pendente | |
| CNES | | Pendente | |
| CNPJ | | Pendente | |
| Município/UF | | Pendente | |
| Telefone institucional | | Pendente | |
| E-mail institucional | | Pendente | |
| Secretaria ou órgão responsável | | Pendente | |
| Natureza jurídica, se exigida | | Pendente | A validar no Portal de Serviços DATASUS |
| Situação do estabelecimento no CNES | | Pendente | A validar no Portal de Serviços DATASUS |
| Observações | | Não aplicável | |
| Responsável pela informação | | Pendente | |

### 3.2 Responsável institucional ou gestor

| Campo | Valor | Status | Pendência |
|---|---|---|---|
| Nome completo | | Pendente | |
| CPF ou CNS | | Pendente | |
| Cargo/função | | Pendente | |
| E-mail institucional | | Pendente | |
| Telefone | | Pendente | |
| Órgão/setor | | Pendente | |
| Confirmação de vínculo no CNES | | Pendente | A validar no Portal de Serviços DATASUS |
| Documento de designação, se exigido | | Pendente | A validar no Portal de Serviços DATASUS |
| Responsável pela solicitação | | Pendente | |

A exigência de vínculo formal, documento de designação ou perfil específico de gestor deve ser validada no Portal de Serviços DATASUS.

## 4. Checklist técnico

### 4.1 Sistema solicitante

| Campo | Valor |
|---|---|
| Nome do sistema | GSI ONE |
| Ecossistema | GSI HealthTech |
| Programa/case | Avança Hospital |
| Versão do sistema | A validar internamente |
| Linguagem predominante | HTML, CSS, JavaScript, front-end estático; Supabase, banco/backend |
| Arquitetura | A validar e documentar antes da solicitação |
| Banco de dados | Supabase, PostgreSQL |
| Versão do banco | A validar no ambiente Supabase |
| URL da aplicação/ambiente | A validar, produção, homologação ou local |
| Ambiente | Pendente de definição |
| Faixa de IP público, se exigida | A validar no Portal de Serviços DATASUS |
| Responsável técnico | Pendente |
| E-mail técnico | Pendente |
| Telefone técnico | Pendente |
| Repositório privado/público, se aplicável | Pendente de confirmação institucional |
| Observações | Não aplicável |

### 4.2 Orientação técnica obrigatória

- O front-end do GSI ONE não deve consumir diretamente APIs governamentais.
- Deve existir backend intermediário seguro ou serviço de integração responsável por toda comunicação externa.
- Credenciais, tokens, certificados, senhas e chaves devem ficar fora do front-end e fora do Git.
- A camada intermediária deve implementar autenticação, autorização, auditoria, logs e controle de finalidade.
- Nenhuma API deve ser considerada homologada ou em produção sem confirmação oficial documentada.

### 4.3 Uso previsto da integração

| Campo | Valor |
|---|---|
| API/sistema solicitado | |
| Finalidade da integração | |
| Módulo do GSI ONE impactado | |
| Tipo de operação, consulta, validação, envio ou recebimento | |
| Tipo de dado envolvido | |
| Base legal/finalidade assistencial ou administrativa | |
| Quantidade mínima de atendimentos/dia | |
| Quantidade máxima de atendimentos/dia | |
| Quantidade estimada de acessos no pico | |
| Períodos de maior acesso | |
| Data estimada de início | |
| Data estimada de fim, se aplicável | |
| Responsável pela justificativa | |
| Status | Pendente |

### 4.4 CNS/CADSUS

Finalidade provável:

- validação cadastral do paciente;
- qualificação do cadastro do usuário no Cadastro de Pacientes do GSI ONE;
- apoio à identificação do usuário SUS.

Detalhes operacionais, volume de consultas, limites de requisição, SLA e formato de resposta devem ser validados no Portal de Serviços DATASUS.

## 5. Checklist de certificado digital

| Campo | Valor | Status |
|---|---|---|
| Tipo de certificado, `.cer` ou A1 `.pfx` | | A validar no Portal de Serviços DATASUS |
| Titular do certificado | | Pendente |
| CPF/CNPJ do titular | | Pendente |
| Validade | | Pendente |
| Estabelecimento vinculado | | Pendente |
| Responsável pela custódia | | Pendente |
| Local seguro de armazenamento | | Pendente |
| Data de emissão | | Pendente |
| Data de vencimento | | Pendente |
| Ambiente de uso, homologação ou produção | | Pendente |
| Status | | Pendente |

Observações obrigatórias:

- não armazenar chave privada no repositório;
- não versionar arquivo `.pfx`;
- não expor senha de certificado;
- não colocar certificado no front-end;
- manter certificados e senhas em ambiente seguro, fora do Git, como cofre de segredos ou equivalente;
- validar requisitos específicos do tipo de certificado exigido no Portal de Serviços DATASUS.

## 6. Checklist de homologação

| Item | Status |
|---|---|
| Solicitação de homologação enviada | Pendente |
| Protocolo da solicitação | Pendente |
| Credencial de homologação aprovada | Pendente |
| Ambiente de homologação configurado | Pendente |
| Certificado de homologação validado, se exigido | A validar no Portal de Serviços DATASUS |
| Testes realizados | Pendente |
| Evidência de Request salva | Pendente |
| Evidência de Response salva | Pendente |
| Evidências em PDF ou PNG | Pendente |
| Data dos testes | Pendente |
| Responsável pelos testes | Pendente |
| Resultado dos testes | Pendente |
| Pendências encontradas | Pendente |
| Aprovação para solicitar produção | Pendente |

As evidências de teste não devem conter dados reais de pacientes sem autorização institucional e finalidade definida. Em ambiente de homologação, utilizar exclusivamente dados fictícios, salvo autorização formal em contrário.

## 7. Checklist de produção

| Item | Status |
|---|---|
| Solicitação de produção enviada | Pendente |
| Evidências de homologação anexadas | Pendente |
| Aprovação recebida | Pendente |
| Credencial de produção recebida | Pendente |
| Certificado de produção validado, se exigido | A validar no Portal de Serviços DATASUS |
| Data de início de uso em produção | Pendente |
| Responsável institucional pela produção | Pendente |
| Responsável técnico pela produção | Pendente |
| Plano de contingência | Pendente |
| Plano de revogação de credencial | Pendente |
| Monitoramento ativo | Pendente |
| Status | Pendente |

A produção só deve ser ativada após autorização institucional formal, validação de segurança da informação e confirmação das regras oficiais vigentes no Portal de Serviços DATASUS.

## 8. Checklist de segurança, LGPD e auditoria

- [ ] Credenciais fora do front-end.
- [ ] Certificado fora do repositório.
- [ ] Chave privada fora do Git.
- [ ] Token não exposto no navegador.
- [ ] Senhas em cofre seguro ou variável de ambiente protegida, fora do versionamento.
- [ ] Backend intermediário seguro definido antes de qualquer integração.
- [ ] Backend intermediário obrigatório implementado antes de homologação técnica real.
- [ ] Log interno de consulta implementado.
- [ ] Finalidade da consulta registrada em log.
- [ ] Controle de acesso por perfil de usuário.
- [ ] Auditoria preservada.
- [ ] Princípio de menor privilégio aplicado.
- [ ] Registro de quem consultou.
- [ ] Registro de quando consultou.
- [ ] Registro de qual finalidade da consulta.
- [ ] Política de retenção de logs definida.
- [ ] Revisão pelo responsável LGPD/DPO ou equivalente realizada.
- [ ] Plano de resposta a incidente definido.
- [ ] Proibição de uso de dados reais em ambiente de teste sem autorização formalizada.

## 9. Pendências

| Item | Descrição | Responsável | Prazo | Status | Observação |
|---|---|---|---|---|---|
| 1 | Confirmar requisitos atualizados no Portal de Serviços DATASUS | Pendente | Pendente | Pendente | A validar no Portal de Serviços DATASUS |
| 2 | Confirmar documentação oficial CNS/CADSUS | Pendente | Pendente | Pendente | A validar no Portal de Serviços DATASUS |
| 3 | Confirmar tipo de certificado exigido | Pendente | Pendente | Pendente | A validar no Portal de Serviços DATASUS |
| 4 | Confirmar necessidade de CNES ativo | Pendente | Pendente | Pendente | A validar no Portal de Serviços DATASUS |
| 5 | Confirmar responsável institucional aceito | Pendente | Pendente | Pendente | A validar no Portal de Serviços DATASUS |
| 6 | Confirmar ambiente de homologação | Pendente | Pendente | Pendente | A validar no Portal de Serviços DATASUS |
| 7 | Confirmar critérios para produção | Pendente | Pendente | Pendente | A validar no Portal de Serviços DATASUS |
| 8 | Confirmar política de logs | Pendente | Pendente | Pendente | A validar institucionalmente |
| 9 | Confirmar responsável LGPD/DPO ou equivalente | Pendente | Pendente | Pendente | A validar institucionalmente |
| 10 | Confirmar se há necessidade de ofício institucional | Pendente | Pendente | Pendente | A validar no Portal de Serviços DATASUS |

## 10. Ordem prática recomendada

1. Validar CNES e dados institucionais.
2. Identificar responsável institucional.
3. Identificar responsável técnico.
4. Levantar documentação oficial atualizada.
5. Confirmar exigência de certificado digital.
6. Preparar ambiente de homologação.
7. Definir backend intermediário seguro.
8. Definir logs e auditoria.
9. Solicitar homologação, quando houver autorização institucional.
10. Executar testes em ambiente apropriado.
11. Salvar evidências sem dados sensíveis indevidos.
12. Solicitar produção, quando houver autorização institucional e homologação aprovada.
13. Validar produção com monitoramento.
14. Registrar política de uso e revisão periódica.

## 11. Histórico de revisão

| Versão | Data | Responsável | Alteração | Status |
|---|---|---|---|---|
| 0.1 | 2026 | GSI HealthTech | Padronização documental inicial conforme GSI-DOCUMENTATION-STANDARD.md e GHAES-0009-DOCUMENTATION-STANDARD.md | Draft |

## 12. Alinhamento ao padrão oficial de documentação

Este checklist segue a estrutura documental mínima definida para documentação técnica do GSI ONE, com identificação documental, objetivo, escopo, checklists por domínio, pendências e histórico de revisão.

Este documento é preparatório e deve ser revisado antes de qualquer solicitação formal. A integração com APIs governamentais deve respeitar LGPD, sigilo assistencial, regras oficiais do DATASUS/gov.br, políticas internas da instituição e autorização formal do gestor responsável.
