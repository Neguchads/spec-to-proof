---
name: spec-to-proof
description: Conduz mudanças de software que exigem critérios de aceite explícitos e verificação reproduzível. Use em funcionalidades, regressões difíceis, otimizações e protótipos com requisitos de qualidade ou desempenho. Adapte a profundidade ao risco da mudança.
---

# Da especificação à verificação

## Defina o que precisa funcionar

- Leia as regras locais e veja como a tarefa chega à implementação e como o projeto já a testa. Se o pedido e o repositório já dão a resposta, prossiga. Declare suposições que alterem o resultado. Pergunte apenas quando a resposta mudar materialmente o escopo, o comportamento ou o critério de aceite, ou quando uma autorização for necessária.
- Identifique o resultado observável, as restrições, o ambiente-alvo e a ordem das prioridades quando houver conflito. Trate restrições como limites e prioridades como critérios de decisão. Use metas existentes. Se um limite numérico não foi definido, meça a referência atual e apresente a comparação sem inventar um corte de aprovação.
- Antes de implementar, associe cada critério relevante a um cenário reproduzível com entrada ou estado inicial, ação, resultado esperado e evidência. Para uma correção simples, basta o cenário da falha e a checagem focada. Reaproveite especificações e testes existentes.

## Implemente e verifique

- Entregue a menor fatia completa pelo ponto de entrada real. Em regressões, reproduza a falha antes da correção quando possível. Preserve o cenário para repetir a verificação.
- Automatize o que pode ser decidido por uma checagem. Execute o caminho usado pelo usuário no ambiente relevante. Para desempenho, fixe configuração e carga, use a mesma metodologia antes e depois e reporte a unidade, a métrica e os limites da comparação. Exemplo: percurso fixo no jogo, carga representativa na API ou entradas fixas na CLI.
- Quando restar julgamento visual ou de interação, capture o artefato em estados fixos e grave o fluxo se o comportamento ao longo do tempo importar. Quando houver revisão independente disponível e autorizada, forneça apenas os critérios e o artefato para esse julgamento. Preserve a revisão de código exigida pelo projeto como uma checagem própria. Se a revisão independente for requisito e estiver indisponível, registre o critério como pendente.
- Use a skill especializada disponível para a etapa que precisar dela. Exemplos: `investigate-first` para causa incerta, `lean-build` para a fatia de implementação, `qa` para QA funcional, `benchmark` para desempenho web, `design-review` para acabamento visual, `recomp-project-auditor` para recompilação e `verify-and-stop` para verificação final. Use `spec` para formalizar uma issue quando o pedido incluir isso, ou `autoplan` quando o usuário pedir uma revisão abrangente do plano. Preserve o escopo e as autorizações da tarefa ao aplicar outros fluxos.
- Se duas tentativas seguidas deixarem o mesmo critério no mesmo estado, preserve o último resultado útil, reavalie a hipótese e rode o menor cenário completo que distinga as alternativas. Após uma correção, repita a checagem correspondente e os portões de regressão aplicáveis.

## Encerre com evidência

Entregue o resultado e informe os comandos ou cenários executados, o que passaram a comprovar e quais critérios falharam ou ficaram sem verificação. Só declare a entrega pronta quando os critérios obrigatórios passarem. Ao passar, encerre.

Método adaptado do [prompt do Abyssal Garden](https://github.com/Noniv/abyssal-garden/blob/main/prompt.txt).
