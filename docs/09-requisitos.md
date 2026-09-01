# Requisitos e aceite

Fonte: GDD seções 3, 4 e 14. IDs estáveis.

## Funcionais

| ID | Sistema | Requisito | Prioridade |
| --- | --- | --- | --- |
| RF-001 | Movimentação | Oito direções no plano 2.5D, corrida, limites de navegação. | Obrigatório |
| RF-002 | Ataque | Leve, pesado, aéreo, agarrão, finalização. | Obrigatório |
| RF-003 | Combo | Encadear em janelas configuráveis; zerar após expirar. | Obrigatório |
| RF-004 | Esquiva | Duração e i-frames configuráveis. | Obrigatório |
| RF-005 | Magia | Conjurar a escola ativa consumindo mana ou carga. | Obrigatório |
| RF-006 | Troca | Alternar até quatro escolas sem pausar a cena. | Obrigatório |
| RF-007 | Cancelamento | Trocar magia em pontos definidos de ataques físicos e mágicos. | Obrigatório |
| RF-008 | Status | Queimadura, molhado, congelamento, choque, vulnerabilidade, corrupção. | Obrigatório |
| RF-009 | Reação | Combinar status; executar o efeito uma vez por janela. | Obrigatório |
| RF-010 | Alvo | Seleção automática por distância, direção e ameaça. | Obrigatório |
| RF-011 | Dano | Poder, multiplicador, defesa, resistência, crítico, dificuldade. | Obrigatório |
| RF-012 | IA | Patrulhar, perseguir, atacar, defender, recuar, reagir a controle. | Obrigatório |
| RF-013 | Progressão | Essência e técnicas permanentes. | MVP |
| RF-014 | Equipamento | Quatro magias e modificadores em pontos seguros. | MVP |
| RF-015 | Salvamento | Campanha, melhorias, opções, último checkpoint. | MVP |
| RF-016 | Tutorial | Movimento, ataque, esquiva, magia, troca, primeira reação. | MVP |
| RF-017 | Acessibilidade | Remap, vibração, tremor, legendas, diferenciação sem cor. | MVP |
| RF-018 | Cooperativo | Dois jogadores locais; reações conjuntas. | Pós-MVP |
| RF-019 | Corrupção | Aumentar/reduzir e efeitos por faixa. | MVP |
| RF-020 | Ritual | Âncoras, ondas, contador, sucesso e falha. | MVP |
| RF-021 | Parceiro IA | Lyra acompanha, combate e comandos simples. | MVP |
| RF-022 | Relíquias | Selos recuperados atualizam poderes, campanha e Estrutura. | MVP |

Aéreo, agarrão e finalização (RF-002) podem ser stub em M0 (só leve e pesado) e completar até M2.

## Não funcionais

| ID | Categoria | Critério |
| --- | --- | --- |
| RNF-001 | Desempenho | 60 FPS em 1080p no alvo; 30 FPS alternativo. |
| RNF-002 | Entrada | Resposta ≤ 100 ms em execução local. |
| RNF-003 | Carregamento | Fase jogável ≤ 10 s; arena sem tela de carga. |
| RNF-004 | Estabilidade | Nenhum erro bloqueador em 60 min contínuos. |
| RNF-005 | Dados | Magias, golpes, inimigos, reações em Resources. |
| RNF-006 | Compatibilidade | Teclado/mouse e XInput. |
| RNF-007 | Resolução | UI de 1280×720 a 3840×2160, várias proporções. |
| RNF-008 | Áudio | Música, efeitos, voz e master separados. |
| RNF-009 | Acessibilidade | Elemento não depende só de cor. |
| RNF-010 | Manutenção | Dano, status e habilidades desacoplados (componentes + sinais). |
| RNF-011 | Save | Gravação atômica, backup, dados versionados. |
| RNF-012 | Localização | Textos fora das cenas. |

## Critérios de aceitação

| ID | Critério |
| --- | --- |
| CA-001 | Slot válido: aura e HUD mudam; próxima magia usa a nova escola em ≤ 100 ms. |
| CA-002 | Troca fora da janela de cancel fica em buffer ≤ 150 ms e executa na primeira janela. |
| CA-003 | Água aplica Molhado; Raio em Molhado ativa Eletrocussão uma vez e propaga a alvos válidos. |
| CA-004 | Chefe imune a congelamento recebe dano de postura equivalente, com feedback. |
| CA-005 | Combo só sobe no hit; encerra após a janela. |
| CA-006 | Alterar Resource da habilidade reflete no jogo sem editar o controlador. |
| CA-007 | Save/load restaura fase, checkpoint, progressão, loadout e opções. |
| CA-008 | 60 FPS no cenário de teste: jogador, 10 inimigos, efeitos do MVP. |
| CA-009 | Toda escola tem ícone e forma distintos; identificável em escala de cinza. |
| CA-010 | Nenhum inimigo ataca fora da câmera sem indicador de ameaça. |

CA-003 no M1 pode usar Vapor no lugar de Eletrocussão se Raio ainda não existir. O critério de reação “uma vez por janela” permanece.

## Casos de teste prioritários

| Caso | Preparação | Resultado |
| --- | --- | --- |
| Troca durante combo | L-L e trocar para fogo. | Troca na janela; terceiro golpe com afinidade. |
| Reação repetida | Alvo molhado + vários raios (ou fogos). | Recarga impede várias ativações no mesmo instante. |
| Mana insuficiente | Técnica sem mana. | Não inicia; feedback; estado não trava. |
| Alvo morre com status | Queimadura letal. | Crédito e recompensa no responsável. |
| Pausa durante magia | Pausar com projétil ativo. | Simulação e timers relevantes param. |
