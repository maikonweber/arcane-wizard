# Mapa de cenários

Cinco fases no GDD. O plano 2.5D restringe profundidade; câmera lateral. Exploração curta (30–60 s) → arena (60–120 s) → recompensa → desafio ambiental → miniboss → descanso → chefe.

## Recorte por versão

| ID | Fase | Tema | Aprendizado | Chefe | Versão |
| --- | --- | --- | --- | --- | --- |
| `lvl_vila_cinzas` | Vila das Cinzas | Ruínas em chamas | Ataque, esquiva, fogo, água, vapor. | Ignar | M2 / MVP |
| `lvl_cidade_submersa` | Cidade Submersa | Canais e templos | Molhado, gelo, raio, riscos de área. | Nerissa | MVP |
| `lvl_fortaleza_runica` | Fortaleza Rúnica | Pedra e máquinas | Postura, terra, inimigos defensivos. | Volkar | MVP |
| `lvl_floresta_sussurros` | Floresta dos Sussurros | Natureza suspensa | Vento, lançamento, rotas alternativas. | Guardião Silvestre | 1.0 |
| `lvl_templo_eclipse` | Templo do Eclipse | Realidade fragmentada | Luz, sombra, todas as reações. | Aethron | 1.0 |

Seraph (luz corrompida) é o quinto chefe do 1.0; o GDD lista cinco chefes e cinco fases. Premissa: Seraph é miniboss ou chefe intermediário do Templo, antes de Aethron. Confirmar em [11-decisoes-pendentes.md](11-decisoes-pendentes.md).

## Grafo da campanha

```text
[Vila das Cinzas] ──Ignar──► [Cidade Submersa] ──Nerissa──► [Fortaleza Rúnica] ──Volkar──►
                                                                      │
                                                              MVP termina aqui
                                                                      │
                              1.0: [Floresta dos Sussurros] ──Guardião──► [Templo do Eclipse] ──Aethron
```

Premissa de ordem MVP: 1 → 3 → 4 no catálogo do GDD (Vila, Cidade, Fortaleza). A Floresta ensina vento; no MVP vento já entra como escola sem fase própria.

## Ritmo interno de uma fase

| Bloco | Duração-alvo | Conteúdo |
| --- | --- | --- |
| Exploração A | 30–60 s | Corredor, prop tutorial, relíquia visível ou lore. |
| Arena 1 | 60–120 s | 2 funções de inimigo. |
| Recompensa | curto | Essência, Núcleo, checkpoint. |
| Desafio ambiental | 1 puzzle/combate com prop | Ver tabela de objetos. |
| Arena 2 / miniboss | 60–120 s | 3–4 funções; elite opcional. |
| Descanso | seguro | Troca de loadout, árvore, save. |
| Chefe | variável | Mecânica central da fase. |

Vitória de fase: chefe derrotado **e** fragmento/relíquia coletado.

## Vila das Cinzas (M2)

Primeira fase e vertical slice. Ensina o núcleo: bater, esquivar, fogo, água, Vapor.

| Trecho | Encontros | Props | Nota |
| --- | --- | --- | --- |
| Rua queimada | Soldado | barril alquímico | Tutorial de ataque e barril. |
| Praça | Soldado + Arqueiro | — | Força prioridade de alvo. |
| Celeiro | Escudeiro | parede rachada | Terra/pesado ainda pode ser só pesado. |
| Forja (chefe) | Ignar | canais rasos / água residual | Resfriar armadura com água, quebrar com pesado. |

Relíquia da fase: Coração das Cinzas (fogo).

## Cidade Submersa (MVP)

Molhado como status de palco. Riscos de área permanentes.

| Trecho | Foco |
| --- | --- |
| Cais | Canais: raio eletrifica, gelo cria passagem (gelo pode ser só ambiental no MVP se a escola não estiver no loadout). |
| Templo inferior | Canalizador + Soldado; zonas molhadas. |
| Chefe Nerissa | Controlar áreas molhadas; evitar congelamento. |

Relíquia: Lágrima do Abismo (água).

## Fortaleza Rúnica (MVP)

Postura e defesa. Escudeiro e Brutamontes.

| Trecho | Foco |
| --- | --- |
| Muralha | Escudeiro; agarrão/água/postura. |
| Pátio de máquinas | Brutamontes; superarmadura. |
| Chefe Volkar | Aterramento, mobilidade, ataques em cadeia (vento/raio). |

Relíquia: Coroa da Montanha (terra) **ou** Olho da Tempestade (raio) — o GDD associa Volkar a vento/raio e a Fortaleza a terra. Premissa: a relíquia da fase é a Coroa; Volkar ensina a quebrar postura mesmo com tema de vento. Ver decisões.

## Floresta dos Sussurros (1.0)

Rotas alternativas, vento, lançamento. Chefe: Guardião Silvestre (não está na tabela de chefes §10.2; só na tabela de fases). Produzir ficha de chefe antes da arte.

Relíquia: Sopro dos Antigos (vento).

## Templo do Eclipse (1.0)

Luz, sombra, domínio de reações. Seraph (clones, rituais) depois Aethron (rouba escolas, copia padrões).

Relíquia: Presa do Eclipse (sombra). Fragmento Celestial (luz) pode ser drop de Seraph.

## Interação ambiental

| Objeto | ID de prop | Interações |
| --- | --- | --- |
| Barril alquímico | `prop_barrel_alchemical` | Fogo explode; água neutraliza. |
| Canal de água | `prop_water_channel` | Raio eletrifica; gelo cria passagem. |
| Parede rachada | `prop_cracked_wall` | Terra ou ataque pesado destrói. |
| Corrente de ar | `prop_air_current` | Vento ativa plataforma ou eleva o personagem. |
| Nó corrompido | `prop_corrupt_node` | Luz purifica; sombra absorve com risco. |

No M2 só barris e, se couber, parede rachada. Canais entram com a Cidade. Correntes com a Floresta. Nós com o Templo.

## Navegação técnica

`NavigationRegion3D` por fase. Limites de câmera por arena. Inimigo fora da câmera não ataca sem indicador de ameaça ([CA-010](09-requisitos.md)). Transição de arena sem tela de carga (RNF-003).
