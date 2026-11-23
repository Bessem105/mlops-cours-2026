# Journal de bord du binôme

<!--
Mode d'emploi (à garder en tête du fichier) :
- Une entrée par séance (et par session de travail importante hors séance), la plus récente en bas.
- 3 à 5 lignes : qui a piloté, ce qui a été fait, ce qui a bloqué ou ce qui a été appris,
  la prochaine étape. Pas de roman : c'est un outil de pilotage, pas un rapport.
- Titre d'entrée au format exact « ## S<n> — AAAA-MM-JJ — <sujet> » (date réelle) :
  le pré-contrôle de rendu (make check-m10) compte les entrées datées.
- Liez les PR, issues et ADR (#12, docs/adr/0003-...). Les problèmes non résolus restent
  visibles : c'est précisément ce qui aide l'enseignant à vous débloquer.
- L'entrée d'exemple ci-dessous (date AAAA-MM-JJ) n'est pas comptée ; supprimez-la
  quand vous aurez écrit la vôtre.
-->

**Binôme :** @Bessem105 (Bessem Jennen), travail en solo
**Repo :** https://github.com/Bessem105/mlops-cours-2026
**Dataset :** german-credit (fil rouge)
**Extensions :** [À compléter à la S8 : @Bessem105 → ext/<nom>]

<!-- Vos entrées commencent ici. Modèle :

## S1 — AAAA-MM-JJ — Lab 0 : setup

- **Pilote / copilote :**
- **Fait :**
- **Bloqué / appris :**
- **Prochaine étape :**

-->

## S2 — 2026-11-23 — Lab 1 : versionner un projet ML

- **Pilote / copilote :** @Bessem105 / seul, sans binôme
- **Fait :** Lab 1 complet, `make check-m1` à 18/18. Pipeline DVC `download -> prepare -> train -> evaluate`, 22 runs MLflow (3 types de modèles), registry `scoring-model` (versions 1 à 3, `@champion` et `@challenger`), feature store Feast (`request_features`, `scoring_v1`). PR `lab/m1` ouverte.
- **Bloqué / appris :** le chargement du `@champion` depuis MLflow restait bloqué : l'URL S3 signée pointait vers `s3.storage:8333`, introuvable depuis WSL. Corrigé en ajoutant `127.0.0.1 s3.storage` dans `/etc/hosts` (le port-forward S3 reste nécessaire). Le port 5000 était aussi occupé par un conteneur `elk-logstash` d'un autre cours, arrêté. Le seuil de décision est coût-optimal (0.318 avec `class_weight: balanced`, coût 108).
- **Prochaine étape :** fusionner la PR après relecture du binôme, puis Lab 2 (pipeline Kubeflow + Airflow).
