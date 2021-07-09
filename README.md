# Comment installer Wordpress ?
Voici la manière que j'utilise et que j'ai appris au sein de BeCode.

## 1. Configurez votre environnement

> Avant l'installation, vous devez vérifier si Ubuntu est à jour en faisant "*apt-get*" ou "*apt update*" dans le terminal. 

Il est recommandé d'installer un serveur HTTP, Apache or Nginx. Personnellement, j'utilise Apache.

Nous avons aussi besoin de PHP et de MySQL.

Il y a plusieurs possibilités pour configurer votre environnement et je conseille Docker.

### 1.1. Docker et Installation Wordpress.

Pour mon workshop, je vais utiliser Docker et je vous invite à faire de même mais vous pouvez aussi utiliser XAMPP ou encore LAMP.

Pour l'installer, copiez le dossier "wordpress" ainsi que le fichier "docker-compose" présent dans le repo pour les mettre dans un dossier créé au préalable.

Une fois fait, il faut rentrer "docker-compose build" puis "docker-compose up" dans le terminal (dans le bon dossier). Faites le bien dans cet ordre !

## 2. La base de données et wp-config.php

1. Avant de lancer Wordpress, nous devons créer une base de données.

Vous devez aller lancer [http://localhost:8001](http://localhost:8001)

Puis, ajoutez une nouvelle base de données.

Exemple :

- Nom de base de données : `wordpress`
- Interclassement : `utf8_unicode_ci`

2. Dans votre dossier, ouvrez le fichier `wp-config.php` et changez les informations pour la connexion avec votre BdD. 

Exemple :

```php
// ** MySQL settings - You can get this info from your web host ** //
/** The name of the database for WordPress */
define('DB_NAME', 'firstWordPress');

/** MySQL database username */
define( 'DB_USER', 'root' );

/** MySQL database password */
define( 'DB_PASSWORD', 'root' );

/** MySQL hostname */
define( 'DB_HOST', 'localhost' );

⚠️ docker
/** MySQL hostname */
define( 'DB_HOST', getenv_docker('WORDPRESS_DB_HOST', 'mysql') );

```
3. Si ce n'est pas fait par défaut, renommez le fichier wp-config-sample.php dans wp-config.php

## 3. Terminez l'installation

Dans votre navigateur, allez sur `localhost`.

Si tout s'est bien passé, l'installation de Wordpress va démarrer et vous demander de fournir vos informations, dont la configuration de la base de données :

- Nom de la base de données 
- Nom d'utilisateur de la base de données (par défaut, c'est root)
- Le mot de passe
- L'adresse de la base de données
- Préfixe de la base de données (pas besoin de le changer)

## 4. Terminez l'installation

Vous avez alors créé votre site Wordpress et vous pouvez vous y connecter.