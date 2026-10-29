# AGENTS

## Visão geral do repositório
- Projeto único (sem monorepo), React 18 + Vite 6.
- Entrada da aplicação: `src/main.jsx`.
- Componente principal e orquestração de estado: `src/App.jsx`.
- Componentes de UI:
  - `src/components/Display.jsx`
  - `src/components/Botao.jsx`
- Regras matemáticas atuais: `src/utils/operacoes.js`.

## Comandos reais (npm)
- Instalar dependências: `npm install`
- Ambiente de desenvolvimento: `npm run dev`
- Build de produção: `npm run build`
- Pré-visualizar build: `npm run preview`

## Verificação antes de concluir alterações
- Não existem scripts de lint, typecheck ou testes automatizados no `package.json`.
- Verificação mínima obrigatória: `npm run build`.

## Como a calculadora funciona hoje (importante para não quebrar fluxo)
- Operadores suportados na UI: apenas `+` e `-` (`OPERADORES` em `src/App.jsx`).
- Fluxo de estado em `App.jsx`:
  - `display`: valor mostrado na tela (string).
  - `anterior`: primeiro operando salvo para a próxima operação.
  - `operador`: operador selecionado (`+` ou `-`).
  - `novoNumero`: controla se o próximo dígito substitui o display ou concatena.
- Encadeamento de operações já existe: ao escolher novo operador com operação pendente, o app calcula primeiro o resultado anterior e segue com ele.
- `igual()` finaliza a operação pendente e reseta `anterior` e `operador`.
- `limpar()` reseta todo o estado para o padrão inicial.

## Contratos entre componentes
- `Botao` sempre executa `onClick(valor)` (não envia evento). Handlers devem esperar o valor do botão.
- `Display` só renderiza `valor`; não contém lógica de formatação.

## Convenções locais
- O código usa nomes e comentários em português (`anterior`, `operador`, `limpar`, `operacoes.js`).
- Mantenha essa convenção para consistência ao adicionar estado, funções e comentários.

## Limites atuais já documentados no código
- Há TODOs para:
  - adicionar `*` e `/` em `src/App.jsx`
  - implementar `multiplicar` e `dividir` em `src/utils/operacoes.js`
  - tratar divisão por zero (`operacoes.js`)
  - botão decimal e histórico (`App.jsx`)
- Se implementar essas partes, atualize `OPERADORES`, `calcular()` e utilitários de forma consistente.

## Fontes confiáveis neste repositório
- Priorize `package.json`, `vite.config.js` e código em `src/` como fonte de verdade executável.
- O `README.md` atual é template padrão do Vite e não descreve regras específicas da calculadora.
