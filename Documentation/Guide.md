# Documentation technique d'installation

## Installation du JDK 11 sous Windows

Télécharger la dernière version du [JDK 11](https://www.oracle.com/java/technologies/javase-downloads.html) sur le site officiel d'Oracle.

Une fois téléchargé, exécuter le fichier d'installation (.exe) et suivre les instructions pour installer le JDK 11.

### Configurer les variables d'environnement

Pour que le JDK 11 soit accessible depuis n'importe quel répertoire, il est nécessaire de configurer les variables d'environnement.

Ouvrir le **Panneau de configuration** (ou **Système**) > **Système et sécurité** > **Système** > **Paramètres avancés du système** > **Variables d'environnement**.

Dans la section **Variables d'environnement du système**, cliquer sur **Nouvelle**.

* Pour le nom, entrer `JAVA_HOME`.
* Pour la valeur, entrer le chemin d'accès où a été installé le JDK 11 (par exemple `C:\Program Files\Java\jdk-11.0.17`).
* Cliquer sur **OK** pour valider la modification.

Ensuite, cliquer sur **Modifier** en face de la variable `Path`.

* Cliquer sur **Nouveau**.
* Entrer le chemin d'accès vers le dossier `bin` du JDK 11 (par exemple `C:\Program Files\Java\jdk-11.0.17\bin`).
* Cliquer sur **OK** pour valider la modification.

Enfin, cliquer sur **OK** pour fermer la fenêtre des variables d'environnement.

Pour vérifier que le JDK 11 est bien installé et que les variables d'environnement sont configurées correctement, ouvrir une invite de commande et taper :

    java -version
    
## Installation de IntelliJ Ultimate

Télécharger la dernière version d'[IntelliJ Ultimate](https://www.jetbrains.com/idea/download/#section=windows) sur le site officiel de JetBrains.

Une fois téléchargé, exécuter le fichier d'installation (.exe) et suivre les instructions pour installer IntelliJ Ultimate.

### Configurer IntelliJ Ultimate

Ouvrir IntelliJ Ultimate.

* Sélectionner le dossier `C:\Program Files\JetBrains\IntelliJ IDEA Ultimate 2021.1.1` comme dossier de configuration.
* Configurer le JDK 11 comme JDK par défaut.

#### Activer IntelliJ Ultimate

Pour utiliser IntelliJ Ultimate (version payante), il faudra activer une licence en se connectant avec un compte JetBrains ou en entrant une clé de licence.

## Configuration de Maven

Télécharger la dernière version de [Maven](https://maven.apache.org/download.cgi) sur le site officiel.

Une fois téléchargé, extraire le contenu du zip dans le dossier `C:\Program Files\Maven`.

### Configurer les variables d'environnement

Ajouter le chemin d'accès au dossier `bin` de Maven dans les variables d'environnement.

* Ouvrir le panneau de configuration des variables d'environnement
* Créer une nouvelle variable d'environnement `M2_HOME` avec comme valeur le chemin d'accès au dossier `C:\Program Files\Maven`
* Ajouter le chemin d'accès au dossier `bin` de Maven dans la variable d'environnement `PATH`.

Pour tester si Maven est bien configuré, ouvrir une invite de commande et taper la commande suivante :

    mvn -version

Pour compiler le projet sans exécuter les tests, entrer cette commande dans le terminal :

    mvn clean install -DskipTests

## Configuration du serveur applicatif Tomcat 9.0.80

Télécharger la dernière version de [Tomcat](https://tomcat.apache.org/download-90.cgi) sur le site officiel.

Une fois téléchargé, extraire le contenu du zip dans le dossier `C:\Program Files\Apache\apache-tomcat-9.0.80`.

### Configurer Tomcat dans IntelliJ

Ouvrir IntelliJ, puis dans le menu `File` > `Settings` > `Build, Execution, Deployment` > `Applications Servers`, cliquer sur le bouton `+` en haut à droite de la fenêtre, puis sélectionner `Tomcat Server` et le dossier `C:\Program Files\Apache\apache-tomcat-9.0.80` comme dossier d'installation de Tomcat.

### Lancement du serveur applicatif

Ouvrir le menu `Run` > `Edit Configurations`, cliquer sur le bouton `+`, puis sélectionner la configuration `Tomcat Server`.

Dans la section `Deployment` > `Deploy at the server startup`,
cliquer sur le bouton `+`, puis sur `Artifact`.

Sélectionner l'artifact `:war:exploded` à déployer.

Le chemin vers le **contexte de l'application** est `/_00_ASBank2023`.

Cliquer enfin sur `Appliquer`, puis `OK` pour valider la configuration.

Pour lancer le serveur applicatif, ouvrir le menu `Run`, puis cliquer sur `Run Tomcat 9.0.80`, ou l'ouvrir grâce au raccourci clavier `CTRL`+`F5` sur Windows.

Une fois le serveur démarré, ouvrir le navigateur et taper l'adresse suivante pour vérifier que Tomcat fonctionne : 
    http://localhost:8080/_00_ASBank2023/
