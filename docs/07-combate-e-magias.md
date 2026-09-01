# Combate e magias

Núcleo do jogo: atacar, trocar de escola e provocar uma reação. Controles de referência do GDD; remapeáveis (RF-017).

## Controles de referência

| Ação | Controle | Regra |
| --- | --- | --- |
| Mover | Analógico / WASD | Plano X/Z, oito direções. |
| Ataque leve | X / J | Sequência rápida de até 4 golpes. |
| Ataque pesado | Y / K | Quebra postura; pode carregar. |
| Magia | RT / L | Habilidade da escola ativa. |
| Esquiva | B / Espaço | Consome vigor; i-frames configuráveis. |
| Pulo | A / I | Ataques aéreos. |
| Trocar magia | D-pad / 1–4 | Troca imediata para o slot. |
| Especial | LT+RT / Q | Consome Medidor Arcano cheio. |

## Regras de troca

- Teto: 100 ms entre entrada e feedback visual.
- Troca não consome mana; habilidades consomem mana ou carga.
- Bloqueada em atordoamento, agarrão sofrido, morte e cenas travadas.
- Cancela ataques só nos marcadores configurados; fora da janela, buffer de até 150 ms (CA-002).
- Nova escola atualiza ícone, cor secundária, runas, som e lista de habilidades.
- Repetir a mesma escola não aumenta o multiplicador de variedade.

## Postura

Pesado e terra reduzem postura. A zero, o inimigo fica vulnerável por janela curta. Chefes não recebem agarrão comum: o controle vira dano de postura. Chefe imune a congelamento recebe dano de postura equivalente, com o mesmo feedback (CA-004).

## Arquitetura de uma escola

Uma escola é habilidades + status + afinidades + resposta visual. Até quatro escolas equipadas. Cada uma oferece ataque rápido, técnica carregada e efeito de afinidade no kit.

## Catálogo de escolas

| Escola | Função | Status | Rápida | Técnica | Limitação | Versão |
| --- | --- | --- | --- | --- | --- | --- |
| Fogo | Dano contínuo e explosão | Queimadura | Projétil Ígneo | Pilar de Chamas | Pouco controle; risco junto a barris. | M1 |
| Água | Controle, empurrão, preparação | Molhado | Onda Cortante | Maré Circular | Dano direto moderado. | M1 |
| Terra | Defesa e quebra de postura | Fratura | Punho de Rocha | Muralha Sísmica | Conjuração lenta. | MVP |
| Vento | Mobilidade e lançamento | Exposto | Lâmina de Ar | Tornado Ascendente | Pouco dano em alvos pesados. | MVP |
| Raio | Combo e propagação | Carregado | Arco Voltaico | Tempestade em Cadeia | Custo alto; fraco isolado. | 1.0 |
| Gelo | Imobilização e execução | Congelamento | Estilhaço | Prisão Glacial | Chefes encurtam o controle. | 1.0 |
| Luz | Suporte, purificação, escudo | Marcado | Raio Solar | Santuário | Menor dano bruto. | 1.0 |
| Sombra | Roubo de vida, alto risco | Corrupção | Garra Sombria | Eclipse Interior | Pode gastar vida ou aumentar dano recebido. | 1.0 |

## Reações

O status preparador existe **antes** do segundo elemento. Recarga por alvo impede ativação a cada frame. Consome o status quando a tabela indica. Escola de origem entra em dano, pontuação e XP.

| Reação | Gatilho | Resultado | Versão |
| --- | --- | --- | --- |
| Vapor | Fogo + Molhado | Consome Molhado; área que reduz precisão e dá dano leve. | M1 |
| Eletrocussão | Raio + Molhado | Dano salta para até 3 alvos molhados. | M1 (se raio no slice) ou 1.0 |
| Congelamento | Gelo + Molhado | Imobiliza; em chefe, grande dano de postura. | 1.0 |
| Magma | Fogo + Fratura | Área persistente: queimadura + queda de defesa. | MVP |
| Tempestade Ígnea | Vento + Queimadura | Espalha queimadura e lança leves. | MVP |
| Estilhaçar | Pesado/Terra + Congelado | Consome congelamento; dano explosivo. | 1.0 |
| Ruptura | Luz + Corrupção | Remove corrupção, dano verdadeiro, gera essência. | 1.0 |
| Tempestade Glacial | Vento + Gelo | Zona de lentidão e projéteis giratórios. | 1.0 |

Premissa M1: provar **Vapor** (fogo + molhado). Eletrocussão entra quando Raio existir, ou como segundo teste se o protótipo incluir um raio temporário. Não implementar as oito reações antes da matriz de quatro escolas estar estável.

## Status listados no RF-008

Queimadura, molhado, congelamento, choque, vulnerabilidade, corrupção. O catálogo de escolas também usa Fratura, Exposto, Carregado, Marcado. Tratar os extras como tags do mesmo `StatusComponent`.

## Medidor Arcano

Preenchido por variedade, trocas úteis, esquivas perfeitas e reações. Dano recebido reduz ganho recente. Em 100%: técnica especial ou Estado de Convergência por tempo limitado.

| Evento | Ganho inicial |
| --- | ---: |
| Golpe diferente no combo | 2 |
| Troca seguida de acerto em até 2 s | 5 |
| Reação elemental | 10 |
| Esquiva perfeita | 8 |
| Derrota de elite | 15 |
| Repetição excessiva | 0–1 |

## Progressão

| Moeda | Uso |
| --- | --- |
| Essência comum | Atributos. |
| Núcleos Elementais | Técnicas. |
| Fragmentos do Coração | Avanço de campanha / relíquias. |

Árvores: Combate, Arcano, Sobrevivência, Personagem. O jogador experimenta técnicas novas com regularidade **sem** completar todas as árvores numa campanha.

## Especiais por personagem

| Personagem | Especial |
| --- | --- |
| Kael | Convergência: combina as duas últimas escolas. |
| Lyra | Círculo Prisma: três zonas elementais. |
| Doran | Impacto Telúrico: arremessa e detona status. |
