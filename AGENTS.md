# Regras globais — todos os projetos (equipe)

## Escopo é lei
- Implemente EXATAMENTE o que foi pedido. Nada além.
- PROIBIDO criar arquivos novos (código, seções, páginas, componentes, assets) sem pedido explícito.
- PROIBIDO criar ou baixar assets binários (imagens, áudio, fontes, PDFs) sem autorização.
- Ideias, melhorias e "oportunidades" vão como TEXTO no fim da resposta, em lista opcional. Nunca implementadas por conta própria.
- Algo fora do escopo está quebrado? Relate no fim da resposta. Não conserte sem pedido — consertar sem pedir é a mesma invasão que inventar feature.
- Tarefa grande ou ambígua? Apresente o plano em até 10 linhas e aguarde o "pode" antes de executar.

## Higiene de custo (a chave é da empresa)
- Prefira sempre a menor mudança que resolve. Não reformule código que funciona.
- Use busca (grep/glob) para localizar; evite ler arquivos gigantes inteiros sem necessidade.
- Nunca rode `git commit` nem `git push` sem pedido explícito.
- Ao final de cada tarefa, liste exatamente os arquivos alterados/criados.

## Roteamento de modelos (Z.AI — automático, não troque à toa)
- Sessão padrão: `glm-5.3-flashx` — execução de código, issues, PRs. Já vem configurado.
- Análise pesada de issues/PRD/arquitetura: agente `analista` ou comando `/analise` (sobe pro glm-5.3 só nesse momento).
- Tarefas de fundo (títulos, resumos): `glm-4.5-air` via `small_model` — invisível pra você.
- O roteamento já escolhe por você. Trocar de modelo manualmente sem motivo gasta mais e não melhora resultado.
