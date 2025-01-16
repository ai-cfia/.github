# Contributing to the CFIA AI Lab

([*Le français est disponible au bas de la
page*](#contribuer-au-labo-dia-de-lacia))

- [Overview](#overview)
- [Development Practices](#development-practices)
  - [Managing Secrets](#managing-secrets)
  - [Editor settings](#editor-settings)
- [Using GitHub Issues](#using-github-issues)
- [Working with GitHub Projects](#working-with-github-projects)
- [Creating a new repository in the
  Organization](#creating-a-new-repository-in-the-organization)
- [Filing an Issue/ticket](#filing-an-issueticket)
- [Creating a Pull Request](#creating-a-pull-request)
- [Working on a Pull Request](#working-on-a-pull-request)
- [Submit for review](#submit-for-review)
- [Reviewing and Approving a Pull
  Request](#reviewing-and-approving-a-pull-request)
- [Closing Pull Requests](#closing-pull-requests)
- [GitHub development processes](#github-development-processes)
  - [Handling divergent branches](#handling-divergent-branches)
    - [Configuring Git for Automatic
      Rebase](#configuring-git-for-automatic-rebase)
    - [Rebase with VScode GitHub
      extension](#rebase-with-vscode-github-extension)

## Overview

This guide details the CFIA AI Lab’s development practices and GitHub workflow,
covering Issues, Projects, Pull Requests, and code reviews to ensure efficient,
collaborative, and high-quality development.

## Development Practices

### Managing Secrets

**⚠️Warning: Never add secrets directly in your code.** Even if it's for quick
testing, secrets in code can easily be committed accidentally.

To securely manage sensitive information, we use `.env` files for
environment-specific configuration and `.env.template` files as templates for
these configurations.

1. **Copy .env.template:** Duplicate the `.env.template` file to create a `.env`
   file locally.

1. **Fill in Secrets:** Add environment-specific values (e.g., API keys,
   database credentials) to your `.env` file as needed. Ask the DevOps team
   about accessing Vault, our secrets management tool, to retrieve them.

1. **Access Secrets in Code**: Use `load_dotenv()` to load values from `.env`,
   then access them with `os.getenv("NAME_OF_SECRET")`.

1. **Protect .env**: Ensure `.env` is listed in `.gitignore` to prevent it from
   being committed to version control.

### Editor settings

Ensure that your editor (preferably in project workspaces) has the following
turned on:

- Automatically wrap lines to 80 characters in Markdown files
  - use Rewrap extension
- Trim Final Newlines: Ensures your files end neatly with a single newline.
- Trim Trailing Whitespace: Eliminates any superfluous spaces at the end of
  lines upon file save.
- Insert Final Newline: Add EOF new line when saving.

## Using GitHub Issues

1. Go to the organization's GitHub repository.
2. Click on [Projects](https://github.com/orgs/ai-cfia/projects) and select a
   project to see all its issues.
3. Create a new issue and assign it to a specific developer. Make sure to:
   - give the issue meaningful title and description
   - assign it the appropriate labels
   - not create new labels at repository level

## Working with GitHub Projects

1. Open the organization's GitHub repository.
2. Click on [Projects](https://github.com/orgs/ai-cfia/projects) and select a
   project to view its board.
3. **Issue Prioritization**: The tasks can be reordered in the table by dragging
   their priority number up or down. The higher up a task is, the more urgent it
   is.
4. **Assignment**: In the `Assignees` column, chose an assignee.
5. **Status**: In the `status` column, update the progress on the issue to keep
   track of it.

**Notes**:

- If the particular repository on which you are working doesn't have a GitHub
  Project, create one with the permission of your supervisor. Follow this
  [guide](https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/quickstart-for-projects).
- Don't assign issues before they are prioritized (by your supervisor or the
  whole team)

## Creating a new repository in the Organization

Refer to the [GitHub Repository Creation
Guide](https://github.com/ai-cfia/devops/blob/main/github-repository-creation-guide.md)
in the DevOps repository for information.

## Filing an Issue/ticket

A good issue:

- A good, descriptive title that is understandable even to management.
- A full summary that provides context.
- Detailed, step-by-step descriptions of the work to be done.
- Clearly defined acceptance criteria.
- A task list that is correctly associated with a project.
- The inclusion of links and (sequence) diagrams to further clarify the work.
- Information about the version and environment tested against, along with
  reproduction steps for filed issues.
- For web applications, utilization of the Developer tools panel in the browser.
- The use of text, screenshots, application logs, and console logs to convey
  information.
- An explanation of the root causes of the problem.

Additionally, issues should be appropriately sized, avoiding refactoring or
minor fixes that could be added as tasks to existing issues. When creating an
issue as a follow-up to a comment in another issue or pull request, utilize the
"Reference in new issue" GitHub feature (found in the ... menu) to provide
context and enhance clarity.

## Creating a Pull Request

1. Reference which issue this PR closes in the description
2. Plan the work required to complete the change as a checklist
    1. Make it work first!
    2. Refactoring
    3. documentation of usage and architecture
    4. manual testing (updatest to TESTING.md)
    5. automated testing
    6. versioning bump (_versions.ts in frontend projects)
3. Mark your pull request as a draft.

    ![Draft](../img/draft-pr.png)

4. Make all the necessary changes you want.
5. Once you addressed all the requests, you can ask for a re-review.

![Re-review](../img/re-review.png)

## Working on a Pull Request

Push and share your code early and often. When you share early code still under
development, prefix your PR with WIP (meaning Work-in-Progress) so that
reviewers know this is not your final version.

## Submit for review

Select list of reviewers that are relevant to the PR, including team lead.

You should also include relevant reviewers even if they are absent or on
vacation so they can catch up when they come back. Their approval is not
required in the meantime to complete the PR.

## Reviewing and Approving a Pull Request

1. Team members review the pull request, leave comments, and suggest changes if
   necessary.
2. Developer addresses the feedback and makes the necessary updates. Developer
   replies to all review comments with "done", comments, new issues (to postpone
   work to future PR) or clarifying questions
3. Once the pull request meets the required criteria, a team member approves the
   pull request.

## Closing Pull Requests

1. Once the pull request is approved, navigate to the pull request's
   description.
2. Update the description by adding the text `Closes #<issue number>` to
   indicate that the issue has been addressed and completed.
3. Consider rebasing and squashing the commit history
4. Merge the pull request into the main branch. If you have a merge conflict
   with your branch being divergent from the main branch, please refer to the
   following [section](#handling-divergent-branches).

5. Don't delete the branch when done (leave them for future reference).

Following this workflow will help in managing tasks, tracking progress, and
closing issues effectively using GitHub's features.

For more detailed information and specific steps, please refer to the GitHub
documentation or reach out to your team for any additional guidelines or
conventions.

[see this repository .vscode/settings.json as example](../.vscode/settings.json)

## GitHub development processes

- check your [Github organization](https://github.com/ai-cfia)
  [notifications](https://github.com/notifications) twice daily.
  - Customize email routing to route ai-cfia repo notifications to your
    inspection.gc.ca
  - Prioritize pull requests reviews above all else
  - Do not just rubber stamp; provide value as a reviewer
- every work item should have a matching issue describing the work to be done
- pull requests
  - branch -> pull request -> peer review -> fixes -> approval -> rebase and
    merge
  - name branch prefix with issue identifier (```59-some-issue-summary```)
  - reference the issue within the description of the pull request
  - do as many request reviews -> get comments from reviewer -> fix and answer
    comments -> request reviews as necessary (until you get the reviewer(s)
    approval
- update your [Github notification settings with Custom
  Routing](<https://github.com/settings/notifications/custom_routing>) from the
  ai-cfia org to your inspection.gc.ca email
- single line commits preferably prefixed with issues being worked on.
  - example: `Issue #19: Introduction Jolan Thomassin`
- don't delete branches when done (leave them for future reference)
- when feedback, suggestions or feature request that come up in one of your PR
  by a reviewer that would require a lot more work outside the scope of the
  current issue, it is encouraged to create a new issue capturing that
  non-trivial piece of work and document it as "postponed work" in the PR.

### Handling divergent branches

When your branch diverges from the main branch (due to updates in the main
branch while you're working on your branch), follow these steps to rebase your
branch onto the main branch. This keeps the project history clean and linear.

```ascii
main      A---B---C---D
               \
branch          E---F---G (divergent)
```

A, B, C, D are commits on the main branch, and E, F, G are your commits on the
branch. C and D are new commits added to the main branch after you created your
branch.

Steps to manually Rebase and Merge

1.Fetch Latest main branch:

```sh
git fetch origin main
```

2.Rebase Your Branch:

Start the rebase process to replay your branch's changes (E, F, G) on top of the
current state of the main branch (D).

```sh
git rebase origin/main
```

3.Resolve Conflicts (if any):

```sh
git add <file>
git rebase --continue
```

Repeat until all conflicts are resolved and the rebase completes.

Push Changes:

Since rebase rewrites history, you'll need to force push your branch.

```sh
git push --force-with-lease
```

This process ensures your changes maintains a linear history :

```ascii
main      A---B---C---D
                        \
branch                   E'---F'---G' (rebased)
```

#### Configuring Git for Automatic Rebase

To set up Git to automatically rebase instead of creating merge commits when
doing a git pull, you can use the following global configuration command:

```sh
git config --global pull.rebase true
```

#### Rebase with VScode GitHub extension

1. Open the command palette (Ctrl+Shift+P)
2. Search for "Rebase" and select "Git: Pull (Rebase)"
3. Select the branch you want to rebase onto the main branch
4. Resolve any conflicts and push your changes

---

## Contribuer au Labo d'IA de l'ACIA

- [Vue d'ensemble](#vue-densemble)
- [Pratiques de développement](#pratiques-de-développement)
  - [Gestion des secrets](#gestion-des-secrets)
  - [Paramètres de l'éditeur](#paramètres-de-léditeur)
- [Utiliser les Issues GitHub](#utiliser-les-issues-github)
- [Travailler avec les Projets GitHub](#travailler-avec-les-projets-github)
- [Créer un nouveau dépôt dans
  l'organisation](#créer-un-nouveau-dépôt-dans-lorganisation)
- [Créer une Issue/Ticket](#créer-une-issueticket)
- [Créer une Pull Request](#créer-une-pull-request)
- [Travailler sur une Pull Request](#travailler-sur-une-pull-request)
- [Soumettre pour révision](#soumettre-pour-révision)
- [Réviser et approuver une Pull
  Request](#réviser-et-approuver-une-pull-request)
- [Fermer les Pull Requests](#fermer-les-pull-requests)
- [Processus de développement GitHub](#processus-de-développement-github)
  - [Gérer les branches divergentes](#gérer-les-branches-divergentes)
    - [Configurer Git pour le Rebase
      automatique](#configurer-git-pour-le-rebase-automatique)
    - [Rebase avec l'extension GitHub pour
      VScode](#rebase-avec-lextension-github-pour-vscode)

## Vue d'ensemble

Ce guide détaille les pratiques de développement du Labo d'IA de l'ACIA et le
workflow GitHub, couvrant les Issues, Projets, Pull Requests et les revues de
code pour garantir un développement collaboratif, efficace et de haute qualité.

## Pratiques de développement

### Gestion des secrets

**⚠️ Avertissement : Ne jamais ajouter de secrets directement dans votre code.**
Même pour des tests rapides, des secrets dans le code peuvent être
accidentellement ajoutés au dépôt.

Pour gérer les informations sensibles en toute sécurité, nous utilisons des
fichiers `.env` pour la configuration spécifique à l'environnement et des
fichiers `.env.template` comme modèles.

1. **Copiez `.env.template` :** Dupliquez le fichier `.env.template` pour créer
   un fichier `.env` localement.

2. **Remplissez les secrets :** Ajoutez les valeurs spécifiques à
   l'environnement (ex. : clés API, identifiants de base de données) dans votre
   fichier `.env`. Consultez l'équipe DevOps pour accéder à Vault, notre outil
   de gestion des secrets.

3. **Accès aux secrets dans le code :** Utilisez `load_dotenv()` pour charger
   les valeurs depuis `.env`, puis accédez-y avec `os.getenv("NOM_DU_SECRET")`.

4. **Protégez `.env` :** Assurez-vous que `.env` est listé dans `.gitignore`
   pour éviter qu'il ne soit ajouté au dépôt.

### Paramètres de l'éditeur

Assurez-vous que votre éditeur (de préférence dans les espaces de travail des
projets) a les options suivantes activées :

- Enroulement automatique des lignes à 80 caractères dans les fichiers Markdown
  - Utilisez l'extension Rewrap
- Suppression des nouvelles lignes finales superflues : Garantit que vos
  fichiers se terminent proprement par une seule nouvelle ligne.
- Suppression des espaces inutiles : Élimine les espaces superflus à la fin des
  lignes lors de l'enregistrement des fichiers.
- Ajout d'une nouvelle ligne finale : Ajoute une nouvelle ligne EOF (End Of
  File) lors de l'enregistrement.

## Utiliser les Issues GitHub

1. Accédez au dépôt GitHub de l'organisation.
2. Cliquez sur [Projets](https://github.com/orgs/ai-cfia/projects) et
   sélectionnez un projet pour voir ses Issues.
3. Créez une nouvelle Issue en lui assignant un(e) développeur(euse) spécifique.
   Assurez-vous de :
   - Donner un titre et une description significatifs.
   - Lui assigner des labels appropriés.
   - Ne pas créer de nouveaux labels au niveau du dépôt.

## Travailler avec les Projets GitHub

1. Ouvrez le dépôt GitHub de l'organisation.
2. Cliquez sur [Projets](https://github.com/orgs/ai-cfia/projects) et
   sélectionnez un projet pour afficher son tableau.
3. **Priorisation des tâches** : Réorganisez les tâches selon leur priorité.
4. **Assignation** : Dans la colonne `Assignees`, choisissez un(e) responsable.
5. **Statut** : Mettez à jour l'avancement dans la colonne `status`.

**Notes :**

- Si le dépôt particulier sur lequel vous travaillez n'a pas de projet GitHub,
  créez-en un avec l'autorisation de votre superviseur(euse). Suivez ce
  [guide](https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/quickstart-for-projects).
- N'assignez pas d'issues avant qu'elles ne soient priorisées (par votre
  superviseur(euse) ou toute l'équipe).

## Créer un nouveau dépôt dans l'organisation

Consultez le [Guide de création de dépôt
GitHub](https://github.com/ai-cfia/devops/blob/main/github-repository-creation-guide.md)
dans le dépôt DevOps.

## Créer une Issue/Ticket

Une bonne issue doit inclure :

- Un titre descriptif et compréhensible.
- Un résumé complet fournissant le contexte.
- Des descriptions détaillées (étape par étape) du travail à réaliser.
- Des critères d'acceptation clairement définis.
- Une liste de tâches correctement associée à un projet.
- L'inclusion de liens et de diagrammes (comme des diagrammes de séquence) pour
  clarifier davantage le travail.
- Des informations sur la version et l'environnement testés, ainsi que des
  étapes de reproduction pour les bugs signalés.
- Pour les applications web, l'utilisation du panneau d'outils développeur du
  navigateur.
- L'utilisation de texte, captures d'écran, journaux d'application et journaux
  de console pour transmettre les informations.
- Une explication des causes profondes du problème.

De plus, les issues doivent être de taille appropriée, en évitant le refactoring
ou les corrections mineures qui pourraient être ajoutées comme tâches à des
issues existantes. Lors de la création d'une issue en tant que suivi d'un
commentaire dans une autre issue ou pull request, utilisez la fonctionnalité
"Référencer dans une nouvelle issue" de GitHub (disponible dans le menu ...)
pour fournir un contexte et améliorer la clarté.

## Créer une Pull Request

1. Référencez l'issue que cette PR ferme dans la description.
2. Planifiez le travail requis sous forme de checklist :
   - Rendre fonctionnel en premier.
   - Refactorisation.
   - Documentation de l'utilisation et de l'architecture.
   - Tests manuels (mise à jour de TESTING.md).
   - Tests automatisés.
   - Mise à jour de version (_versions.ts dans les projets frontend).
3. Marquez la PR comme brouillon.
4. Effectuez les modifications nécessaires.
5. Demandez une relecture une fois terminé.

![Re-review](../img/re-review.png)

## Travailler sur une Pull Request

Partagez votre code fréquemment. Préfixez les PR en cours par WIP
(Work-in-Progress) pour indiquer qu'il s'agit d'une version en développement.

## Soumettre pour révision

Sélectionnez les membres d'équipe pertinents, y compris le ou la responsable
d'équipe.

Ajoutez les absent(e)s pour qu'ils puissent suivre à leur retour. Leur
approbation n'est pas obligatoire en attendant.

## Réviser et approuver une Pull Request

1. Les membres de l'équipe examinent la PR et laissent des commentaires.
2. Le développeur ou la développeuse ajuste le code en fonction des retours,
   répond aux commentaires et peut ouvrir de nouvelles issues pour différer les
   tâches non critiques.
3. Une fois la PR conforme, un(e) membre l'approuve.

## Fermer les Pull Requests

1. Une fois que la pull request est approuvée, accédez à sa description.
2. Mettez à jour la description en ajoutant le texte `Closes #<numéro de
   l'issue>` pour indiquer que l'issue a été traitée et complétée.
3. Envisagez de rebaser et de fusionner les commits pour nettoyer l'historique.
4. Fusionnez la pull request dans la branche principale. Si vous avez un conflit
   de fusion avec une branche divergente, consultez la
   [section](#gérer-les-branches-divergentes).

5. Ne supprimez pas la branche après la fusion (gardez-la pour une référence
   future).

En suivant ce workflow, vous pourrez gérer les tâches, suivre les progrès et
clôturer les issues efficacement en utilisant les fonctionnalités de GitHub.

Pour des informations plus détaillées et des étapes spécifiques, veuillez
consulter la documentation GitHub ou contacter votre équipe pour toute directive
ou convention supplémentaire.

[Consultez cet exemple de fichier `.vscode/settings.json` dans ce
dépôt](../.vscode/settings.json)

## Processus de développement GitHub

- Consultez vos [notifications GitHub](https://github.com/notifications) deux
  fois par jour.
  - Personnalisez le routage des e-mails pour acheminer les notifications des
    dépôts ai-cfia vers votre adresse inspection.gc.ca.
  - Priorisez les revues de pull requests avant toute autre tâche.
  - Ne validez pas sans examiner ; apportez une réelle valeur en tant que
    réviseur(e).
- Chaque tâche doit avoir une issue correspondante décrivant le travail à
  effectuer.
- Workflow des pull requests :
  - branche -> pull request -> revue par les pairs -> corrections -> approbation
    -> rebase et fusion.
  - Préfixez les noms de branche avec l'identifiant de l'issue
    (```59-some-issue-summary```).
  - Référencez l'issue dans la description de la pull request.
  - Faites autant de revues que nécessaire -> recevez des commentaires du
    relecteur -> corrigez et répondez aux commentaires -> demandez de nouvelles
    revues jusqu'à obtention de l'approbation.
- Mettez à jour vos [paramètres de notifications GitHub avec le routage
  personnalisé](https://github.com/settings/notifications/custom_routing) pour
  acheminer les notifications de l'organisation ai-cfia vers votre adresse
  inspection.gc.ca.
- Préférez les commits d'une seule ligne, préfixés par l'issue sur laquelle vous
  travaillez.
  - Exemple : `Issue #19: Introduction Jolan Thomassin`.
- Ne supprimez pas les branches après leur fusion (gardez-les pour référence
  ultérieure).
- Lorsqu'il y a des suggestions, des retours ou des demandes de fonctionnalités
  apparaissent dans une PR et nécessitent un travail supplémentaire en dehors de
  la portée de l'issue actuelle, créez une nouvelle issue pour capturer ce
  travail non trivial et documentez-le comme "travail reporté" dans la PR.

### Gérer les branches divergentes

Lorsque votre branche diverge de la branche principale (en raison de mises à
jour sur la branche principale pendant que vous travaillez sur votre branche),
suivez ces étapes pour rebaser votre branche sur la branche principale. Cela
garantit que l'historique du projet reste propre et linéaire.

```ascii
main      A---B---C---D
               \
branch          E---F---G (divergent)
```

A, B, C, D sont des commits sur la branche principale, et E, F, G sont vos
commits sur votre branche. C et D sont de nouveaux commits ajoutés à la branche
principale après la création de votre branche.

**Étapes pour rebaser et fusionner manuellement**

1. Récupérez la dernière version de la branche principale :

```sh
git fetch origin main
```

2. Rebasez votre branche :

Lancez le processus de rebase pour mettre les modifications de votre branche (E,
F, G) sur l'état actuel de la branche principale (D).

```sh
git rebase origin/main
```

3. Résolvez les conflits (le cas échéant) :

```sh
git add <file>
git rebase --continue
```

Répétez jusqu'à ce que tous les conflits soient résolus et que le rebase soit
terminé.

4. Pousser les modifications :

Comme le rebase réécrit l'historique, vous devrez forcer le push de votre
branche.

```sh
git push --force-with-lease
```

Ce processus garantit que vos modifications maintiennent un historique
linéaire :

```ascii
main      A---B---C---D
                        \
branch                   E'---F'---G' (rebased)
```

#### Configurer Git pour le Rebase automatique

Pour configurer Git afin d'effectuer automatiquement un rebase au lieu de créer
des commits de fusion lors d'un `git pull`, utilisez la commande de
configuration globale suivante :

```sh
git config --global pull.rebase true
```

#### Rebase avec l'extension GitHub pour VScode

1. Ouvrez la palette de commandes (Ctrl+Shift+P).
2. Recherchez "Rebase" et sélectionnez "Git : Pull (Rebase)".
3. Sélectionnez la branche que vous souhaitez rebaser sur la branche principale.
4. Résolvez les conflits, le cas échéant, et poussez vos modifications.
