# Visão do produto

**Estrutura** é um beat 'em up lateral 2.5D de fantasia sombria. Dois magos caçadores enfrentam cultistas e criaturas do Abismo. O jogador troca escolas de magia no meio dos combos, provoca reações elementais e recupera relíquias que mantêm um demônio milenar aprisionado.

Pasta no monorepo: `ArcaneWizard/`. Plataforma-base do GDD: PC. Engine: Godot 4.x / GDScript. Público: 12+; fãs de ação arcade, combos e progressão. Modo: campanha solo com parceiro por IA; cooperativo local previsto (pós-MVP).

## Pitch

Kael e Lyra são magos caçadores enviados para impedir que a Ordem do Eclipse complete um ritual de invocação. A dupla investiga cultos de Crawlers, interrompe cerimônias, recupera relíquias e enfrenta demônios libertados pelas rachaduras da Estrutura.

## Background

Há milhares de anos, Malakar, o Devorador de Eras, tentou romper o Véu entre o mundo humano e o Abismo. Incapazes de destruí-lo, os primeiros magos caçadores dividiram sua essência em oito relíquias. Unidas, formam a **Estrutura Arcana**: prisão, fonte de magia e barreira contra invasões.

A Ordem do Eclipse, ligada aos cultos de Crawlers, localizou os selos. Pretende desmontar a Estrutura num alinhamento celestial e usar um hospedeiro humano para trazer Malakar de volta. Cada relíquia removida enfraquece o Véu e transforma regiões inteiras.

Kael absorve energia das relíquias e troca poderes no combate; Malakar invade sua mente. Lyra domina rituais de selamento e tenta impedir que Kael vire o receptáculo definitivo.

Nota de produção: [`backgroud.md`](backgroud.md) é o pitch curto original; este arquivo é o canônico.

## Pilares

| Pilar | Aplicação |
| --- | --- |
| Combate legível | Antecipação clara, cores consistentes, resposta imediata. |
| Troca significativa | Cada magia resolve situações diferentes; trocar vence repetir. |
| Expressão do jogador | Combos livres, cancelamentos e reações permitem estilo próprio. |
| Fantasia de poder | Impactos fortes, evolução visual, especiais espetaculares. |
| Escopo controlado | Primeiro marco: 1 personagem, 4 magias, 1 fase, 1 chefe. |

## Diferenciais

- Troca de magia durante golpes, sem interromper o combo.
- Reações elementais pela ordem das magias.
- Personagens com funções distintas sobre o mesmo conjunto mágico.
- Inimigos que mudam resistência, posição e comportamento conforme o elemento.
- Cenários com objetos afetados por fogo, gelo, vento, raio e terra.

## Relíquias da Estrutura

| Relíquia | Escola | Papel |
| --- | --- | --- |
| Coração das Cinzas | Fogo | Aprisiona a fúria de Malakar. |
| Lágrima do Abismo | Água | Controla as passagens entre mundos. |
| Coroa da Montanha | Terra | Sustenta fisicamente a Estrutura. |
| Sopro dos Antigos | Vento | Impede a voz do demônio de atravessar o Véu. |
| Olho da Tempestade | Raio | Alimenta a rede de selos. |
| Cristal do Inverno | Gelo | Conserva o corpo adormecido. |
| Fragmento Celestial | Luz | Purifica a influência demoníaca. |
| Presa do Eclipse | Sombra | Contém a consciência e a corrupção de Malakar. |

## Facções

| Facção | Função |
| --- | --- |
| Guardiões Arcanos | Magos caçadores das relíquias e do Véu. |
| Ordem do Eclipse | Quer libertar e controlar Malakar. |
| Cultos de Crawlers | Células de sacrifício; abrem rachaduras pequenas. |
| Crawlers | Criaturas do Abismo que atravessam falhas na Estrutura. |

## Loop principal

| Etapa | Ação | Resultado |
| --- | --- | --- |
| Explorar | Avançar pela fase e descobrir rotas. | Recursos, história, encontros. |
| Combater | Golpes, magia, esquiva, troca. | Essências, pontuação, progressão. |
| Adaptar | Ler resistência, escudo e posição. | Poder e reação certos. |
| Evoluir | Comprar técnicas e melhorar escolas. | Combos e especializações. |
| Confrontar | Derrotar miniboss ou chefe. | Relíquia recuperada; avanço narrativo. |

Ritmo de fase: exploração curta (30–60 s) → arena (60–120 s) → recompensa → desafio ambiental → miniboss → descanso/melhoria → chefe.

## Condições

| Tipo | Condição |
| --- | --- |
| Vitória de arena | Inimigos obrigatórios derrotados. |
| Vitória de fase | Chefe derrotado e fragmento coletado. |
| Derrota | Vida a zero sem carga de retorno. |
| Rank | Tempo, dano recebido, variedade, combo máximo, reações. |

## Recorte de versões

| Versão | Conteúdo mínimo |
| --- | --- |
| Protótipo | Kael, arena, ataques básicos, fogo/água, 3 inimigos, troca instantânea. |
| MVP | Kael, 4 magias, 3 fases, 8 inimigos, 3 chefes, progressão e save. |
| 1.0 | 3 personagens, 8 magias, 5 fases, 12 inimigos, 5 chefes e modos extras. |

O núcleo a provar: atacar, trocar de magia e provocar uma reação. Se a troca não for rápida, legível e útil, corrige-se o sistema antes de ampliar fases ou elenco.
