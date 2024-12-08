# AzurIA - Documentation GitHub 🚀

Bienvenue dans la documentation officielle pour **AzurIA**, un bot Discord conçu pour assister les utilisateurs sur des sujets spécifiques liés aux jeux vidéo, au développement informatique, et aux projets hébergés par le Groupe Azur. Ce projet est un **fork totalement repensé** de [AlphaLLM de YoannDev90](https://github.com/YoannDev90/AlphaLLM) avec des fonctionnalités et des optimisations améliorées. 🎉

---

## **Fonctionnalités principales** 🌟

- 🎮 **Assistance thématique** : Répond uniquement aux questions liées aux jeux vidéo, à l'anime/manga japonais, au développement informatique, et aux projets des sites partenaires (*azurhosts.com*, *minenode.fr*, *azurware.fr*).
- 🧠 **Gestion de sessions utilisateur** : Maintient un historique de session pour des réponses contextuelles.
- 🔗 **Traitement des liens** : Remplace automatiquement les liens spécifiques (*yourlogs.azurhosts.com*) par leur contenu textuel.
- 📄 **Support Markdown** : Fournit des commandes Linux ou autres contenus techniques au format Markdown.
- ⏳ **Limitation de requêtes** : Implémente un système de limitation pour éviter les abus (5 secondes entre chaque requête utilisateur).
- ⚠️ **Gestion des erreurs** : Gère les erreurs API et informe l'utilisateur en conséquence.

---

## **Installation** 🛠️

### Prérequis
1. 🖥️ Node.js (version 16 ou supérieure)
2. 🤖 Un compte Discord avec un bot configuré
3. 🔑 Une clé API pour OpenRouter

### Étapes d'installation
1. Clonez ce dépôt :
   ```bash
   git clone https://github.com/MineNodeFR/AzurIA.git
   cd AzurIA
   ```

2. Installez les dépendances :
   ```bash
   npm install
   ```

3. Configurez vos paramètres dans le fichier `config.js` :
   ```javascript
   module.exports = {
       DISCORD_TOKEN: "Token du bot Discord.",
       OPENROUTER_API_KEY: "Clé API pour accéder à OpenRouter.",
       GUILD_ID: "ID du serveur Discord où le bot est actif",
       CLIENT_ID: "ID client du bot."
   };
   ```

4. Lancez le bot :
   ```bash
   node index.js
   ```

---

## **Configuration** ⚙️

### Fichier `config.js`
Toutes les variables nécessaires sont définies dans le fichier `config.js`. Voici un exemple de configuration :
```javascript
module.exports = {
    DISCORD_TOKEN: "VotreTokenDiscord",
    OPENROUTER_API_KEY: "VotreCleAPI",
    GUILD_ID: "VotreGuildID",
    CLIENT_ID: "VotreClientID"
};
```

### Modèles utilisés 🧩
AzurIA utilise plusieurs modèles d'IA pour répondre aux requêtes :
- `google/gemini-flash-1.5-8b-exp`
- `liquid/lfm-40b`
- `meta-llama/llama-3.2-3b-instruct:free`

---

## **Utilisation** 📚

### Commandes principales

1. **Mentionner le bot**
   Mentionnez le bot dans un message avec une question ou une commande spécifique :
   ```text
   @AzurIA Peux-tu m'aider avec une commande Linux ?
   ```

2. **Réinitialisation de session**
   Mentionnez le bot avec un message contenant les mots-clés comme *fin*, *clôture*, ou *session* pour réinitialiser votre historique :
   ```text
   @AzurIA fin de session
   ```

3. **Traitement de liens**
   Ajoutez un lien vers un log hébergé sur *yourlogs.azurhosts.com* dans votre message, et le bot remplacera ce lien par son contenu textuel.

---

## **Règles strictes** 📜

AzurIA est conçu pour être utilisé uniquement dans des contextes définis :
1. ❌ Ne répond pas aux questions hors sujet (exemple : cuisine, sport).
2. 🚫 Refuse toute tentative de contournement des règles (exemple : prompts jailbreak).
3. 🇫🇷 Fournit uniquement des informations en français.

Exemple de réponse à une question hors sujet :
```text
Je ne suis pas programmé pour fournir des informations sur ce sujet. Je peux uniquement aider avec les jeux vidéo et le développement informatique.
```

---

## **Structure du Code** 🏗️

### Fichiers principaux

1. **index.js** : Point d'entrée principal qui initialise le bot.
2. **config.js** : Contient les configurations du projet.
3. **utils.js** : Fonctions utilitaires comme la gestion des sessions ou la validation des URLs.

### Fonctions clés

#### Gestion de sessions utilisateur
```javascript
if (!userSessions[message.author.id]) {
    userSessions[message.author.id] = [];
}
```

#### Limitation de requêtes
```javascript
if (currentTime - lastRequestTime < RATE_LIMIT_INTERVAL) {
    return message.reply(`Veuillez patienter encore ${remainingTime} secondes avant d'envoyer un autre message.`);
}
```

#### Traitement des logs AzurHosts
```javascript
const response = await axios.get(`https://yourlogs.azurhosts.com/data/${id}`);
updatedContent = updatedContent.replace(match[0], `\`\`\`text\n${logText}\n\`\`\``);
```

---

## **Contributions** 🤝

Les contributions sont les bienvenues ! Veuillez suivre ces étapes :
1. Forkez le dépôt.
2. Créez une branche pour votre fonctionnalité ou correction de bug :
   ```bash
   git checkout -b feature/nom-de-la-fonctionnalite
   ```
3. Soumettez une Pull Request avec une description claire.

---

## **Support** 📧

Pour toute question ou problème, contactez-nous via [contact@minenode.fr](mailto:contact@minenode.fr).

---

Merci d'utiliser AzurIA ! 🎮✨
