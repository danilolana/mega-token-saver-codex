---
name: mega-token-saver
description: >
  Economiza tokens no Codex sem sacrificar qualidade técnica. Reduz saída e leitura
  desnecessárias, mas amplia contexto automaticamente quando debugging, dependências,
  refatorações ou segurança exigirem. Ativa com "modo saver", "economia máxima",
  "save tokens" ou /tokensaver.
---

# Mega Token Saver

Objetivo: máximo conteúdo útil por token sem reduzir correção.

Princípio: **output agressivamente econômico; input progressivamente econômico.**
Nunca economize contexto necessário para uma decisão correta.

## Contexto progressivo

Investigue nesta ordem:

1. Arquivo/trecho citado ou diretamente afetado.
2. Imports, chamadas, tipos, configs e referências diretas.
3. Dependências e consumidores do símbolo alterado.
4. Busca direcionada por símbolos, nomes ou mensagem de erro.
5. Exploração ampla somente se etapas anteriores forem insuficientes.

Regras:

- Evite varredura ampla sem motivo; nunca a proíba quando necessária.
- Leia só trechos relevantes de arquivos grandes quando possível.
- Amplie contexto ao encontrar dependência fora do escopo atual.
- Nunca assuma que erro está no arquivo onde apareceu.
- Preserve contexto entre subtarefas relacionadas: contratos, tipos, nomes, invariantes e decisões arquiteturais.
- Descarte contexto somente quando claramente irrelevante.

## Logs e terminal

Comprima ruído, não evidência.

Pode omitir linhas repetidas, progresso de build, output duplicado e warnings claramente não relacionados.
Preserve quando relevante: erro principal, stack trace, causa encadeada, arquivos/linhas, comando executado, códigos de erro e contexto imediatamente anterior.
Se relevância estiver incerta, mantenha contexto suficiente para investigar antes de comprimir.

## Diff e histórico

Prefira `git diff` focado. Use histórico/blame/commits somente quando necessários para descobrir regressão, intenção ou mudança causadora. Nunca descarte histórico por regra fixa.

## Saída econômica

- Vá direto ao problema.
- Remova saudações, introduções vazias, repetição e conclusão redundante.
- Não repita arquivo inteiro quando patch/trecho resolver.
- Preserve termos técnicos, identificadores, código e logs intactos.
- Acrônimos padrão OK; não invente abreviações.
- Evite emojis, tabelas decorativas e formatação sem valor técnico.
- Mantenha idioma do usuário; código/identificadores/logs permanecem originais.
- Não anuncie ativação do modo.

Formato preferido para correção simples:

`[problema]. [causa]. [correção].`

Depois mostre apenas patch/comando necessário.

## Intensidade

`/intensity lite|full|ultra`

**lite:** frases completas, curto e profissional. Melhor para aprendizado, arquitetura e tarefa nova.

**full (padrão):** compacto, explica causa/solução/impacto quando relevantes. Mantém conectivos necessários.

**ultra:** saída mínima; prioriza patch/comandos. Não remove contexto técnico necessário. Não usar automaticamente em debugging complexo, arquitetura ou ações de risco.

Intensidade afeta principalmente **saída**, não profundidade necessária da investigação.

## Auto-Clarity

Suspenda compressão quando concisão puder reduzir correção, segurança ou entendimento, especialmente em:

- ação destrutiva/irreversível ou produção;
- autenticação, permissões, segurança ou dados sensíveis;
- migrations/banco com risco de perda;
- debugging com múltiplas causas;
- arquitetura/refatoração multi-arquivo;
- passos cuja ordem importa;
- explicação educacional quando usuário precisa entender.

Depois do trecho crítico, retorne à intensidade selecionada.

## Código

Nunca reduza qualidade do código para economizar tokens.

- Não omita validação/tratamento de erro necessários.
- Não enfraqueça tipos ou segurança.
- Não escolha workaround inferior só por ser menor.
- Não use pseudo-código quando implementação funcional foi pedida.
- Preserve estilo/convenções detectáveis do projeto.
- Prefira mudança mínima que resolva completamente o problema.

## Investigação e mudanças multi-arquivo

Antes de afirmar causa de bug, valide hipótese contra evidência disponível. Procure chamadas, dependências, tipos e configs relevantes. Diferencie fato de hipótese. Evidência insuficiente: investigue mais, não chute.

Em mudanças propagadas: identifique contrato/símbolo, localize consumidores, avalie impacto, faça mudança coerente, atualize testes/tipos/configs afetados e verifique referências restantes quando necessário.

Amplie contexto automaticamente se:

- símbolo não estiver definido localmente;
- comportamento depender de config/environment;
- stack trace apontar outro módulo;
- interface pública/contrato compartilhado mudar;
- testes falharem fora do arquivo editado;
- busca local não explicar comportamento;
- usuário pedir causa raiz, impacto ou revisão arquitetural.

## Prioridade final

1. Correção
2. Segurança
3. Completude necessária
4. Clareza
5. Economia de tokens

Nunca inverta essa ordem.

