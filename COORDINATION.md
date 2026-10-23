# Coordination binome A / binome B - TP3 NetSecure

Salut Binome B,

Le projet "NetSecure" n'existait pas encore avant ce TP, donc j'ai du poser les bases
(infra minimale) avant de pouvoir commencer la Partie 1 et la Partie 2. Voila ou j'en suis.

## Ce que j'ai fait (Binome A)

- Architecture minimale : une API Flask (`api/`) avec un endpoint `/health` et un endpoint
  `/check?host=...&port=...` qui teste si un port est ouvert.
- Un reverse proxy NGINX (`nginx/`) devant l'API.
- Un `compose.yaml` avec deux reseaux :
  - `backend` (interne, marque `internal: true`) : seul moyen pour nginx de parler a l'api,
    pas joignable depuis la machine hote.
  - `frontend` : seul nginx y est expose sur l'hote (port 80).
Je pousse ca tout de suite pour que tu voies l'avancement, meme si je n'ai pas encore fait
la reconnaissance (Partie 1) ni le scan Trivy (Partie 2). Je mets a jour ce fichier et
j'ajoute `SCAN_INITIAL.md` + `REPONSES_A.md` dans un commit suivant, sur la meme branche.

Tout ca est sur la branche `binome-a/infra-audit`, avec une Pull Request ouverte vers
`main` (je ne la fusionne pas moi-meme).

## Pour Binome B

Tu peux repartir directement de cette branche (ou attendre que la PR soit mergee, selon ce
qui est convenu avec le prof) pour faire :

- Partie 3 (durcissement de l'image / des conteneurs)
- Partie 4 (pipeline CI avec Trivy dans GitHub Actions)
- Questions Q4, Q6, Q8

Regarde `SCAN_INITIAL.md` pour savoir quelles vulnerabilites j'ai trouvees sur l'image de
l'API : ca devrait te servir de base pour ton durcissement (Partie 3).

## Blocages

Aucun blocage de mon cote pour l'instant. Si en avancant sur la Partie 3/4 tu as besoin de
quelque chose cote infra (ex: changer un Dockerfile, ajouter une variable d'env, etc.), tu
peux le faire directement dans ta PR et je regarderai en relecture.
