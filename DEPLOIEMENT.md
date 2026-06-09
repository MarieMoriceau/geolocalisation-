# 🚀 Guide de déploiement Hugging Face

## Étape 1 — Créer le Space

1. Va sur https://huggingface.co/new-space
2. Remplis :
   - **Space name** : `equation-sie-prospection` (ou ce que tu veux)
   - **License** : *Other* (proprietary)
   - **SDK** : **Streamlit**
   - **Hardware** : *CPU basic* (gratuit, largement suffisant)
   - **Visibility** : ⚠️ **PRIVATE** (très important — données Pipedrive)
3. Clique sur **Create Space**

## Étape 2 — Uploader les fichiers

Tu as 2 options :

### Option A — Via l'interface web (le plus simple)
1. Sur la page du Space, clique sur **Files** → **+ Contribute** → **Upload files**
2. Glisse les 4 fichiers du dossier :
   - `app.py`
   - `requirements.txt`
   - `README.md`
   - `.gitignore`
3. Commit message : "Initial deployment"
4. **Commit changes**

### Option B — Via Git (si tu es à l'aise)
```bash
git clone https://huggingface.co/spaces/TON_USER/equation-sie-prospection
cd equation-sie-prospection
# Copier les 4 fichiers ici
git add .
git commit -m "Initial deployment"
git push
```

## Étape 3 — Configurer le mot de passe admin

1. Dans le Space, clique sur **Settings** (icône engrenage en haut)
2. Descends jusqu'à **Variables and secrets** → **New secret**
3. Ajoute :
   - **Name** : `ADMIN_PASSWORD`
   - **Value** : un mot de passe robuste (ex: `Equation@2026!Prosp`)
4. **Save**

⚠️ Si tu ne fais pas cette étape, le mot de passe par défaut est `equation2026` — à changer impérativement avant usage.

## Étape 4 — Attendre le build

Le Space va se construire automatiquement (~2-3 min). Tu peux suivre les logs
dans l'onglet **Logs**.

Quand tu vois "Your app is running on http://..." → c'est prêt.

## Étape 5 — Premier usage

1. Ouvre ton Space
2. Va dans l'onglet **⚙️ Admin**
3. Saisis le mot de passe
4. Upload le fichier **organisations** Pipedrive (.xlsx)
   → Géocodage automatique (~1 min)
5. Upload le fichier **contacts** Pipedrive (.xlsx)
6. Reviens dans l'onglet **🔍 Recherche** → c'est parti !

## ❓ Problèmes courants

| Problème | Solution |
|---|---|
| L'app crash au démarrage | Vérifier les logs du Space, souvent un souci de `requirements.txt` |
| "Adresse pivot non trouvée" | L'API BAN ne reconnaît que les adresses françaises |
| Géocodage très lent | L'API BAN peut avoir des pics de latence, le code retry automatiquement |
| Fichier > 100 Mo refusé | Limite HF — découper le fichier en plusieurs envois |

## 🔄 Mettre à jour les données

À chaque fois que tu veux rafraîchir :
1. Onglet **Admin** → uploader un nouveau fichier organisations ou contacts
2. La date d'import se met à jour automatiquement sur la page d'accueil
3. Le statut passe à 🟢 À jour

## 💰 Coûts

- Space privé Streamlit en CPU basic : **gratuit** pour les comptes Pro,
  ou ~9$/mois pour avoir des Spaces privés en compte gratuit
- Vérifier sur https://huggingface.co/pricing

## 🆘 En cas de souci

Logs du Space : onglet **Logs** dans l'interface HF.
Pour redémarrer : **Settings** → **Factory rebuild**.
