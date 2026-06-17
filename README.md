# Test Standard — Loksite

## Fichiers du repo

| Fichier | Rôle |
|---|---|
| `vitrine.html` | Site public — vitrine publiée, servie via GitHub Pages |
| `vitrine-preview.html` | Copie de travail utilisée par l'éditeur intégré (LKE) dans l'espace client avant publication. "Enregistrer" écrit ici, "Publier" copie ce fichier vers `vitrine.html` |
| `espace.html` | Espace client Loksite (connexion, tableau de bord, modification du site, messages, réservations, analytics…) |

## Identité du client de test

| Champ | Valeur |
|---|---|
| Nom | Test Standard |
| Email | muscu.digital@gmail.com |
| Ville | Lille |
| Téléphone | 07 49 17 54 70 |
| Type d'activité | Restaurant (générique) |
| Plan | Standard — 49€/mois |

## Déploiement

Ce repo est servi tel quel via **GitHub Pages** (branche `main`, racine `/`).

- Vitrine publique : `https://loksite.github.io/test-standard/vitrine.html`
- Espace client : `https://loksite.github.io/test-standard/espace.html`

## Backend

- **Supabase** : `qhnofvfgutsdgbfwhupg.supabase.co` — table `profiles`, colonne `github_repo` = `Loksite/test-standard`
- **n8n** : workflow "Loksite — Assistant IA" pour la publication et les modifications via l'éditeur (selon le plan souscrit)

## ⚠️ À faire après création du compte Supabase Auth

`vitrine.html` et `vitrine-preview.html` contiennent une variable `CLIENT_ID` (UUID) câblée en dur pour le suivi analytics (lignes ~394 et ~489), reprise du client précédent. **Elle doit être remplacée par l'UUID réel du compte Test Standard** une fois celui-ci créé dans Supabase Authentication, sinon les visites seront comptabilisées sur le mauvais profil.

## Notes

Ce compte est un compte de **test** servant à valider le parcours d'onboarding complet (création Supabase → création repo GitHub → connexion espace client) pour le plan **Standard**, qui donne accès à la quasi-totalité des fonctionnalités (réservations, rapport PDF, QR code, programmation de publication, statistiques avancées) à l'exception des trois widgets analytics exclusifs Premium (taux d'engagement, sections cliquées, visiteurs vs réservations), déjà correctement masqués par `isPremiumPlan()` dans `espace.html`.
