# Real Madrid — Performance Analysis 2024/2025
## Documentation des KPI, des calculs et des observations

Source : Football-Data.co.uk (LaLiga 2024/2025), 38 matchs du Real Madrid (19 à domicile, 19 à l'extérieur).
Tous les chiffres ci-dessous ont été recalculés indépendamment depuis `Liga_2024_2025.csv` (pandas) et comparés aux formules DAX du modèle.

## 1. Colonnes calculées (modèle existant, inchangé)

| Colonne | Logique |
|---|---|
| Lieu du match | « Domicile » si HomeTeam = Real Madrid, sinon « Extérieur » |
| Buts par match / Encaissés par match | FTHG ou FTAG selon le côté du Real |
| Tirs par match / Tirs cadrés par match | HS, HST ou AS, AST selon le côté du Real |
| Tirs subis par match / Tirs cadrés subis | HS, HST ou AS, AST du côté adverse |

## 2. Mesures utilisées dans le rapport

| Mesure | Définition | Valeur |
|---|---|---|
| Nombre de matchs | COUNTROWS | 38 |
| Victoires | Matchs gagnés (H à domicile, A à l'extérieur) | 26 |
| Matchs nuls | FTR = "D" | 6 |
| Défaites | Matchs − Victoires − Nuls | 6 |
| Buts marqués | Somme des buts du Real | 78 |
| Buts encaissés | Somme des buts adverses | 38 |
| Taux de conversion | Σ buts / Σ tirs | 12,32 % |
| Matchs sans encaisser | Matchs où Encaissés par match = 0 | 15 |
| Moyenne tirs subis | AVERAGE(Tirs subis par match) | 10,63 |
| Moyenne tirs cadrés subis | AVERAGE(Tirs cadrés subis) | 3,47 |

Agrégations directes sur colonnes (dans les visuels) : moyenne de « Buts par match » (2,05), moyenne de « Tirs par match », moyennes par lieu (domicile / extérieur).
Les graphiques « par lieu » utilisent le contexte de filtre de la colonne « Lieu du match » (pas de mesure à filtre figé), donc chaque barre est bien calculée sur son propre périmètre.

## 3. Valeurs par lieu (vérifiées)

| | Domicile | Extérieur |
|---|---|---|
| Buts marqués | 45 | 33 |
| Moyenne de buts marqués | 2,37 | 1,74 |
| Buts encaissés | 19 | 19 |
| Moyenne de buts encaissés | 1,00 | 1,00 |
| Tirs par match | 19,21 | 14,11 |
| Tirs cadrés par match | 7,68 | 5,47 |
| Taux de tirs cadrés | 40,00 % | 38,81 % |
| Taux de conversion | 12,33 % | 12,31 % |
| Tirs subis par match | 9,42 | 11,84 |
| Tirs cadrés subis par match | 2,79 | 4,16 |
| Bilan V / N / D | 16 / 1 / 2 | 10 / 5 / 4 |
| Matchs sans encaisser | 8 | 7 |

## 4. Écarts avec le brief initial

Deux valeurs du brief ne correspondent pas aux données :
- Moyenne de buts à domicile : 45 / 19 = **2,37** (brief : 2,39).
- Moyenne de buts à l'extérieur : 33 / 19 = **1,74** (brief : 1,47, probablement deux chiffres inversés).

Le rapport affiche les valeurs calculées (2,37 et 1,74). Toutes les autres statistiques du brief sont confirmées.

## 5. Principales observations

1. **Saison solide** : 26 victoires sur 38 (68,42 %), 78 buts marqués pour 38 encaissés, soit un écart de +40.
2. **Écart domicile / extérieur offensif** : 2,37 buts par match à domicile contre 1,74 à l'extérieur, avec 19,21 tirs contre 14,11. Le Real tire nettement moins en déplacement.
3. **Efficacité identique** : la conversion est quasi égale (12,33 % contre 12,31 %). La différence de buts vient du volume de tirs, pas de la finition.
4. **Défense stable en buts, pas en tirs** : 19 buts encaissés dans chaque lieu, mais 11,84 tirs subis (4,16 cadrés) à l'extérieur contre 9,42 (2,79 cadrés) à domicile.
5. **Solidité** : 15 matchs sans encaisser (8 à domicile, 7 à l'extérieur) ; le Real n'a pas marqué lors de 2 matchs seulement.
6. **Résultats** : à domicile 16 victoires, 1 nul, 2 défaites ; à l'extérieur 10 victoires, 5 nuls, 4 défaites. Les points perdus se concentrent en déplacement.

## 6. Benchmark LaLiga

Table `LaLiga_Equipes` : une ligne par équipe et par match (760 lignes), construite dans Power Query à partir des 380 matchs du championnat ; elle n'a aucune relation avec la table du Real.
Les mesures LaLiga lisent le lieu du match sélectionné dans le rapport (domicile, extérieur ou les deux) ; le filtre de dates ne s'y applique pas.

| Indicateur | Real Madrid | Moyenne LaLiga |
|---|---|---|
| Buts par match | 2,05 | 1,31 (domicile 1,45, extérieur 1,17) |
| Tirs par match | 16,66 | 11,85 |
| Taux de conversion | 12,32 % | 11,05 % |
| Points | 84 (2e) | Barcelone 88, Atlético 76 |

Le Real n'a ni la meilleure attaque (Barcelone : 102 buts contre 78) ni la meilleure défense (Ath Bilbao : 29 buts encaissés, Real : 38). Il encaisse toutefois 1,00 but par match contre 1,31 en moyenne.
La moyenne de buts encaissés de la ligue est égale à celle de buts marqués, puisque chaque but compte dans les deux sens.

## 7. Limites

Analyse descriptive sur une seule saison, sans indicateurs de qualité d'occasion (xG). Le benchmark compare le Real à la moyenne de la ligue, sans pondérer par le niveau des adversaires.
