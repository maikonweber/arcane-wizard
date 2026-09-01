# Backlog

Legenda: **P0** bloqueia M0/M1; **P1** entra no vertical slice (M2) e no MVP (M3); **P2** 1.0 ou pós-MVP.

| ID | Pri. | Item | Dependência | Critério de aceite |
| --- | --- | --- | --- | --- |
| AW-001 | P0 | Arena de teste + câmera 2.5D | — | Jogador anda no plano X/Z e permanece enquadrado. |
| AW-002 | P0 | Ataque leve e pesado com hit-stop | AW-001 | Combo de até 4 leves; pesado conecta; miss não conta (CA-005). |
| AW-003 | P0 | Hit reaction e vida | AW-002 | Dummy sofre hit visível e morre. |
| AW-004 | P0 | Esquiva com i-frames | AW-001 | Invulnerabilidade configurável; vigor consome. |
| AW-005 | P0 | Resources de golpe | AW-002 | Mudar `AttackData` altera dano sem recodar. |
| AW-006 | P1 | Loadout com 2 escolas (fogo, água) | AW-005 | Troca ≤ 100 ms; HUD e aura (CA-001). |
| AW-007 | P1 | Projétil Ígneo e Onda Cortante | AW-006 | Consomem mana; falha de recurso não trava. |
| AW-008 | P1 | Status Molhado e Queimadura | AW-007 | Aplicam, tictam/expiram. |
| AW-009 | P1 | Reação Vapor | AW-008 | Uma vez por janela no alvo (CA-003 adaptado). |
| AW-010 | P1 | Buffer de cancel 150 ms | AW-006 | CA-002. |
| AW-011 | P1 | Soldado, Arqueiro, Escudeiro | AW-003 | Três comportamentos distintos. |
| AW-012 | P1 | HUD combate | AW-006 | Vida, vigor, mana, slots, combo; ícones distintos em cinza (CA-009). |
| AW-013 | P1 | EncounterDirector na arena | AW-011 | Ondas com teto de atacantes. |
| AW-014 | P1 | Vila das Cinzas até Ignar | AW-009, AW-013 | Fase curta + chefe: água na armadura, pesado na quebra. |
| AW-015 | P1 | Save versionado + checkpoint | AW-014 | CA-007. |
| AW-016 | P1 | Áudio mínimo (música, hit, troca, magia) | AW-012 | Canais separados. |
| AW-017 | P1 | Tutorial dos seis verbos | AW-014 | RF-016 sem texto hardcoded na cena. |
| AW-018 | P1 | Terra e vento no loadout | AW-006 | Quatro escolas no MVP. |
| AW-019 | P1 | Cinco inimigos extras do MVP | AW-011 | 8 tipos no total. |
| AW-020 | P1 | Cidade Submersa + Nerissa | AW-018 | Fase completa com fragmento. |
| AW-021 | P1 | Fortaleza Rúnica + Volkar | AW-018 | Postura e defensores. |
| AW-022 | P1 | Progressão (essência, núcleos, árvore) | AW-015 | RF-013, RF-014. |
| AW-023 | P1 | Relíquias e atualização da Estrutura | AW-020 | RF-022. |
| AW-024 | P1 | Lyra IA | AW-014 | Acompanha e ataca; não bloqueia o jogador (RF-021). |
| AW-025 | P1 | Corrupção por faixa | AW-015 | RF-019. |
| AW-026 | P1 | Ritual (âncoras/ondas) | AW-013 | RF-020 num encontro. |
| AW-027 | P1 | Acessibilidade básica | AW-012 | Remap, volumes, reduzir tremor, formas sem cor (RF-017). |
| AW-028 | P1 | Alvo automático | AW-011 | RF-010. |
| AW-029 | P1 | Teste 60 FPS / 10 inimigos | AW-014 | CA-008. |
| AW-030 | P2 | Lyra e Doran jogáveis | AW-022 | Kits do GDD §5. |
| AW-031 | P2 | Quatro escolas restantes | AW-018 | 8 escolas, matriz de reações completa. |
| AW-032 | P2 | Floresta + Templo | AW-021 | Duas fases 1.0. |
| AW-033 | P2 | Seraph e Aethron | AW-032 | Chefes 1.0. |
| AW-034 | P2 | Cooperativo local | AW-014 | RF-018, só após M2. |
| AW-035 | P2 | Mímico, Arauto e regionais | AW-019 | 12 inimigos. |
