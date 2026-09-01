# Mapa de personagens

Fichas longas em [`../personagens/`](../personagens/). Este arquivo é o índice de produção: quem entra em qual versão, atributos e relações.

## Recorte

| ID | Nome | Função | Protótipo | MVP | 1.0 |
| --- | --- | --- | --- | --- | --- |
| `char_kael` | Kael | Protagonista jogável | Sim | Sim | Sim |
| `char_lyra` | Lyra | Parceira IA (jogável em 1.0) | Não | IA | Jogável |
| `char_doran` | Doran | Mentor / terceiro kit | Não | Não | Jogável |
| `npc_malakar` | Malakar | Antagonista, voz e chefe final temático | Voz/corrupção | Voz | Chefe Aethron / arco |
| `fac_guardioes` | Guardiões Arcanos | Facção do jogador | Lore | Lore | Lore |
| `fac_eclipse` | Ordem do Eclipse | Antagonista organizacional | Encontros | Sim | Sim |
| `fac_crawlers` | Cultos de Crawlers / Crawlers | Inimigos e células | 3 tipos | 8 tipos | 12 tipos |

## Jogáveis

### Kael — Guardião Arcano

Protagonista equilibrado, caçador de demônios. Arma: espada rúnica. Absorção: equipa poderes das relíquias recuperadas. Conflito: ligação com Malakar aumenta corrupção. Combos flexíveis e boa sobrevivência; não domina alcance nem dano máximo. Especial: **Convergência** — combina as duas últimas escolas usadas.

### Lyra — Feiticeira Errante

Parceira, investigadora, especialista em selos. Arma: catalisador flutuante. Eco arcano: a terceira magia repete com 40% do poder. Purifica Kael e desfaz rituais da Ordem. Controle de grupos e geração de status; vida e resistência menores. Especial: **Círculo Prisma** — três zonas elementais simultâneas.

No MVP ela acompanha, combate e aceita comandos simples (RF-021). Não é selecionável.

### Doran — Punho Rúnico

Mentor desaparecido, tanque e quebra de postura. Arma: manoplas rúnicas. Imbuir: magia ativa altera golpes pesados. Narrativa: infiltrado na Ordem ou corrompido por uma relíquia (GDD deixa as duas). Dano de postura e resistência; mobilidade baixa. Especial: **Impacto Telúrico** — arremessa inimigos e detona status.

## Atributos-base (referência)

Valores relativos a 100 = média de Kael. Ajustáveis por Resource.

| Personagem | Vida | Mana | Ataque | Velocidade | Controle | Dificuldade |
| --- | ---: | ---: | ---: | ---: | ---: | --- |
| Kael | 100 | 100 | 100 | 100 | 100 | Baixa |
| Lyra | 75 | 130 | 85 | 115 | 130 | Média |
| Doran | 140 | 80 | 125 | 75 | 105 | Média |

## Relacionamentos

```text
Malakar ──corrupção──► Kael ◄──purifica── Lyra
                │                    │
                └──── selos / relíquias ────┘
                              │
                         Doran (?) ── infiltrado ou corrompido
                              │
                    Ordem do Eclipse ── cultos de Crawlers
```

## Antagonista

**Malakar, o Devorador de Eras.** Essência partida em oito relíquias. Cada selo perdido enfraquece o Véu. A Presa do Eclipse contém consciência e corrupção. Kael é o hospedeiro candidato. Não é personagem jogável.

## Identidade visual (produção)

Premissa até fechar [direção 2.5D](11-decisoes-pendentes.md): silhueta e paleta distintas por personagem, escola ativa como aura secundária.

| Personagem | Paleta-base | Silhueta |
| --- | --- | --- |
| Kael | índigo, aço, runa âmbar | espadachim, capa curta |
| Lyra | prata, violeta, catalisador | feiticeira, catalisador orbital |
| Doran | pedra, bronze, runas de terra | tanque, manoplas grandes |
| Malakar | eclipse, ouro podre, sombra | presença / voz; corpo só em CG ou chefe |
