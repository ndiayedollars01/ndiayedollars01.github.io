# Les pages publiques — à héberger avant la mise en ligne sur Google Play

> ⚠️ **Ce dossier s'appelait `web/`.** Il a été renommé `docs/` le
> 9 septembre 2026 pour une raison bête et incontournable : GitHub Pages
> ne propose que **deux** dossiers source, la racine du dépôt ou
> `/docs`. Aucun autre nom n'apparaît dans le menu, et la marche à
> suivre écrite ici était donc impossible à appliquer telle quelle.

Ce dossier ne fait pas partie de l'application. Ce sont quatre fichiers
statiques — aucun script, aucune dépendance — destinés à être publiés à
une **adresse web publique**, parce que Google Play réclame deux liens
qu'une page interne à l'application ne peut pas satisfaire :

| Ce que Play demande | Le fichier |
| --- | --- |
| **Privacy policy** (fiche du magasin ET formulaire « Sécurité des données ») | `confidentialite.html` |
| **URL de demande de suppression du compte** (section Sécurité des données) | `suppression-compte.html` |

`conditions.html` n'est pas exigé par Play, mais un magasin qui ne trouve
aucune condition d'utilisation pour une application qui encaisse des
commissions pose des questions. `index.html` relie les trois : sans lui,
la racine du site renvoie une erreur 404.

## Publier

Le plus simple, et gratuit : **GitHub Pages**.

1. Pousser le dépôt sur GitHub — les pages sont servies depuis ce qui y
   est publié, pas depuis le disque local.
2. Sur le dépôt, `Settings` → `Pages`.
3. `Source` : **Deploy from a branch**, branche `master`, dossier
   **`/docs`**. Enregistrer.
4. Attendre deux minutes. L'adresse est alors
   `https://ndiayedollars01.github.io/yoonu-travel/`, et la politique se
   trouve à `.../confidentialite.html`.
5. Ouvrir les trois pages dans un navigateur AVANT de coller quoi que ce
   soit dans la Play Console : une adresse qui rend une 404 fait rejeter
   la fiche, et le refus arrive plusieurs jours plus tard.
6. Coller cette adresse dans la Play Console, aux deux endroits du
   tableau ci-dessus.

⚠️ **Le dépôt doit être public.** GitHub Pages n'est disponible sur un
dépôt privé qu'avec un compte payant. S'il est privé et doit le rester,
n'importe quel hébergement statique gratuit fait l'affaire — Netlify ou
Vercel acceptent un dossier déposé tel quel, il n'y a rien à construire.

## La règle à ne pas oublier

**Ces pages recopient les textes de l'application.** Quand
`app/confidentialite.tsx` ou `app/conditions.tsx` change, le fichier HTML
correspondant change dans le même commit, et la date en tête des deux
suit `MAJ_TEXTES_LEGAUX` (`src/lib/legal.ts`).

Deux versions différentes du même engagement, l'une dans le téléphone et
l'autre sur le web, c'est précisément ce qu'un litige vient chercher.

## Ce qui reste à compléter

Le NINEA et le RCCM apparaissent comme « en cours d'immatriculation »
dans `conditions.html` comme dans l'application. Le jour de
l'immatriculation, les deux se corrigent — ainsi que
`MENTIONS_ENTREPRISE` dans `src/lib/legal.ts`, qui alimente les reçus.
