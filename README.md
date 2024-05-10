# dimongo Docker Image MONGOdb
Par [pctronique](https://pctronique.fr/) <br />
Version 1.0.0

<details>
  <summary>Table des matières</summary>
  <ol>
    <li><a href="#Présentation">Présentation</a></li>
    <li><a href="#Import-SGBD">Import SGBD</a></li>
    <li><a href="#Test-version">Test version</a></li>
    <li><a href="#Docker-hub">Docker hub</a></li>
  </ol>
</details>

## Présentation

Pour créer une image docker mongodb à partir du mongodb de docker.
Cette image permet de faire une importation de base de données facilement.
Cette version est utile pour tester son fonctionnement sur des versions de mongodb.

La version :
<ul>
  <li>Mongo:7.0.9</li>
</ul>

> [!NOTE]
> Récupérer l'image du dossier « image ».

## Import SGBD

Pour importer les bases de données :

Le faire a partir d'un fichier « docker-compose.yml » :
```
volumes:
    - ./config/data:/docker-entrypoint-initdata.d:rw
```

<ul>
  <li>Faire une exportation de la base sous format json.</li>
  <li>Placer les fichiers json dans le dossier « config/data » de votre projet.</li>
</ul>

Sans le fichier, en ligne de commande :
```
docker run -v `pwd`/config/data:/docker-entrypoint-initdata -p 27017:27017 Dockerfile
```

## Docker hub

Pour le transmettre sur docker hub, il serait préférable d'avoir une version fixe de l'image.

Remplacer :
```
# variable environnement
ARG VALUE_MONGO_VERSION
ARG DEF_MONGO_VERSION=${VALUE_MONGO_VERSION:-7.0.9}

# config install nodejs
FROM mongo:${DEF_MONGO_VERSION}
```

Par :
```
FROM mongo:7.0.9
```