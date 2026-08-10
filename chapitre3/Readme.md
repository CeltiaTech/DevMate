# Programmez avec Ollama - Chapitre 3 – Choisir automatiquement le meilleur modèle

![1786267493083](images/Readme/1786267493083.png)

Dans les chapitres précédents, nous avons appris à dialoguer avec un LLM, puis à conserver le contexte d’une conversation.

Notre assistant **DevMate** est désormais capable de tenir une discussion. Mais une question se pose rapidement :

*Quel modèle faut-il utiliser ?*

Avec Ollama, il est très facile de changer de modèle. On peut passer d’un modèle généraliste à un modèle spécialisé dans le code en modifiant simplement un paramètre.

C’est une force… mais aussi une décision que l’on ne devrait pas demander à l’utilisateur.

C’est à l’application de choisir le modèle le plus adapté.

### Il n’existe pas de modèle parfait

Chaque modèle possède ses points forts.

Certains excellent dans la génération de code.

D’autres sont très efficaces pour résumer un document, traduire un texte ou répondre à des questions générales.

On pourrait bien sûr utiliser le même modèle pour toutes les tâches.

Mais ce serait un peu comme utiliser un marteau pour tous les travaux : cela fonctionne parfois, mais ce n’est pas toujours le meilleur outil.

Notre objectif est donc simple :

**choisir automatiquement le modèle le plus adapté à la demande de l’utilisateur.**

### Une première stratégie

Pour notre assistant DevMate, nous allons commencer avec quelques règles simples.

* 💻 **Développement et programmation** → qwen3-coder
* 🌍 **Traduction** → gemma3
* 📄 **Résumé de documents** → phi4-mini
* 💬 **Conversation générale** → llama3.2

Cette liste n’a rien de figé.

Vous pourrez naturellement la faire évoluer en fonction des modèles installés sur votre machine.

L’idée est simplement d’ajouter une première couche d’intelligence à notre assistant.

### Une fonction de sélection

Créons une fonction chargée de déterminer quel modèle utiliser.
![1786267353691](images/Readme/1786267353691.png)
Cette approche repose simplement sur la présence de quelques mots-clés.

Ce n’est évidemment pas une solution parfaite.

Mais elle suffit largement pour comprendre le principe.

Et surtout, elle permet de rendre notre application plus intelligente sans ajouter de complexité.

### Intégrer la sélection dans DevMate

Il ne reste plus qu’à utiliser cette fonction avant d’interroger Ollama.
![1786267399973](images/Readme/1786267399973.png)

À présent, l’utilisateur ne choisit plus le modèle.

Il pose simplement sa question.

DevMate se charge de sélectionner le plus approprié.

Cette séparation est importante : l’utilisateur exprime ​**son intention**​, l’application décide ​**de la meilleure manière d’y répondre**​.

### Peut-on aller plus loin ?

Absolument.

La fonction choose\_model() pourrait prendre en compte de nombreux critères :

* la longueur de la question ;
* le nombre de messages déjà échangés ;
* la mémoire disponible sur la machine ;
* la vitesse de réponse attendue ;
* ou encore les capacités propres à chaque modèle.

On pourrait même demander… à un petit LLM de déterminer quel autre modèle devra traiter la requête.

C’est ce que l’on appelle parfois un **routeur de modèles** (​*model router*​).

Les grandes plateformes d’IA utilisent largement ce type de mécanisme pour optimiser les coûts et les performances.

### En résumé

Notre assistant est désormais capable de choisir automatiquement le modèle le plus adapté à chaque demande.

L’utilisateur n’a plus besoin de connaître les différents modèles installés ni de décider lequel utiliser. Cette logique appartient désormais à l’application, qui peut évoluer au fil du temps en ajoutant de nouvelles règles ou en prenant en compte d’autres critères.

Nous avons ainsi franchi une nouvelle étape dans la construction de **DevMate**. Notre assistant sait maintenant conserver le contexte d’une conversation et sélectionner le modèle le plus pertinent en fonction de la tâche à accomplir.

Mais il reste encore un point à améliorer.

Lorsqu’une question est envoyée à Ollama, notre application attend que le modèle ait terminé de générer toute sa réponse avant de l’afficher. Pour les réponses les plus longues, cette attente peut donner l’impression que l’application ne fait rien.

Dans le prochain chapitre, nous verrons comment utiliser le **streaming** pour afficher les réponses au fur et à mesure de leur génération, et offrir à DevMate une expérience utilisateur beaucoup plus fluide et réactive.![1786343115401](images/Readme/1786343115401.png)

