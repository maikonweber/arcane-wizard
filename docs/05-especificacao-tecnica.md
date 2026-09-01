# Especificação técnica

Godot **4.7** / GDScript. Apresentação 2.5D: `CharacterBody3D`, profundidade restrita, câmera lateral. Hitbox e Hurtbox: `Area3D` com camadas de colisão definidas.

## Estrutura de pastas

```text
ArcaneWizard/
  assets/          # ver 03-mapa-de-assets.md
  docs/
  personagens/
  resources/
    abilities/
    attacks/
    schools/
    status/
    reactions/
    enemies/
    characters/
  scenes/
    main.tscn              # boot atual; vira roteador
    game_session.tscn
    levels/
    actors/
    ui/
  scripts/
    app/
    combat/
    magic/
    actors/
    ai/
    save/
    ui/
  tests/
```

## Cenas

`Main` → `GameSession` → `Level` → `Actors/Player`, `Actors/Enemies`, `EncounterDirector`, `CameraRig`, `NavigationRegion3D`, `UI`.

O stub atual (`scenes/main.tscn`) só mostra o título. Em M0 ele instancia `GameSession` com a arena de teste.

## Componentes

| Componente | Responsabilidade | Não deve fazer |
| --- | --- | --- |
| `PlayerController` | Entrada, intenção, ligação com a state machine. | Calcular dano ou aplicar status. |
| `CharacterStateMachine` | Estados, transições, cancelamentos, bloqueios. | Conhecer escolas pelo nome. |
| `CombatComponent` | Combos, hitboxes, hurtboxes, postura, agarrões. | Instanciar magias. |
| `MagicLoadout` | Slots, escola ativa, troca, mana, recargas. | Resolver reações. |
| `AbilityRunner` | Executa `AbilityData` e instancia a cena da habilidade. | Decidir dano final. |
| `StatusComponent` | Status, duração, intensidade, imunidades. | Procurar pares de reação. |
| `ReactionResolver` | Pares de tags → `ReactionData`. | Movimentar o ator. |
| `HealthComponent` | Vida, dano, cura, morte, sinais. | Salvar campanha. |
| `EnemyBrain` | Estados/árvore simples e navegação. | Dropar loot diretamente. |
| `SaveService` | Persistência versionada e checkpoints. | Renderizar UI. |
| `GameEvents` | Barramento tipado só do que precisa ser global. | Virar god-object. |

Estados do personagem: Idle, Move, Attack, Cast, Dodge, Hit, Knockdown, Grab, Airborne, Special, Dead, Interact. Troca de escola é camada paralela — não muda estado, salvo conjuração obrigatória.

## Resources

Magias, golpes, inimigos e reações **não** têm valores centrais no código (RNF-005).

| Resource | Conteúdo |
| --- | --- |
| `AbilityData` | `id`, `school`, `base_power`, `mana_cost`, `cooldown`, `cast_time`, `tags`, `status_payload`, `scene`, `cancel_window`, vfx/sfx. |
| `AttackData` | Dano, postura, impulso, hit-stop, cancelamentos. |
| `MagicSchoolData` | Identidade, afinidades, habilidades, HUD. |
| `StatusData` | Duração, pilhas, modificadores, VFX. |
| `ReactionData` | Tags exigidas, consumo, resultado, recarga por alvo. |
| `EnemyData` | Atributos, resistências, recompensas, IA. |
| `CharacterData` | Atributos-base, kit, animações, progressão. |

Ciclo de uma magia: entrada → dados (`AbilityData`) → `AbilityRunner` → colisão (`DamagePacket`) → `DamageSystem` + `StatusComponent` → `ReactionResolver` → VFX/SFX/câmera/UI.

## Fórmula de dano (ajustável)

`final = max(1, base_power × attack × combo_mul × elemental_mod × crit − defense)`

Resistência elemental recomendada: −50% a +80%.

## Sinais essenciais

`magic_changed(old_id, new_id)`, `ability_started(id)`, `hit_confirmed(packet)`, `status_applied(target, status)`, `reaction_triggered(target, reaction)`, `health_changed(current, max)`, `actor_defeated(actor)`, `encounter_completed(id)`, `checkpoint_reached(id)`.

## Persistência

Gravação atômica com cópia de segurança; schema versionado (RNF-011, RF-015). Save: campanha, melhorias, configurações, último checkpoint, loadout. Roundtrip obrigatório em M2 ([CA-007](09-requisitos.md)).

## Desempenho e entrada

- 60 FPS em 1080p no hardware-alvo; 30 FPS como modo alternativo (RNF-001).
- Feedback visual/mecânico em até 100 ms local (RNF-002); troca de escola no mesmo teto (CA-001).
- Fase jogável em até 10 s; troca de arena sem loading screen (RNF-003).
- Teclado/mouse e controle XInput no MVP (RNF-006).
- Textos fora das cenas, prontos para tradução (RNF-012).

## Métricas de teste inicial

- FPS com jogador + 10 inimigos + efeitos do MVP (CA-008).
- Latência entrada → aura na troca de escola.
- Tempo até o chefe da Vila das Cinzas.
- Reações disparadas vs. recarga por alvo (não deve ativar todo frame).
