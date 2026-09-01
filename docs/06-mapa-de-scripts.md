# Mapa de scripts

Godot 4.x / GDScript. Começar pelos P0. Caminhos propostos.

## Dependências

```text
Resources (Ability, School, Status, Reaction, Enemy, Character)
        │
 PlayerController ── CharacterStateMachine ── CombatComponent
        │                                          │
 MagicLoadout ── AbilityRunner ── Hitbox/Hurtbox ── DamageSystem
        │                              │
        │                         StatusComponent ── ReactionResolver
        │
 HealthComponent
        │
 EncounterDirector ── EnemyBrain
        │
 GameSession ── SaveService
        │
 HUD / UI ── GameEvents
```

## P0 — prova de combate (M0)

| Arquivo | Classe | Responsabilidade | Depende de | Aceite |
| --- | --- | --- | --- | --- |
| `scripts/app/game_session.gd` | `GameSession` | Instancia nível, jogador, câmera. | — | Arena abre a partir de Main. |
| `scripts/actors/player_controller.gd` | `PlayerController` | WASD/analógico, intenção de ataque e esquiva. | State machine | Move em X/Z; respeita limites. |
| `scripts/combat/character_state_machine.gd` | `CharacterStateMachine` | Estados e transições. | — | Idle→Move→Attack→Idle. |
| `scripts/combat/combat_component.gd` | `CombatComponent` | Leve (até 4 hits), pesado, hit-stop. | `AttackData` | Combo conecta; miss não conta (CA-005). |
| `scripts/combat/health_component.gd` | `HealthComponent` | Vida, hit reaction, morte. | — | Hit visível; morte encerra controle. |
| `scripts/combat/hitbox.gd` | `Hitbox` | Envia `DamagePacket`. | camadas | Só acerta Hurtbox. |
| `scripts/combat/hurtbox.gd` | `Hurtbox` | Recebe pacote. | `HealthComponent` | I-frames da esquiva ignoram. |
| `scripts/camera/camera_rig.gd` | `CameraRig` | Lateral, limites de arena. | — | Jogador permanece enquadrado. |
| `scripts/data/attack_data.gd` | `AttackData` | Resource de golpe. | — | Mudar power no inspector muda o dano. |

## P1 — magia, troca, reação (M1)

| Arquivo | Classe | Responsabilidade | Depende de | Aceite |
| --- | --- | --- | --- | --- |
| `scripts/data/ability_data.gd` | `AbilityData` | Resource da habilidade. | — | CA-006. |
| `scripts/data/magic_school_data.gd` | `MagicSchoolData` | Escola, HUD, habilidades. | `AbilityData` | Dois schools carregam. |
| `scripts/data/status_data.gd` | `StatusData` | Status persistente. | — | Molhado aplica e expira. |
| `scripts/data/reaction_data.gd` | `ReactionData` | Par de tags. | `StatusData` | Um par por resource. |
| `scripts/magic/magic_loadout.gd` | `MagicLoadout` | 4 slots, escola ativa, mana, troca ≤100 ms. | schools | CA-001, CA-002. |
| `scripts/magic/ability_runner.gd` | `AbilityRunner` | Instancia cena da magia. | `AbilityData` | Sem mana: não inicia, feedback, estado livre. |
| `scripts/magic/status_component.gd` | `StatusComponent` | Pilhas, duração, imunidades. | `StatusData` | Queimadura tica e some. |
| `scripts/magic/reaction_resolver.gd` | `ReactionResolver` | Uma reação por janela/alvo. | `ReactionData` | CA-003. |
| `scripts/magic/damage_system.gd` | `DamageSystem` | Fórmula de dano. | packet | Resistência altera número. |
| `scripts/ui/hud.gd` | `CombatHud` | Vida, mana, slots, combo, reação. | sinais | Escola ativa identificável em cinza. |
| `scripts/ai/enemy_brain.gd` | `EnemyBrain` | Patrulha, perseguir, atacar. | `EnemyData` | 3 inimigos distintos. |
| `scripts/data/enemy_data.gd` | `EnemyData` | Atributos e resistências. | — | Resource por tipo. |

## P2 — slice, save, encontro (M2+)

| Arquivo | Classe | Responsabilidade | Depende de |
| --- | --- | --- | --- |
| `scripts/levels/encounter_director.gd` | `EncounterDirector` | Ondas, limite ativo, spawn, pausa. | `EnemyData` |
| `scripts/save/save_service.gd` | `SaveService` | Save atômico, versão, checkpoint. | `GameSession` |
| `scripts/app/game_events.gd` | `GameEvents` | Autoload de sinais globais mínimos. | — |
| `scripts/data/character_data.gd` | `CharacterData` | Kit e atributos de Kael. | schools |
| `scripts/progression/essence_service.gd` | `EssenceService` | Essência, núcleos, árvore. | `SaveService` |
| `scripts/actors/partner_ai.gd` | `PartnerAI` | Lyra acompanha e ataca. | `EnemyBrain` (não copiar jogador) |
| `scripts/levels/corruption_meter.gd` | `CorruptionMeter` | Faixas de corrupção (RF-019). | `SaveService` |
| `scripts/levels/ritual_controller.gd` | `RitualController` | Âncoras, ondas, sucesso/falha (RF-020). | `EncounterDirector` |
| `scripts/ui/pause_menu.gd` | `PauseMenu` | Remap, volumes, tremor. | `SaveService` |

## Ordem de criação

1. `GameSession`, câmera, `PlayerController`, state machine.
2. `AttackData`, Hitbox/Hurtbox, `CombatComponent`, `HealthComponent`.
3. Dummy inimigo que anda e morre.
4. `MagicSchoolData`, `MagicLoadout`, troca + HUD.
5. `AbilityRunner` fogo e água.
6. `StatusComponent` + `ReactionResolver` (uma reação).
7. Três `EnemyData` + `EnemyBrain`.
8. `EncounterDirector` + Vila das Cinzas + Ignar.
9. `SaveService` e pause.
10. Progressão, Lyra IA, rituais — depois do slice.

## Autoloads

| Script | Autoload? | Motivo |
| --- | --- | --- |
| `GameEvents` | Sim | Sinais entre combate, HUD e save. |
| `SaveService` | Sim | Única fonte de persistência. |
| `GameSession` | Não | Vive na cena da sessão. |
| `MagicLoadout` | Não | Componente do jogador. |
| `ReactionResolver` | Não | Pode ser nó da sessão ou componente do alvo. |
