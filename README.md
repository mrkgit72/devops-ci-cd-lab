# Mini-Projet DevOps – CI/CD avec GitHub Actions

## Objectif:
Développer une page HTML dédiée à votre groupe, intégrée dans une application Flask, et soumise à un pipeline CI/CD via GitHub Actions.

## Niveau 1 : Intégration ([aide: Fiche-CI](Fiche-CI.md)) 

### Structure du projet
Le dépôt parent contient :
```
devops-v2/
├── app.py
├── templates/
│   ├── base.html
│   ├── home.html
│   ├── group10.html  <--- A MODIFIER par le groupe 10
│   ├── group20.html  <--- A MODIFIER par le groupe 20
│   └── ...
├── .github/
│   └── workflows/
│       └── ci.yml
└── README.md
```

---
### 👉 IMPORTANT : NE TELEVERSEZ QUE LA PAGE DE VOTRE GROUPE 
---

### Étapes à suivre

1. **Fork du dépôt parent**
   - Rendez-vous sur le dépôt GitHub `devops-ci-cd-lab`
   - Cliquez sur **Fork** pour créer votre propre copie

2. **Cloner et tester votre fork localement**
   ```bash
   git clone https://github.com/votrelogin/devops-ci-cd-lab.git
   cd devops-ci-cd-lab
   docker-compose down
   docker-compose up -d --build
   curl localhost:5000
   ```

3. **Modifier votre fichier HTML**
   - Allez dans `templates/groupeYY.html` (remplacez YY par votre numéro de groupe)
   - Personnalisez le contenu selon les consignes du projet ([voir contenu-requis](contenu-requis.md))

   - Tester et valider vos modifications 
      - `docker exec -it devops-tp pytest -v `
      - `docker exec -it devops-tp flake8 app.py test_app/py`
      - si erreur, corriger et retester
      - Relancer : 
            1) `docker-compose down` 
            2) `docker-compose up -d --build`
      - Vérifier : `curl localhots:5000`

4. **Commit & Push**
```bash
git add templates/groupeYY.html

git commit -m "votre commentaire"

git push origin main
```

5. **Créer une Pull Request**
   - Vérifiez que les tests CI/CD passent (GitHub Actions) 
   - Depuis GitHub, ouvrez une **Pull Request** vers le dépôt parent ([voir § Téléverser vos changements dans Fiche-CI.md](./Fiche-CI.md))

6. **Validation**
   - Si le pipeline CI/CD est vert ✅, votre PR sera mergée
   - Sinon, corrigez les erreurs et recommencez

### Livraison attendue
- Un seul fichier modifié : `templates/groupeYY.html`
- Une Pull Request propre et validée par le pipeline CI/CD

---

## Niveau 2 : Déploiement 
[Lire Fiche-CD](Fiche-CD.md)


<!-- 
----------------- Notes formateur --------------------------
- Actions
   - DONE compte: mrkgit72: devops-tp2-draft-prof fork with devops-tp2-draft
   - Rester entièrement devops-v2

- compte Github formateur 
   * mrkgit72 / m....1xXX

- No edit in Container : only run (by docker or manually by using docker exec -it <container name> <shell command>)

- create PR with main branch
   * go to Gisthub UI
   * "contribute" -> "create PR" # make sure the destination repo is that wanted

- si on utilise une branche (c'est le process standard pour les PR)
  - docker-compose down
  - git checkout -b new-branche  # a new branch per PR
  - docker-compose up -d --build
  - edit dans host
  - run on container : docker exec -it devios-tp pytest -v
  - git add files
  - git commit -m "comment"
  - git push origin new-branch
  - go github UI and create PR and choose the destination : the fork repo or the parent.

- synchro du Fork avec le parent
   - Méthode 1
      * aller sur github du fork (repo de travail)
      * bouton "Sync Fork"
      * en local : git pull
   - Méthode 2 : ajouter le parent comme remote
      * git remote add upstream <liknk-to-repo-parent.git>
      * git fetch upstream
      * git merge upstream/main
      * git push origin main

- Reminder SSH for Github
   * ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   * cat ~/.ssh/id_rsa_github.pub
   * copy/paste in Github 
   * git clone ssh-git-link !!!!!!

- Ressource
  * Comment effectuer des tests unitaires dans Flask: https://fr.linux-console.net/?p=34043
  * https://dev.to/david_oyewole/automating-flask-deployment-with-github-actions-and-docker-4j1a
  


 -->



