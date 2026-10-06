# Kit OpenCode — Z.AI · Auto-seleção de modelos para a equipe

Configuração duplicável. Objetivo: **melhor resultado por token gasto**, sem nenhum dev precisar pensar em modelo.

## O roteamento (automático)

| Situação | Modelo | US$/M tokens (in · out) |
|---|---|---|
| Dia-a-dia: código, issues, PRs (sessão padrão) | `glm-5.3-flashx` | 0.37 · 1.25 |
| Análise pesada de pacote de issues / arquitetura | `glm-5.3` (via `/analise` ou agente `analista`) | 1.40 · 4.40 |
| Fundo invisível: títulos de sessão, resumos | `glm-4.5-air` (`small_model`) | 0.20 · 1.10 |

O modelo caro entra **só na análise, uma vez por pacote de issues**. Todo o resto do dia roda ~72% mais barato.

## Instalação (por dev, ~5 min)

1. **Copiar 4 itens** para a pasta global do OpenCode (`C:\Users\<voce>\.config\opencode\`):
   - `opencode.json`
   - `AGENTS.md`
   - `agents/analista.md`
   - `commands/analise.md`
   ⚠️ Já tem `opencode.json` ou `AGENTS.md` próprio? **Mescle**, não sobrescreva.
2. **Autenticar** (escolha UMA):
   - `setx ZAI_API_KEY "<chave-da-empresa>"` → feche e reabra o terminal; **ou**
   - `opencode auth login` → **Z.AI** → cole a chave
   ⚠️ A chave é da empresa. NUNCA em repo, print, chat ou commit.
3. **Conferir o endpoint**: o kit usa `https://api.z.ai/api/coding/paas/v4` (contrato atual). Se sua chave for de API comum e der erro 401/404, troque `baseURL` para `https://api.z.ai/api/paas/v4`.
4. **Reiniciar o OpenCode** e rodar `/models` → o provider `zai` deve listar os 3 modelos.

## Uso diário

- Trabalho normal: só conversar — flashx automático.
- Chegou pacote de issues? `/analise <cole as issues ou o caminho do arquivo>`
- Alternativa: trocar pro agente de análise (`/agent analista`) — ele é somente-leitura por segurança.
- Conferir o modelo ativo: `/models`.

## Com assento no Coding Plan (OAuth)?

Custo marginal vira $0. Troque as referências `zai/` → `zai-coding-plan/` em: `model` e `small_model` no `opencode.json`, e o `model:` no frontmatter de `agents/analista.md` e `commands/analise.md`.

## Manutenção do kit

- Atualização do kit = sobrescrever os 4 arquivos; configs de projeto local de cada dev não são tocadas.
- Projetos sensíveis podem endurecer permissões no próprio `opencode.jsonc` do projeto (ex.: `edit → ask`, mídia com `deny`).
- Os plugins (maestra/mesa) NÃO fazem parte deste kit e ficam fora do escopo.
