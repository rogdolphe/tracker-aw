# FINANCES.PERSO — Guide d'installation GitHub Sync + App Mobile

## CE QUE ÇA DONNE À LA FIN
- L'app est installable sur ton téléphone (icône sur l'écran d'accueil, s'ouvre en plein écran)
- Desktop et mobile lisent/écrivent les mêmes données via GitHub
- Chaque sauvegarde pousse les données dans ton repo (historique = backup automatique)

---

## ÉTAPE 1 — Créer le Personal Access Token GitHub (5 min)

1. Va sur : https://github.com/settings/tokens
2. Clique "Generate new token" → "Generate new token (classic)"
3. Note : "FINANCES.PERSO sync"
4. Expiration : "No expiration" (ou 1 an)
5. Coche UNIQUEMENT : ☑ repo (toute la case, pas juste les sous-options)
6. Clique "Generate token" tout en bas
7. **⚠️ COPIE LE TOKEN MAINTENANT — il commence par ghp_ — tu ne le reverras plus jamais**
   Sauvegarde-le dans Notes ou quelque part sécuritaire.

---

## ÉTAPE 2 — Créer le fichier de données dans ton repo (2 min)

1. Va sur ton repo GitHub : https://github.com/rogdolphe/tracker-aw
2. Clique "Add file" → "Create new file"
3. Nom du fichier : fin_data.json
4. Contenu : {}
5. Clique "Commit changes" (message par défaut, c'est correct)

---

## ÉTAPE 3 — Ajouter les 3 fichiers dans ton repo (5 min)

Tu dois ajouter ces 3 fichiers dans la MÊME branche que ton HTML (probablement main ou gh-pages).

### finances_perso.html
→ Remplace ton fichier HTML actuel par la nouvelle version fournie.
   Même procédure : édite le fichier existant ou supprime/recrée.

### manifest.json
→ Crée un nouveau fichier "manifest.json" dans le repo.
   Copie-colle le contenu du fichier manifest.json fourni.

### icon.svg
→ Crée un nouveau fichier "icon.svg" dans le repo.
   Copie-colle le contenu du fichier icon.svg fourni.

---

## ÉTAPE 4 — Configurer le token dans l'app (2 min)

1. Ouvre l'app : https://rogdolphe.github.io/tracker-aw/finances_perso.html
2. Va dans l'onglet "OBJECTIF & PROJECTION"
3. Trouve la carte "☁️ GitHub Sync"
4. Remplis :
   - Propriétaire repo : rogdolphe
   - Nom du repo : tracker-aw
   - Fichier données : fin_data.json
   - Token : colle ton ghp_xxxx
5. Clique "Connecter & Syncer →"
6. Si ça marche : tu vois "✓ Connecté" et une icône ☁ verte dans le header

---

## ÉTAPE 5 — Installer l'app sur mobile Android/Chrome (2 min)

1. Ouvre Chrome sur ton téléphone
2. Va sur : https://rogdolphe.github.io/tracker-aw/finances_perso.html
3. Tape les 3 points ⋮ en haut à droite
4. Clique "Ajouter à l'écran d'accueil" (ou "Installer l'app")
5. Confirme le nom "Finances" → Installer
6. L'icône apparaît sur ton écran d'accueil
7. Ouvre l'app → configure le token (Étape 4) sur le téléphone aussi

---

## ÉTAPE 6 — Installer l'app sur desktop Chrome (optionnel)

1. Ouvre Chrome sur ton desktop
2. Va sur l'URL de l'app
3. Dans la barre d'adresse, cherche l'icône d'installation (carré avec flèche vers le bas)
   ou : Menu ⋮ → "Installer Finances Perso..."
4. Confirme → l'app s'ouvre dans sa propre fenêtre, sans barre d'adresse

---

## COMMENT LE SYNC FONCTIONNE

- Au démarrage : l'app charge tes données locales immédiatement (pas de délai),
  puis fetche GitHub pour voir s'il y a une version plus récente
- À chaque modification : après 1.5 secondes d'inactivité, tes données sont
  poussées vers fin_data.json sur GitHub
- L'icône ☁ dans le header indique l'état :
  - ☁ vert = synchronisé
  - ⟳ = en train de sauvegarder
  - ✗ rouge = erreur (clique pour aller aux settings)

## EN CAS DE PROBLÈME

- Erreur 401 → token incorrect ou expiré → regénère un nouveau token
- Erreur 404 → fin_data.json n'existe pas → crée-le (Étape 2)
- Données différentes entre appareils → utilise "⟳ Sync maintenant" dans les settings
- Réinitialiser → clique "Déconnecter" puis reconnecte

## SÉCURITÉ

Le token est stocké dans le localStorage de ton navigateur (pas dans le HTML).
Il donne accès en écriture à ton repo. Ne le partage jamais.
Si tu penses qu'il est compromis, va sur github.com/settings/tokens et révoque-le.
