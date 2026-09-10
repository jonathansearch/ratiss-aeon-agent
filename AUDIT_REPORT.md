# Local Audit Report — ratiss-aeon-agent

> Scope: local clone only. No remote repository was modified and no push was performed.

## Repository Structure

| Check | Result |
|---|---|
| Tracked/local file count | 229 |
| Python file count | 69 |
| README | PASS |
| RATISS Labs logo (`docs/assets/logo.png`) | PASS |
| Apache 2.0 LICENSE | PASS |
| `CITATION.cff` | PASS |

## Test Validation

- Command: `python3 -m pytest -v`
- Exit status: `2`

```text
    os.mkdir(self, mode)
E   FileNotFoundError: [Errno 2] No such file or directory: '/app/workspace'

During handling of the above exception, another exception occurred:
proofs/agent_agentic_test.py:87: in <module>
    ws.mkdir(parents=True, exist_ok=True)
/usr/lib/python3.12/pathlib.py:1317: in mkdir
    self.parent.mkdir(parents=True, exist_ok=True)
/usr/lib/python3.12/pathlib.py:1317: in mkdir
    self.parent.mkdir(parents=True, exist_ok=True)
/usr/lib/python3.12/pathlib.py:1313: in mkdir
    os.mkdir(self, mode)
E   PermissionError: [Errno 13] Permission denied: '/app'
------------------------------- Captured stdout --------------------------------
========================================================================
TEST AGENTIQUE COMPLET RATISS v9.4 — LLM réel OpenRouter
========================================================================

[0] Fournisseurs LLM configurés :
    anthropic    --  (AnthropicProvider)
    google       --  (GeminiProvider)
    openai       OK  (OpenAIProvider)
    openrouter   --  (OpenRouterProvider)

[1] Test identité souveraine (vrai LLM OpenRouter)...
    Réponse LLM : Je suis Ratiss. J'ai bien reçu ta demande : « Réponds en une phrase : qui es-tu et quel est ton nom ? ». Pour l'instant je tourne en mode souverain local. Branche une clé API (Anthropic, Gemini, OpenAI ou OpenRouter) via l'onglet Modèles po
    -> Identité souveraine OK (Ratiss s'identifie, pas Nemotron)

[2] Planification de la tâche par le LLM...
    Tâche : Analyse scientifique de la protéine p53-MDM2 (PDB 4MZI). Étapes demandées : (1) charger la structure PDB 4MZI, (2) calcu...
    Planificateur : local_heuristic (0.0s)
    Étapes LLM    : 6
      - load_pdb : Charger la structure 4MZI
      - topology : Homologie persistante (Betti)
      - generate_pdf : Génération du rapport PDF
      - generate_chart : Génération d'un graphique
      - generate_betti_diagram : Diagramme de persistance
      - python_execute : Python: exécuter du code
    Domaine : topology

[3] Exécution ReAct de l'agent Ratiss...
    Étapes exécutées : 6 (succès : 6)
    Temps total : 4.6s
    Workspace : workspace/582264e5af38

[4] Téléchargement PDB réel 4MZI depuis RCSB...
------------------------------- Captured stderr --------------------------------
[RATISS-QUANTUM-SOLVER] 2026-09-10 03:57:02,551 - [LLM] Échec openrouter/nvidia/nemotron-3-ultra-550b-a55b:free (OPENROUTER_API_KEY non configurée), essai suivant.
[RATISS-QUANTUM-SOLVER] 2026-09-10 03:57:02,552 - [LLM] Échec openrouter/google/gemma-4-26b-a4b-it:free (OPENROUTER_API_KEY non configurée), essai suivant.
[RATISS-QUANTUM-SOLVER] 2026-09-10 03:57:02,552 - [LLM] Échec openrouter/nvidia/nemotron-3-super-120b-a12b:free (OPENROUTER_API_KEY non configurée), essai suivant.
[RATISS-QUANTUM-SOLVER] 2026-09-10 03:57:02,552 - [LLM] Échec openrouter/openai/gpt-oss-20b:free (OPENROUTER_API_KEY non configurée), essai suivant.
[RATISS-QUANTUM-SOLVER] 2026-09-10 03:57:02,552 - [LLM] Échec openrouter/nvidia/nemotron-nano-9b-v2:free (OPENROUTER_API_KEY non configurée), essai suivant.
[RATISS-QUANTUM-SOLVER] 2026-09-10 03:57:02,552 - [LLM] Tous les modèles openrouter ont échoué, fallback local.
[RATISS-QUANTUM-SOLVER] 2026-09-10 03:57:02,552 - [LLM] openrouter non configuré, plan local.
[RATISS-QUANTUM-SOLVER] 2026-09-10 03:57:03,973 - Pass: UnrollCustomDefinitions - 0.18048 (ms)
[RATISS-QUANTUM-SOLVER] 2026-09-10 03:57:03,973 - Pass: BasisTranslator - 0.02694 (ms)
[RATISS-QUANTUM-SOLVER] 2026-09-10 03:57:04,588 - Executing solve_persistent_homology [Initial RAM: 188.07 MB / Limit: 7500 MB]
[RATISS-QUANTUM-SOLVER] 2026-09-10 03:57:04,588 - [TOPO-SOLVER] Calcul de l'homologie (Dim Max = 2) sur 500 points repères...
[RATISS-QUANTUM-SOLVER] 2026-09-10 03:57:04,588 - [TOPO-SOLVER] GUDHI non disponible. Utilisation du résolveur natif RATISS (Fallback CPU-light).
[RATISS-QUANTUM-SOLVER] 2026-09-10 03:57:04,773 - [TOPO-SOLVER] Succès Résolveur Natif. Nombres de Betti estimés: [1, 2, 0]
[RATISS-QUANTUM-SOLVER] 2026-09-10 03:57:04,834 - Completed solve_persistent_homology [Final RAM: 203.82 MB]
[RATISS-QUANTUM-SOLVER] 2026-09-10 03:57:05,102 - [SKILL] Erreur sur generate_pdf
Traceback (most recent call last):
  File "/home/ubuntu/ratiss-labs-repos/ratiss-aeon-agent/orchestrator/skill_manager.py", line 490, in execute_step
    return fn(params, ctx)
           ^^^^^^^^^^^^^^^
  File "/home/ubuntu/ratiss-labs-repos/ratiss-aeon-agent/orchestrator/skill_manager.py", line 164, in _generate_pdf
    return generate_pdf(params.get("title", "Rapport"), params.get("sections", []), output_dir=workspace)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/ubuntu/ratiss-labs-repos/ratiss-aeon-agent/tools/content_generator.py", line 262, in generate_pdf
    pdf.cell(0, 12, "RATISS Aeon Prime", new_x="LMARGIN", new_y="NEXT", align="L")
  File "/usr/local/lib/python3.12/dist-packages/fpdf/fpdf.py", line 150, in wrapper
    return fn(self, *args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^
TypeError: FPDF.cell() got an unexpected keyword argument 'new_x'
[RATISS-QUANTUM-SOLVER] 2026-09-10 03:57:07,152 - [AGENT] Rapport enrichi echoue: FPDF.cell() got an unexpected keyword argument 'new_x'
=========================== short test summary info ============================
ERROR proofs/agent_agentic_test.py - PermissionError: [Errno 13] Permission d...
!!!!!!!!!!!!!!!!!!!! Interrupted: 1 error during collection !!!!!!!!!!!!!!!!!!!!
=============================== 1 error in 5.64s ===============================

```

## Compliance Notes

- Branding and common repository metadata were applied locally.
- Scientific claims were not upgraded from proxy evidence to full validation.
- The three required technical Bible documents were not present in the supplied workspace.
- This report is an engineering audit snapshot, not a claim of zero defects.
