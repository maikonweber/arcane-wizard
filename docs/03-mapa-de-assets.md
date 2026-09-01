# Mapa de assets

Estilo: fantasia sombria, combate arcade legível. Cores de escola consistentes em VFX, HUD e aura. Informação elemental **não** depende só de cor — cada escola tem ícone e forma próprios ([CA-009](09-requisitos.md)).

Direção ainda aberta: modelos 3D 2.5D (premissa do GDD, `CharacterBody3D`) ou sprites 2D. Convenções abaixo servem aos dois; a extensão muda (`glb` vs `png`).

**Resolução-alvo de UI:** funcional de 1280×720 a 3840×2160. Viewport atual do stub: 1280×720.

## Estrutura

```text
assets/
  characters/
    kael/
    lyra/
    doran/
  enemies/
  bosses/
  environments/
    vila_cinzas/
    floresta_sussurros/
    cidade_submersa/
    fortaleza_runica/
    templo_eclipse/
  vfx/
    schools/
    reactions/
    hits/
  ui/
    hud/
    icons/
    menus/
  audio/
    music/
    sfx/
    voice/
  relics/
```

## Convenção de nome

`{grupo}_{sujeito}_{variante}_{estado}`

Minúsculas, `snake_case`. IDs estáveis no Resource, não no nome de arquivo.

| Grupo | Prefixo | Exemplo |
| --- | --- | --- |
| Personagem | `char_` | `char_kael_idle` |
| Inimigo | `ene_` | `ene_soldado_walk` |
| Chefe | `boss_` | `boss_ignar_armor` |
| Cenário | `env_` | `env_vila_cinzas_far` |
| Prop | `prop_` | `prop_barrel_alchemical` |
| Relíquia | `rel_` | `rel_coracao_cinzas` |
| Magia | `abl_` | `abl_fire_bolt` |
| Reação | `rxn_` | `rxn_electrocute` |
| Ícone HUD | `ico_` | `ico_school_fire` |
| UI | `ui_` | `ui_slot_magic` |

Estados de ator: `_idle`, `_walk`, `_run`, `_attack_l`, `_attack_h`, `_cast`, `_dodge`, `_hit`, `_knockdown`, `_air`, `_special`, `_dead`.

## Paleta elemental (HUD + VFX)

Forma distinta obrigatória; cor é reforço.

| Escola | ID | Cor de apoio | Forma do ícone |
| --- | --- | --- | --- |
| Fogo | `fire` | vermelho-laranja | triângulo / chama |
| Água | `water` | azul | gota |
| Terra | `earth` | ocre | hexágono |
| Vento | `wind` | ciano-claro | crescente |
| Raio | `lightning` | amarelo | raio ziguezague |
| Gelo | `ice` | branco-azulado | losango |
| Luz | `light` | dourado | sol / cruz |
| Sombra | `shadow` | violeta-escuro | crescente invertido / olho |

## Personagens — pacote de produção

Animações mínimas = estados do GDD §6.2. Placeholder aceito até M2 se identificado.

| ID | Sujeito | M0 | M1 | M2 | MVP | 1.0 |
| --- | --- | --- | --- | --- | --- | --- |
| CHAR-01 | Kael mesh/sprite + idle/walk/attack_l/hit | Sim | Sim | Sim | Sim | Sim |
| CHAR-02 | Kael attack_h, dodge, jump, death | — | Sim | Sim | Sim | Sim |
| CHAR-03 | Kael cast, special, auras das escolas equipadas | — | 2 escolas | 4 | 4 | 8 |
| CHAR-04 | Lyra (IA) mesh + kit reduzido | — | — | opcional | Sim | Sim |
| CHAR-05 | Doran | — | — | — | — | Sim |

## Inimigos e chefes

Lista canônica em [08-inimigos-e-encontros.md](08-inimigos-e-encontros.md). Cada inimigo precisa: idle, walk, attack, hit, death. Chefes: fases visuais da mecânica central.

| ID | Arquivo-base | Versão |
| --- | --- | --- |
| ENE-01 | `ene_soldado_corrompido` | Protótipo |
| ENE-02 | `ene_arqueiro_runico` | Protótipo |
| ENE-03 | `ene_escudeiro_pedra` | Protótipo |
| ENE-04 | `ene_canalizador` | MVP |
| ENE-05 | `ene_assassino_vento` | MVP |
| ENE-06 | `ene_parasita_arcano` | MVP |
| ENE-07 | `ene_devorador` | MVP |
| ENE-08 | `ene_brutamontes` | MVP |
| ENE-09 | `ene_mimico_elemental` | 1.0 |
| ENE-10 | `ene_arauto_eclipse` | 1.0 |
| BOSS-01 | `boss_ignar` | M2 |
| BOSS-02 | `boss_nerissa` | MVP |
| BOSS-03 | `boss_volkar` | MVP |
| BOSS-04 | `boss_guardiao_silvestre` | 1.0 |
| BOSS-05 | `boss_seraph` | 1.0 |
| BOSS-06 | `boss_aethron` | 1.0 |

## Cenários

Cada fase: fundo `far` / `mid` / `near` (ou malha única), chão navegável, props da [tabela ambiental](04-mapa-de-cenarios.md).

| ID | Pasta | Versão |
| --- | --- | --- |
| ENV-01 | `environments/vila_cinzas/` | M2 / MVP |
| ENV-02 | `environments/cidade_submersa/` | MVP |
| ENV-03 | `environments/fortaleza_runica/` | MVP |
| ENV-04 | `environments/floresta_sussurros/` | 1.0 |
| ENV-05 | `environments/templo_eclipse/` | 1.0 |

## Magias e reações (VFX/SFX)

Uma cena ou sprite sheet por habilidade rápida e por técnica. Reações têm VFX único (não reusar o da escola).

| Escola | Rápida | Técnica | MVP |
| --- | --- | --- | --- |
| Fogo | `abl_fire_bolt` | `abl_fire_pillar` | Sim |
| Água | `abl_water_wave` | `abl_water_tide` | Sim |
| Terra | `abl_earth_fist` | `abl_earth_wall` | Sim (4ª ou 3ª) |
| Vento | `abl_wind_blade` | `abl_wind_tornado` | Sim (4ª ou 3ª) |
| Raio | `abl_lightning_arc` | `abl_lightning_storm` | 1.0 |
| Gelo | `abl_ice_shard` | `abl_ice_prison` | 1.0 |
| Luz | `abl_light_ray` | `abl_light_sanctuary` | 1.0 |
| Sombra | `abl_shadow_claw` | `abl_shadow_eclipse` | 1.0 |

Premissa das 4 magias do MVP: Fogo, Água, Terra, Vento — cobre dano, controle, postura e mobilidade. Raio/Gelo/Luz/Sombra no 1.0. Se o slice M2 só precisa de Fogo+Água, Terra e Vento entram em M3.

Reações com asset próprio no MVP: Vapor, Eletrocussão, Magma, Estilhaçar. Demais no 1.0. Catálogo completo em [07-combate-e-magias.md](07-combate-e-magias.md).

## Relíquias

Oito props/ícones. Aparecem na vitória de fase e na UI da Estrutura.

| ID | Arquivo | Escola |
| --- | --- | --- |
| REL-01 | `rel_coracao_cinzas` | Fogo |
| REL-02 | `rel_lagrima_abismo` | Água |
| REL-03 | `rel_coroa_montanha` | Terra |
| REL-04 | `rel_sopro_antigos` | Vento |
| REL-05 | `rel_olho_tempestade` | Raio |
| REL-06 | `rel_cristal_inverno` | Gelo |
| REL-07 | `rel_fragmento_celestial` | Luz |
| REL-08 | `rel_presa_eclipse` | Sombra |

## HUD e UI

| ID | Asset | Notas |
| --- | --- | --- |
| UI-01 | Barras de vida e vigor | Canto superior esquerdo. |
| UI-02 | Mana/cargas + 4 slots | Escola ativa: forma + ícone + nome + cor. |
| UI-03 | Medidor Arcano | Mostra as duas últimas escolas. |
| UI-04 | Combo / variedade / reação | Sem cobrir o combate. |
| UI-05 | Vida e postura de chefe | Centro superior. |
| UI-06 | Feedback de troca | Runa, nome, aura. |
| UI-07 | Números de dano e resistência | Resistência com ícone distinto. |
| UI-08 | Menus: pause, opções, save, árvore | Textos externos às cenas. |

## Áudio mínimo

Canais separados: música, efeitos, voz, master (RNF-008).

| ID | Evento | Quando |
| --- | --- | --- |
| AUD-01 | Música da arena de teste | M0 |
| AUD-02 | Hit, dodge, footsteps | M0 |
| AUD-03 | Troca de escola, magia fogo/água | M1 |
| AUD-04 | Reação elemental | M1 |
| AUD-05 | Música Vila das Cinzas + Ignar | M2 |
| AUD-06 | Falha de recurso (mana) | M1 |
