# Redis Hawk Monitoring

**Version :** 2.0  
**Auteur :** Aubin MIENANZAMBI  
**Licence :** GPLv2 ou supérieure

---

## Description

**Redis Hawk Monitoring** est un plugin WordPress avancé conçu pour surveiller et gérer efficacement votre cache Redis. Grâce à une interface intuitive et complète, ce plugin vous offre une vue d'ensemble en temps réel des performances de votre serveur Redis, vous permettant ainsi d'optimiser l'utilisation du cache et de maintenir la santé globale de votre environnement WordPress.

### Fonctionnalités principales :

- **Tableau de bord en temps réel :** Visualisez les statistiques clés de Redis, telles que l'utilisation de la mémoire, le nombre de connexions clientes, le taux d'éviction des clés, et plus encore.
- **Gestion du cache :** Videz le cache Redis en un seul clic pour garantir la fraîcheur des données mises en cache.
- **Alertes configurables :** Recevez des notifications personnalisées en cas d'utilisation excessive de la mémoire ou de connexions simultanées élevées.
- **Compatibilité multisite :** Gérez efficacement le cache Redis pour plusieurs sites hébergés sur le même serveur en utilisant des préfixes uniques pour chaque site.
- **Fallback intelligent :** En cas d'indisponibilité de Redis, le plugin bascule automatiquement vers un cache interne non persistant, assurant ainsi la continuité de votre site sans interruption.
- **Interface utilisateur ergonomique :** Profitez d'une interface claire et facile à naviguer, adaptée tant aux administrateurs novices qu'aux utilisateurs avancés.

---

## Installation

1. **Téléchargement :**
   - Téléchargez le plugin **Redis Hawk Monitoring** depuis le répertoire officiel des plugins WordPress ou depuis votre espace de développement.

2. **Installation via l'admin WordPress :**
   - Accédez à votre tableau de bord WordPress.
   - Naviguez vers `Extensions` > `Ajouter`.
   - Cliquez sur `Téléverser une extension`.
   - Sélectionnez le fichier ZIP du plugin et cliquez sur `Installer maintenant`.
   - Une fois l'installation terminée, cliquez sur `Activer l'extension`.

3. **Configuration :**
   - Après activation, accédez au menu `Redis Hawk` dans votre tableau de bord WordPress.
   - Suivez les instructions pour configurer les paramètres Redis, notamment l'hôte, le port, le préfixe, et la base de données.

4. **Assurez-vous que Redis est installé et opérationnel :**
   - **Avant d'utiliser Redis Hawk Monitoring, assurez-vous que Redis est déjà installé et fonctionnel sur votre serveur.**
   - Si Redis rencontre des problèmes, vous pouvez revenir au système de cache par défaut en **supprimant simplement le fichier `object-cache.php`** de votre répertoire `wp-content`.

---

## Configuration

Pour configurer Redis avec WordPress et Redis Hawk Monitoring, suivez ces étapes :

1. **Modifier le fichier `wp-config.php` :**
   - Ajoutez les lignes suivantes à votre fichier `wp-config.php` :
     ```php
     // Active la mise en cache WordPress
     define('WP_CACHE', true);
     
     // Configuration Redis
     define('WP_REDIS_HOST', '127.0.0.1');
     define('WP_REDIS_PORT', 6379);
     define('WP_REDIS_PREFIX', 'nomsite_'); // Remplacez 'nomsite_' par un préfixe unique pour chaque site
     define('WP_REDIS_DATABASE', 0); 
     ```
   - **Important :** Remplacez `'nomsite_'` par un préfixe unique correspondant au nom de votre site pour éviter toute confusion, surtout si vous hébergez plusieurs sites sur le même serveur.

2. **Vérifier la présence de `object-cache.php` :**
   - Assurez-vous que le fichier `object-cache.php` est bien présent dans le répertoire `wp-content`. Ce fichier est essentiel pour que WordPress utilise Redis comme système de cache objet.

3. **Configurer Redis Hawk Monitoring :**
   - Accédez au menu `Redis Hawk` dans votre tableau de bord WordPress.
   - Configurez les paramètres Redis en fonction de votre environnement (hôte, port, préfixe, etc.).
   - Configurez les alertes selon vos préférences pour être informé des anomalies ou des utilisations excessives des ressources.

---

## Utilisation

### Tableau de bord Redis Hawk :

- **Vue d'ensemble :** Accédez au tableau de bord Redis Hawk pour visualiser les statistiques en temps réel de votre serveur Redis.
- **Statistiques clés :** Observez l'utilisation de la mémoire, les connexions actives, les opérations de cache, et plus encore.
- **Gestion du cache :** Utilisez le bouton `Vider le cache` pour purger rapidement toutes les données mises en cache dans Redis.

### Alertes et notifications :

- **Configuration des alertes :** Définissez des seuils pour recevoir des notifications en cas d'utilisation excessive de la mémoire ou de connexions simultanées élevées.
- **Réactivité :** Restez informé des performances de votre cache Redis pour intervenir rapidement en cas de besoin.

### Compatibilité multisite :

- **Préfixes uniques :** Attribuez des préfixes uniques pour chaque site dans un environnement multisite afin d'éviter les conflits de clés dans Redis.
- **Gestion centralisée :** Surveillez et gérez le cache Redis de tous vos sites depuis une interface centralisée.

---

## FAQ

### 1. **Redis Hawk Monitoring peut-il fonctionner sans Redis installé ?**
Non, le plugin nécessite que Redis soit installé et configuré sur votre serveur pour fonctionner correctement. En cas d'indisponibilité de Redis, le plugin bascule automatiquement vers un cache interne non persistant, mais pour une performance optimale, Redis doit être opérationnel.

### 2. **Comment personnaliser le préfixe Redis pour chaque site dans un environnement multisite ?**
Lors de la configuration dans `wp-config.php`, définissez un préfixe unique pour chaque site en modifiant la constante `WP_REDIS_PREFIX`. Par exemple :
```php
define('WP_REDIS_PREFIX', 'mon_site_');

