# Roadmap de implementação

Engine: Godot 4.x, GDScript. Plataforma-base: PC. Dados de magia, golpe, inimigo e reação em Resources — sem valores centrais fixos no código.

## Fases

| Fase | Entrega | Critério de saída |
| --- | --- | --- |
| M0 — Prova | Movimento, câmera 2.5D, ataque leve/pesado, hit reaction. | Combate básico agradável; personagem anda, bate e reage a dano. |
| M1 — Vertical técnico | Fogo e água, troca de escola, status, uma reação, 3 inimigos. | Sistemas centrais validados; ver [definição de pronto M1](#definicao-de-pronto-m1). |
| M2 — Vertical slice | Fase curta (Vila das Cinzas), chefe Ignar, HUD, áudio, progressão mínima, save. | Qualidade representativa; ver [definição de pronto M2](#definicao-de-pronto-m2). |
| M3 — MVP | 3 fases, 4 magias, 8 inimigos, 3 chefes, acessibilidade básica. | Teste externo e balanceamento possíveis. |
| M4 — Conteúdo 1.0 | 3 personagens, 8 magias, 5 fases, modos extras. | Release candidate. |

Estimativa em semanas fica aberta até haver equipe. O GDD não fixa calendário — só marcos e saídas.

## Marcos de decisão

1. **Fim de M0** — se hit-stop, câmera e som não dão impacto, não expandir magias.
2. **Fim de M1** — se troca + reação não forem fluidas e úteis, não produzir mais fases. É o gate do produto.
3. **Fim de M2** — validar se a fase curta representa a qualidade-alvo (arte e áudio identificáveis como placeholder ou finais).
4. **Fim de M3** — só então discutir cooperativo, Lyra jogável e as quatro escolas restantes.

## Ordem de conteúdo

1. Arena de teste + Kael (M0).
2. Fogo, água, Molhado, Vapor ou Eletrocussão, três inimigos básicos (M1).
3. Vila das Cinzas + Ignar (M2).
4. Cidade Submersa + Nerissa; Fortaleza Rúnica + Volkar (M3).
5. Floresta dos Sussurros + Templo do Eclipse; Lyra e Doran; oito escolas (M4).

Premissa de recorte MVP (fases 1, 3 e 4 do [mapa de cenários](04-mapa-de-cenarios.md)): as três com chefes nomeados no núcleo de aprendizado do GDD. Floresta e Templo ficam para 1.0.

## Definição de pronto M1

Todos obrigatórios:

- Kael move em oito direções no plano 2.5D e executa leve, pesado e esquiva.
- Dois slots (fogo e água) trocam em até 100 ms com feedback de aura e HUD ([CA-001](09-requisitos.md)).
- Água aplica Molhado; uma reação (Vapor ou Eletrocussão) dispara uma vez por janela ([CA-003](09-requisitos.md)).
- Três inimigos distintos entram, atacam e morrem sem travar o estado do jogador.
- Magias e reações vêm de Resource; alterar o Resource muda o jogo sem editar o controlador ([CA-006](09-requisitos.md)).

## Definição de pronto M2 (vertical slice)

Do GDD, seção 15 — todos obrigatórios:

- Uma fase curta do início ao chefe, com exploração + arenas + Ignar.
- HUD com vida, vigor, mana, quatro slots (dois preenchidos), escola ativa e combo.
- Checkpoint e save restauram fase, loadout e opções ([CA-007](09-requisitos.md)).
- Áudio: música, golpe, magia e troca (volumes separados).
- Rank da fase calculado (mesmo que os pesos ainda sejam provisórios).
- Nenhum bloqueador no caminho crítico.

## Riscos a testar cedo

| Risco | Impacto | Teste / mitigação | Dono |
| --- | --- | --- | --- |
| Excesso de combinações | Balanceamento e bugs explodem. | Começar com 4 escolas e matriz explícita. | Design |
| Efeitos poluem a tela | Combate ilegível. | Orçamento de partículas e redução automática. | Arte + prog. |
| Combate sem impacto | Mecânica certa, sensação fraca. | Hit-stop, câmera, som e animação em M0. | Design + prog. |
| IA cerca o jogador | Dano injusto. | Tokens de ataque e limite de atacantes. | Prog. |
| Escopo cooperativo | Dobra testes. | Solo primeiro; coop só após M2. | Produto |
