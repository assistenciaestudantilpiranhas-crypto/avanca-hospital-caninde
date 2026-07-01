# GSI ONE - Protótipo Técnico

Protótipo técnico do GSI ONE, plataforma operacional do ecossistema GSI HealthTech para fluxos assistenciais integrados, login por perfil, governança assistencial, rastreabilidade e auditabilidade.

O ambiente demonstrativo técnico contempla a evolução do projeto para autenticação por perfil, banco de dados Supabase, regras de segurança por RLS, trilha de auditoria, persistência dos fluxos assistenciais e módulos operacionais integrados. Este repositório público não contém informações de acesso, endereços técnicos internos ou dados sensíveis.

## Arquitetura conceitual

- **GSI HealthTech** = ecossistema / marca institucional.
- **GSI ONE** = sistema / plataforma com login, perfis, banco Supabase, RLS, auditabilidade e fluxos assistenciais persistidos.
- **Avança Hospital** = programa / case de implantação.

## Aviso institucional

A demonstração com login e banco de dados é realizada em ambiente controlado, por se tratar de protótipo técnico em desenvolvimento. O ambiente apresenta os módulos operacionais do GSI ONE aplicados ao programa Avança Hospital.

## Módulos incluídos

Cadastro e recepção, Atendimentos, Painel de Chamada, Triagem e classificação de risco, Consulta médica, Conduta e desfechos, Farmácia, Exames, Sala de Estabilização, Observação clínica, pediátrica e obstétrica, Transferência regulada, Indicadores, Auditoria, Relatórios e Configurações.

## Perfis operacionais

Administração, Recepção, Técnico em Enfermagem, Médico, Farmácia, Técnico em RX, Regulação de Transferência e Auditoria.

## Executar localmente

Basta abrir `index.html` em um navegador, ou servir a pasta com qualquer servidor estático:

```
npx serve .
```

## Publicar no Netlify

1. Crie um repositório com esses arquivos (`index.html`, `style.css`, `script.js`, `api.js`, `netlify.toml`).
2. No Netlify, escolha "Add new site" → "Import an existing project" e selecione o repositório.
3. Build command: vazio. Publish directory: `.` (raiz do projeto) — já configurado em `netlify.toml`.
4. Deploy. O protótipo publicado é estático e não exige variáveis de ambiente públicas.

Alternativa rápida: arraste a pasta do projeto na área de "Deploys" do Netlify (drag and drop).

## Restaurar dados de demonstração

Na tela Cadastro e Recepção, use o botão "Restaurar dados demo" para limpar o `localStorage` e voltar aos dados fictícios originais.
