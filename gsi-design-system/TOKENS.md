# Tokens de Design

Os tokens do GDS documentam a linguagem visual do GSI ONE e do Avanca Hospital. A base atual usa azul-petroleo/navy, verde institucional/teal, neutros frios e estados clinicos de alto reconhecimento.

## Cores institucionais

- `--blue-950`: `#071d35` - navy profundo, usado em sidebar, fundos institucionais e textos fortes.
- `--blue-900`: `#0b2b4c` - azul institucional escuro.
- `--blue-800`: `#15456d` - azul-petroleo.
- `--blue-700`: `#1d5d89` - azul de acao, foco e destaque.
- `--blue-600`: `#2a72a8` - azul de apoio.
- `--blue-100`: `#e8f1f8` - fundo informativo claro.

## Verde institucional

- `--green-700`: `#0f7441` - verde forte para status positivo.
- `--green-600`: `#169653` - verde principal de confirmacao.
- `--green-100`: `#e6f6ee` - fundo positivo claro.

## Neutros

- `--gray-950`: `#1f2933` - texto principal.
- `--gray-700`: `#425466` - texto secundario.
- `--gray-500`: `#6b7b8c` - texto auxiliar.
- `--gray-300`: `#d9e2ec` - bordas relevantes.
- `--gray-200`: `#e8eef5` - bordas suaves.
- `--gray-100`: `#f4f7fb` - fundo de superficie.
- `--gray-50`: `#f8fafc` - fundo de pagina.
- `--white`: `#ffffff` - superficie principal.

## Estados e risco

- `--red`: `#d93025` - erro, risco alto, criticidade.
- `--orange`: `#ef7d22` - alerta importante.
- `--yellow-500`: `#f4c542` - atencao e destaque.
- `--yellow-100`: `#fff6d8` - fundo de atencao.
- `--risk-yellow`: `#d99a00` - classificacao de risco amarela.
- `--risk-blue`: `#276ef1` - classificacao de risco azul.

## Tipografia

- Familia: `"Inter", "Segoe UI", Arial, Helvetica, sans-serif`.
- Monospace tecnico: `"Inter", monospace`.
- Peso regular: 400.
- Peso medio: 500.
- Peso semibold: 600.
- Peso bold: 700.
- Pesos 800 e 900 podem ser usados em titulos institucionais ou numeros de destaque, sem comprometer leitura de dados clinicos.

## Escala de espacamento

- `space-1`: 4 px.
- `space-2`: 8 px.
- `space-3`: 12 px.
- `space-4`: 16 px.
- `space-5`: 20 px.
- `space-6`: 24 px.
- `space-8`: 32 px.
- `space-10`: 40 px.

## Bordas e radius

- `--radius-sm`: 7 px - controles compactos.
- `--radius`: 10 px - cards, inputs, paineis e modais.
- Radius circular: 999 px - badges, pills e avatares.
- Borda padrao: 1 px solida com neutro frio.
- Sidebar atual: `--sidebar-width`: 296 px.

## Sombras

- `--shadow-soft`: `0 8px 22px rgba(9, 35, 63, 0.07)` - elevacao discreta.
- `--shadow`: `0 20px 48px rgba(9, 35, 63, 0.14)` - paineis e overlays.
- `--shadow-lift`: `0 14px 30px rgba(9, 35, 63, 0.16)` - destaque temporario.

## Z-index

- Base: conteudo normal.
- `10`: elementos fixos locais.
- `100`: sidebar, header fixo ou barras de contexto.
- `500`: dropdowns e popovers.
- `900`: overlays.
- `1000`: modais.
- `1100`: notificacoes criticas.

## Estados visuais

- Foco: contorno ou halo visivel com azul institucional.
- Hover: mudanca discreta de fundo, borda ou sombra.
- Active: reducao sutil de elevacao ou tom.
- Disabled: menor contraste, cursor apropriado e sem interacao.
- Loading: indicador claro sem bloquear leitura clinica desnecessariamente.
- Movimento padrao: `--ease`: `cubic-bezier(0.22, 1, 0.36, 1)`.
