---
title: Equation-Sie Prospection Géolocalisée
emoji: 📍
colorFrom: indigo
colorTo: purple
sdk: streamlit
sdk_version: 1.39.0
app_file: app.py
pinned: false
license: other
short_description: Outil interne Equation-Sie de prospection géolocalisée
---

# 📍 Equation-Sie — Outil de prospection géolocalisée

Croise la base Pipedrive (organisations + contacts) avec une adresse pivot et un rayon,
pour sortir les sociétés et contacts dans la zone autour.

## 🎯 Fonctionnement

1. **Import** des fichiers Pipedrive (organisations + contacts) via l'onglet Admin
2. **Géocodage automatique** des adresses via l'API officielle Base Adresse Nationale
3. **Recherche** par adresse pivot + rayon (carte interactive + export Excel)
4. **Historique** des 20 dernières recherches, rejouables en un clic

## 🔐 Confidentialité

Ce Space contient des données sensibles (Pipedrive). **Il doit être configuré en
visibilité privée** dans les paramètres du Space.

## ⚙️ Configuration

Dans les *Settings* du Space, ajouter un secret :
- `ADMIN_PASSWORD` : le mot de passe d'accès à l'onglet Admin

Par défaut (à changer impérativement) : `equation2026`

## 🔄 Cycle de mise à jour recommandé

| Fichier | Fréquence conseillée |
|---|---|
| Organisations Pipedrive | tous les 1-3 mois |
| Contacts Pipedrive | tous les mois |

L'app affiche en page d'accueil :
- 🟢 < 30 jours : à jour
- 🟠 30-60 jours : à rafraîchir
- 🔴 > 60 jours : périmé

## 🛠️ Stack

- **Streamlit** : interface
- **pandas / openpyxl** : traitement Excel
- **Folium** : carte interactive
- **API Base Adresse Nationale** (adresse.data.gouv.fr) : géocodage

## 📁 Structure attendue des fichiers Pipedrive

### Organisations
Colonnes requises : `Organisation - ID`, `Organisation - Nom`, `Organisation - Adresse`
+ toutes les autres colonnes métier (postes, surface, échéance bail, etc.)

### Contacts
Colonnes requises : `Personne - ID`, `Organisation - ID`, `Personne - Prénom`,
`Personne - Nom de famille` + emails, téléphones, LinkedIn.
