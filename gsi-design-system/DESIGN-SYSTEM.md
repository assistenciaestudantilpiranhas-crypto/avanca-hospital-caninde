# GSI Design System

O GSI Design System (GDS) e um ativo tecnico e institucional da GSI HealthTech. Ele define a base visual, interativa e operacional para interfaces do GSI ONE e das implementacoes associadas ao Avanca Hospital.

## Filosofia

O GDS existe para reduzir variacao desnecessaria, aumentar seguranca de uso, melhorar leitura clinica e acelerar evolucao do produto com consistencia. Em sistemas hospitalares, design nao e apenas aparencia: e parte da qualidade operacional, da rastreabilidade e da seguranca da informacao.

## Principios

- Clareza clinica antes de ornamentacao.
- Consistencia entre modulos assistenciais e administrativos.
- Acessibilidade em condicoes reais de uso hospitalar.
- Governanca para alteracoes feitas por pessoas e agentes de IA.
- Rastreabilidade de decisoes visuais relevantes.
- Preservacao de fluxos, regras de negocio e integracoes.

## Escopo

O GDS cobre:

- tokens de design;
- componentes de interface;
- padroes de UX clinica;
- acessibilidade;
- motion;
- orientacao para agentes de IA;
- prompts de revisao e criacao de telas.

O GDS nao define regras clinicas, protocolos assistenciais, regras de faturamento, autorizacoes, banco de dados ou politicas de seguranca. Esses temas pertencem aos documentos funcionais, tecnicos e institucionais correspondentes.

## Estrutura

- `README.md`: apresentacao do GDS.
- `DESIGN.md`: guia rapido para agentes de IA.
- `DESIGN-SYSTEM.md`: documento principal.
- `TOKENS.md`: tokens e fundamentos visuais.
- `COMPONENTS.md`: componentes iniciais.
- `CLINICAL-UX.md`: principios de experiencia clinica.
- `ACCESSIBILITY.md`: acessibilidade aplicada ao contexto hospitalar.
- `MOTION.md`: regras para movimento e transicoes.
- `AI-DESIGN-ENGINE.md`: regras para uso de IA no design.
- `PROMPTS.md`: prompts padronizados para evolucao e revisao.

## Governanca

Mudancas no GDS devem ser pequenas, justificadas e rastreaveis. Alteracoes que impactem identidade, semantica de risco, componentes clinicos, acessibilidade ou governanca de IA devem ser documentadas.

Qualquer aplicacao do GDS em telas existentes deve preservar:

- fluxos assistenciais;
- regras de negocio;
- funcoes JavaScript;
- eventos;
- IDs;
- integracoes;
- Supabase;
- localStorage;
- auditabilidade.

