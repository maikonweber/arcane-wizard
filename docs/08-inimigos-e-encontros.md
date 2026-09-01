# Inimigos e encontros

IA: patrulhar, perseguir, atacar, defender, recuar e reagir a controle (RF-012). No máximo **quatro funções** simultâneas no MVP. Distância não fica fora da câmera por muito tempo. `EncounterDirector` controla ondas, limite ativo, spawn e pausa entre grupos. Tokens de ataque: limite de atacantes simultâneos.

## Catálogo

| ID | Inimigo | Papel | Comportamento | Versão |
| --- | --- | --- | --- | --- |
| `ene_soldado` | Soldado Corrompido | Básico | Aproxima, sequência curta, pode ser lançado. | Protótipo |
| `ene_arqueiro` | Arqueiro Rúnico | Distância | Reposiciona; força prioridade de alvo. | Protótipo |
| `ene_escudeiro` | Escudeiro de Pedra | Defensor | Bloqueia a frente; água, agarrão e postura respondem. | Protótipo |
| `ene_canalizador` | Canalizador | Suporte | Fortalece aliados e cria zonas; prioridade alta. | MVP |
| `ene_assassino` | Assassino do Vento | Ágil | Ataca pelas costas; esquiva projéteis. | MVP |
| `ene_parasita` | Parasita Arcano | Controle | Bloqueia uma escola por curto período. | MVP |
| `ene_devorador` | Devorador | Adaptativo | Ganha resistência ao elemento repetido. | MVP |
| `ene_brutamontes` | Brutamontes | Pesado | Superarmadura; vulnerável após ataques fortes. | MVP |
| `ene_mimico` | Mímico Elemental | Especial | Copia a escola ativa; obriga troca. | 1.0 |
| `ene_arauto` | Arauto do Eclipse | Elite | Sombra + escola da região. | 1.0 |

O GDD pede 8 inimigos no MVP e 12 no 1.0. A tabela tem 10 nomes. Premissa: os oito do MVP são as linhas “Protótipo” + “MVP”; 1.0 acrescenta Mímico, Arauto e dois tipos regionais (um por fase nova) ainda sem nome.

## Composições sugeridas

| Contexto | Funções | Teto na tela |
| --- | --- | --- |
| Tutorial Vila | Soldado | 4 |
| Arena mista Vila | Soldado + Arqueiro | 6 |
| Porta / corredor | Escudeiro + Soldado | 4 |
| Cidade | Canalizador + Soldado + Arqueiro | 6 |
| Fortaleza | Escudeiro + Brutamontes | 4 |
| Elite | Arauto + 2 básicos | 4 |

Nenhum inimigo ataca fora da câmera sem indicador de ameaça (CA-010).

## Chefes

| ID | Chefe | Tema | Mecânica central | Versão |
| --- | --- | --- | --- | --- |
| `boss_ignar` | Ignar | Fogo / terra | Resfriar armadura com água; quebrar com terra/pesado. | M2 |
| `boss_nerissa` | Nerissa | Água / gelo | Controlar áreas molhadas; evitar congelamento. | MVP |
| `boss_volkar` | Volkar | Vento / raio | Aterramento, mobilidade, ataques em cadeia. | MVP |
| `boss_guardiao` | Guardião Silvestre | Natureza / vento | Ainda sem mecânica no GDD — escrever ficha antes da arte. | 1.0 |
| `boss_seraph` | Seraph | Luz corrompida | Purificar clones; interromper rituais. | 1.0 |
| `boss_aethron` | Aethron | Eclipse | Rouba escolas, copia padrões, força reações. | 1.0 |

Chefes não usam agarrão comum. Imunidade a um status não apaga o feedback: converte para postura (CA-004).

## Ritual (RF-020)

Âncoras, ondas, contador, sucesso e falha. Usar em encontros da Ordem e no Templo. Fora do vertical slice, salvo um esboço no chefe Ignar se a fase pedir interrupção de canalização.
