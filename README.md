# Prédiction des débits des rivières bretonnes par machine learning

Projet de recherche de la spécialité MCE (Mathematical and Computational Engineering), IMT Atlantique, en collaboration avec le RIKEN (Japon).

> **Statut : en cours.** Le projet en est à la phase de prise en main des outils. Aucun résultat sur la Bretagne n'est encore disponible.

## Contexte

Les régimes hydrologiques des bassins versants bretons évoluent, avec des risques accrus de crues et de sécheresses d'ici 2100. Les modèles d'IA permettent de représenter les relations complexes entre précipitations et débits, sans la lourdeur des modèles physiques classiques.

## Objectifs

- Prédire l'évolution des débits des rivières bretonnes jusqu'en 2100, selon plusieurs scénarios climatiques.
- Adapter et évaluer des architectures d'IA développées au RIKEN sur des problématiques hydrologiques régionales.

## Approche

Le modèle du RIKEN combine deux briques entraînées ensemble :

1. **Génération de ruissellement** : un réseau LSTM estime l'eau envoyée à la rivière par chaque sous-bassin à partir des données météo.
2. **Routage** : l'eau circule dans le réseau de rivières (DiffRoute). Le routage linéaire est écrit comme une convolution, `Q = conv(R, K)`, ce qui le rend rapide sur GPU et différentiable.

Référence principale : Hascoet, T., Pellet, V., Oishi, S., & Miyoshi, T. (2026). *Differentiable river routing for end-to-end learning of hydrological processes.* JGR: Machine Learning and Computation, 3, e2025JH000760. https://doi.org/10.1029/2025JH000760

## Outils

| Outil | Rôle |
|---|---|
| [DiffRoute](https://github.com/TristHas/DiffRoute) | Routage différentiable sur réseau de rivières |
| [DiffHydro](https://github.com/TristHas/DiffHydro) | Pipelines hydrologiques différentiables |
| [ba_school_handson](https://github.com/TristHas/ba_school_handson) | TP de prise en main (LSTM sur un bassin japonais) |
| [NeuralHydrology](https://neuralhydrology.github.io/) | Bibliothèque et ressources sur l'IA en hydrologie |

## Données

- **Débits historiques** : HydroPortail
- **Météo historique** : ERA5
- **Projections climatiques** : CMIP6

## Travail prévu

1. Traiter, harmoniser et formater les données CMIP6, de débit et de météo.
2. Calibrer les modèles du RIKEN sur les bassins bretons.
3. Exécuter les simulations prospectives jusqu'en 2100.

## Difficultés identifiées

- Entrées différentes de celles de l'article (grilles, pas de temps, stations à harmoniser).
- Construction du graphe en arbre du réseau de rivières breton.
- Ré-entraînement nécessaire sur des bassins bretons.
- Risque de non-généralisation d'une relation apprise sur un bassin à un bassin très différent.
- Modèle linéaire : pas de barrages ni de plaines d'inondation.
- Passage du passé à 2100 : harmonisation CMIP6/ERA5 et validation du modèle en climat futur.

## Structure du dépôt

```
[à compléter selon votre organisation, par exemple :]
data/        données brutes et traitées (hors Git si volumineuses)
notebooks/   exploration et prise en main
src/         scripts de préparation et d'entraînement
docs/        notes et présentation
```

## Encadrement

- Tuteur école : Pierre Tandeo (IMT Atlantique)
- Partenaire : Tristan Hascoet (RIKEN)

## Auteurs

[Noms des membres du groupe]
