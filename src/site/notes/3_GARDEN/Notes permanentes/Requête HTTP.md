---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Requête HTTP/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:45.670+01:00","mtime":"2025-09-02T10:33:36.581+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/IA]]","[[3_GARDEN/MOCs/N8N]]"],"source":["Perplexity"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-08-13","aliases":null}}
---

## La note 

Une requête HTTP est une demande envoyée par un client (typiquement un navigateur web) à un serveur pour réaliser une action sur une ressource spécifique. Cette ressource peut être une page web, une image, un fichier, ou des données d'une API.

#### Comment fonctionne une requête HTTP concrètement ?

1. **Initiation côté client** : L’utilisateur interagit, par exemple en tapant une URL, cliquant sur un lien, ou envoyant un formulaire.
    
2. **Envoi de la requête au serveur** : Le client envoie une requête HTTP au serveur, précisant l’action souhaitée à l’aide d'une méthode HTTP (GET, POST, etc.) et l'URL de la ressource.
    
3. **Traitement de la requête par le serveur** : Le serveur reçoit la requête, effectue l’opération demandée (récupération, création, mise à jour, suppression) sur la ressource.
    
4. **Réponse du serveur** : Le serveur renvoie une réponse HTTP incluant un code de statut (200 pour succès, 404 si ressource non trouvée, etc.) et éventuellement des données (ex. une page HTML).
    

#### Les principales méthodes HTTP et leur usage

|Méthode|Fonction principale|Exemple d'usage|Caractéristique clé|
|---|---|---|---|
|**GET**|Récupérer une ressource (données, page)|Charger une page web, récupérer des infos|Idempotente, pas de corps dans la requête, données visibles dans l’URL (ex: ?id=123)|
|**POST**|Envoyer des données pour création ou traitement|Envoyer un formulaire utilisateur|Non idempotente, corps de requête avec données cachées dans la requête|
|**PUT**|Remplacer ou créer une ressource complète|Mettre à jour un objet ou créer une ressource|Idempotente, nécessite une représentation complète de la ressource|
|**PATCH**|Modifier partiellement une ressource|Mettre à jour partiellement une donnée|Non idempotente, plus flexible que PUT|
|**DELETE**|Supprimer une ressource|Supprimer un utilisateur ou un fichier|Idempotente|

#### Détails concrets sur les méthodes GET et POST

- **GET** : Utilisée pour demander des données au serveur. Les paramètres sont envoyés dans l'URL, visibles et donc peu sécurisés. Utile pour charger des pages ou rechercher des informations. Par exemple :  
    `GET /search?query=chat HTTP/1.1`  
    Le serveur renvoie la page correspondant à la recherche "chat".
    
- **POST** : Utilisée pour envoyer des données au serveur, souvent via un formulaire web. Les données sont envoyées dans le corps de la requête, donc non visibles dans l’URL, ce qui est plus sécurisé pour des informations sensibles comme des mots de passe. Par exemple, lors d’une inscription utilisateur.  
    `POST /signup HTTP/1.1` avec corps `{ "username": "Alice", "password": "secret" }`
    

En résumé, une requête HTTP est un échange essentiel entre un client et un serveur sur le web, orchestré par des méthodes HTTP qui définissent la nature de l’action à effectuer sur les ressources disponibles. 

### Avec les API REST
#### Qu'est-ce qu'une API ?

Une **API** (Application Programming Interface) est un ensemble de définitions et de protocoles qui permet à différentes applications logicielles de communiquer entre elles. C'est comme un menu de restaurant : il vous indique ce que vous pouvez commander (les fonctions disponibles) et comment le faire (comment interagir avec elles). L'API gère la commande et vous apporte le plat (la réponse).

#### Qu'est-ce que REST ?

**REST** (Representational State Transfer) est une architecture logicielle qui fournit un ensemble de principes de conception pour les systèmes distribués. Les API qui respectent ces principes sont appelées API RESTful. L'objectif principal de REST est d'améliorer la performance, l'évolutivité, la simplicité et la fiabilité des applications web.

Les principes clés de REST sont :

1. **Client-Serveur** : Le client (par exemple, votre navigateur web) et le serveur (où l'API est hébergée) sont indépendants. Le client n'a pas besoin de connaître la logique métier du serveur, seulement comment interagir avec son API.
2. **Stateless (Sans état)** : Chaque requête du client au serveur doit contenir toutes les informations nécessaires pour comprendre la requête. Le serveur ne doit pas stocker d'informations sur l'état du client entre les requêtes.
3. **Cacheable (Cachable)** : Les réponses des requêtes peuvent être mises en cache pour améliorer les performances, comme la mise en cache de pages web.
4. **Uniform Interface (Interface Uniforme)** : C'est le principe le plus important. Il simplifie l'architecture en rendant les interactions client-serveur uniformes. Cela inclut des sous-contraintes :
    - **Identification des ressources** : Les ressources (données) sont identifiées par des URI (Uniform Resource Identifiers).
    - **Manipulation des ressources via des représentations** : Le client reçoit une représentation de la ressource (par exemple, JSON ou XML) et envoie des représentations pour modifier ou créer des ressources.
    - **Messages auto-descriptifs** : Chaque message contient suffisamment d'informations pour que le client sache comment le traiter.
    - **HATEOAS (Hypermedia As The Engine Of Application State)** : Le serveur fournit des liens hypermédias dans ses réponses, permettant au client de découvrir les actions disponibles et l'état de l'application.
5. **Layered System (Système de couches)** : Un client ne sait pas s'il est directement connecté au serveur final ou à un intermédiaire. Les intermédiaires peuvent fournir des services comme la sécurité ou la mise en cache.

#### Composants d'un appel d'API REST

Un appel d'API REST typique se compose des éléments suivants :

1. **Endpoint (Point de terminaison)** : C'est l'URL spécifique où l'API est accessible. Par exemple : `https://api.exemple.com/utilisateurs/123`.
2. **Méthodes HTTP (Verbes HTTP)** : Indiquent l'action que le client souhaite effectuer sur la ressource. Les plus courantes sont :
    - `GET` : Récupérer des données.
    - `POST` : Créer de nouvelles données.
    - `PUT` : Mettre à jour des données existantes (remplace la ressource complète).
    - `PATCH` : Mettre à jour partiellement des données existantes.
    - `DELETE` : Supprimer des données.
3. **Headers (En-têtes)** : Fournissent des métadonnées sur la requête ou la réponse. Ils peuvent inclure des informations d'authentification, le type de contenu envoyé (`Content-Type`), ou le type de contenu accepté (`Accept`).
4. **Body (Corps de la requête)** : Contient les données envoyées au serveur, principalement avec les méthodes `POST`, `PUT` et `PATCH`. Ces données sont généralement au format JSON ou XML.
5. **Codes de statut HTTP** : Le serveur renvoie un code de statut pour indiquer le résultat de la requête.
    - `2xx` (Succès) : Par exemple, `200 OK`, `201 Created`.
    - `4xx` (Erreur client) : Par exemple, `400 Bad Request`, `401 Unauthorized`, `404 Not Found`.
    - `5xx` (Erreur serveur) : Par exemple, `500 Internal Server Error`.

En résumé, un appel d'API REST est une interaction standardisée entre un client et un serveur, où le client envoie une requête spécifique (Endpoint, Méthode, Headers, Body) et le serveur répond avec des données et un code de statut. 


### Dans N8N

#### Concrètement le nœud http request n8n

**1. Qu'est-ce que le nœud HTTP Request ?**
C'est un nœud fondamental dans n8n qui vous permet de faire des requêtes HTTP à n'importe quelle application ou service disposant d'une API REST. Il est particulièrement utile lorsque n8n ne dispose pas d'un nœud dédié pour l'intégration souhaitée.

**2. Configuration de base :**
*   **Méthode (Method):** Choisissez la méthode HTTP appropriée pour votre requête (GET, POST, PUT, DELETE, PATCH, HEAD, OPTIONS).
*   **URL:** Saisissez l'URL de l'API à laquelle vous souhaitez vous connecter.
*   **Authentification (Authentication):**
    *   **Predefined Credential Type:** Si l'intégration est courante, n8n peut avoir un type d'authentification prédéfini.
    *   **Generic Credentials:** Pour les API moins courantes ou personnalisées, vous pouvez configurer manuellement l'authentification (Basic Auth, OAuth1, OAuth2, Bearer Token, Header, Query Parameter, Custom).
*   **Paramètres de requête (Query Parameters):** Permettent de filtrer les résultats ou d'envoyer des informations via l'URL (ex: `?param1=val1`). Vous pouvez les ajouter sous forme de paires Nom/Valeur ou en JSON.
*   **En-têtes (Headers):** Utilisés pour envoyer des métadonnées avec la requête (ex: `Content-Type: application/json`, `Authorization: Bearer VOTRE_TOKEN`). Configurez-les en paires Nom/Valeur ou en JSON.
*   **Corps de la requête (Body):** Si vous utilisez des méthodes comme POST ou PUT, vous devrez envoyer un corps de requête. Les options incluent :
    *   **Form URLencoded:** Pour les données de formulaire simples.
    *   **Form-Data:** Pour envoyer des fichiers ou des données de formulaire plus complexes.
    *   **JSON:** Très courant pour les API REST.
    *   **n8n Binary File:** Pour envoyer des fichiers binaires.
    *   **Raw:** Pour envoyer du texte brut ou d'autres formats.

**3. Options avancées :**
*   **Array Format:** Gère la manière dont les tableaux sont sérialisés dans les paramètres de requête.
*   **Batching:** Permet de traiter les requêtes par lots.
*   **Ignore SSL Issues:** À utiliser avec prudence, pour ignorer les problèmes de certificat SSL.
*   **Lowercase Headers:** Convertit les noms des en-têtes en minuscules.
*   **Redirects:** Gère les redirections HTTP.
*   **Response settings:** Configure la gestion de la réponse (inclure les en-têtes, le statut, ne jamais générer d'erreur, format de la réponse).
*   **Pagination:** Très utile pour les API qui renvoient de grandes quantités de données et nécessitent des requêtes multiples pour tout récupérer.
*   **Proxy:** Permet d'utiliser un proxy pour la requête.
*   **Timeout:** Définit le délai d'attente pour la réponse.

**4. Utilisation avec des outils IA (Tool-only options):**
Si le nœud HTTP Request est utilisé dans le cadre d'un agent IA, il existe des options pour optimiser la réponse pour les LLM (Large Language Models), en spécifiant le format de la réponse (JSON, HTML, Text) et en permettant de sélectionner, exclure ou tronquer certains champs.

**5. Importation cURL :**
Une fonctionnalité très pratique est la possibilité d'importer une commande cURL. Cela permet de configurer rapidement le nœud si vous disposez déjà d'une requête cURL fonctionnelle.

**6. Exemples d'utilisation :**
*   Scraper des pages web (récupérer le contenu d'une page avec GET).
*   Créer des ressources dans d'autres services (ex: créer un serveur sur DigitalOcean avec POST).
*   Convertir de la parole en texte en utilisant une API de service vocal (ex: Wit.ai avec POST de données binaires).

## Références


> [!example]- Flashcards
> ...




## Liens 




