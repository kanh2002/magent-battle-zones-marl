# MAgent Battle-Zones — Subtask A

## Resources

| Resource | Link |
|---|---|
| Value-based notebook (VDN starter) | **https://www.kaggle.com/code/kimanh2002/value-based-baseline** |
| Policy-based notebook (MAPPO starter) | **https://www.kaggle.com/code/kimanh2002/policy-based-baseline** |
| Battle-Zones environment / dataset | **https://www.kaggle.com/datasets/kimanh2002/battle-zones/data** |
| Staff Base Policy (`base_policy_hard.pt`) | **https://www.kaggle.com/models/kimanh2002/base-policy/** |

## What you must do

1. **Implement two MARL algorithm families:** at least one **value-based** algorithm (e.g., VDN, QMIX, QTRAN, QPLEX) and one **policy-based** algorithm (e.g., MAPPO, HAPPO, MADDPG, COMA). The linked VDN/MAPPO notebooks are editable starting points, not mandatory algorithm choices.
2. **Train on both Easy and Hard:** produce a separate policy for each setting and for each algorithm (**four exported policies** in total).
3. **Respect the compute budget:** at most **60 minutes of total training for Easy + Hard per notebook** on a Kaggle GPU. Enforce the limit with a wall-clock check. Evaluation time is excluded.
4. **Run all official evaluations** using the original evaluation functions and seeds:

   | Train → Evaluate | Opponents | Episodes per opponent |
   |---|---|---:|
   | Easy → Easy | Random, Staff Base Policy | 20 |
   | Hard → Hard | Random, Staff Base Policy | 50 |
   | Easy → Hard (transfer) | Random, Staff Base Policy | 50 |

   **Easy → Hard uses the Easy-trained policy without additional training.** This is **240 evaluation episodes per algorithm** (480 for two algorithms). Report win/draw/loss, kill %, death %, and K/D for every required case.
5. **Export compatible TorchScript models:** `float32 (N, 13, 13, 7) → (N, 21)` action logits. The executed policy must use only permitted local observations; global state may be used during training.

## Implementation boundaries

- **You may change:** the learning algorithm within the required family, network, loss/optimization, exploration, experience collection, reward shaping for training, training opponents, curriculum, and hyperparameters.
- **You must not change:** environment dynamics, execution-time observations, official `run_episode()`/`evaluate()` functions, evaluation seeds, or metric definitions.
- **Pretrained weights:** weights from outside the notebook are prohibited **except the provided Base Policy**, which may be used as an opponent or for initialization.

## Subtask A submission — 8 Dec 2026

**Submit both the saved Kaggle version links and the required output files.** For each notebook, select **Save Version → Save & Run All (Commit)**, wait until the run finishes successfully, and verify that the training/evaluation outputs and exported models are present. **Quick Save or a draft link alone is not accepted.**

Provide **direct links to the specific submitted versions** of both Kaggle notebooks.

```text
Kaggle link: A_value_based       # Specific completed Save & Run All version
Kaggle link: A_policy_based      # Specific completed Save & Run All version
<value_algo>_easy.pt
<value_algo>_hard.pt
<policy_algo>_easy.pt
<policy_algo>_hard.pt
results_A.json                  # All official results for BOTH algorithms
Nominated policy for Subtask B  # State exact algorithm + exported file
```

Both saved notebook versions must run **top to bottom on Kaggle** with their declared dependencies and fixed seeds, and must show configurations, training logs, **wall-clock training time for Easy, Hard, and the combined total**, official evaluations, and output files. The combined training time must be **≤60 minutes per notebook**.

**Code freeze:** The submitted Kaggle versions and exported models are fixed at the Subtask A deadline. Later edits/versions do not replace the submission. Staff may download and rerun the exact submitted code, verify outputs and training time, and compare model files with the recorded results.

## Final report — 16 Dec 2026

Submit a **PDF report (maximum 8 pages, excluding references and appendix)**. Include:

- Names, student IDs, individual contributions, and links to the Kaggle notebooks.
- Algorithm descriptions, design choices, training results/curves, **all Subtask A evaluations**, and analysis of Easy vs Hard and Easy → Hard transfer.
- Experimental comparisons or ablations, limitations, and **Subtask B results/discussion**.
- Citations for external sources/code

## Academic integrity
- Training: Do not bypass the 60-minute training limit through external training, hidden sessions, or undeclared checkpoints. Training must be reproducible from the submitted notebooks.

- Evaluation: Do not modify official evaluation code, seeds, episode counts, or metrics. Do not falsify logs, results, or model files.

- Verification: Instructors may inspect notebook version history, rerun experiments, and investigate inconsistencies.