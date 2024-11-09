
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

### Accéder à la base de données MySQL depuis IntelliJ

Dans IntelliJ, ouvrez l'onglet **Database** dans le panneau latéral.
Cliquez sur le bouton `+` et sélectionnez **Data Source** > **MySQL**.
Entrez les informations de connexion suivantes :
- **Host** : `localhost`
- **Port** : `3306`
- **Database** : `bankiut`
- **User** : `root` (ou `newuser` si vous en avez créé un autre)
- **Password** : `root` (ou le mot de passe de `newuser`)
  Testez la connexion puis enregistrez-la.
  Refaite la même étape en modifiant les informations avec la base de donnée bankiuttest, tester la connexion puis enregistrez-la

**Pensez bien à adapter les fichiers  XML en fonction de votre User et de votre Password.**

### Importer les tables dans IntelliJ

Accédez à l'onglet **Database**.
Faites un clic droit sur la première base de données (bankiut), puis sélectionnez
**SQL Script** > **Run SQL Script**.
Dans la fenêtre qui s'ouvre, sélectionnez le fichier `dumpSQL.sql` qui se trouve dans le dossier `script` de votre projet.
Validez pour lancer le script et importer les tables dans votre base de données.
Répéter la même étape poour la seconde base de données (bankiuttest) avec le fichier `dumpSQL_JUnitTest.sql` qui se trouve aussi dans le dossier `script`.


# Votre application est maintenant fonctionnelle et prête à être lancée !

## Version macOS/Linux

### Installation du JDK 11

#### macOS

Téléchargez le JDK 11 depuis [Oracle](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html).
Installez-le en ouvrant le fichier `.dmg` et en suivant les instructions.

### Configurer les variables d'environnement

Configurez les variables d'environnement en ajoutant ces lignes à votre fichier `~/.bash_profile` ou `~/.zshrc` (selon le shell que vous utilisez) :
   ```bash
   export JAVA_HOME=$(/usr/libexec/java_home -v 11)
   export PATH=$JAVA_HOME/bin:$PATH
   ```
   Ensuite, rechargez le fichier avec la commande :
   ```bash
   source ~/.bash_profile  # ou ~/.zshrc si vous utilisez zsh
   ```
Vérifiez que le JDK 11 est bien configuré en exécutant :
   ```bash
   java -version
   ```

#### Linux

Installez le JDK 11 via le gestionnaire de paquets :
   ```bash
   sudo apt update
   sudo apt install openjdk-11-jdk
   ```

### Configurer les variables d'environnement

Configurez les variables d'environnement en ajoutant ces lignes à votre fichier `~/.bashrc` :
   ```bash
   export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
   export PATH=$JAVA_HOME/bin:$PATH
   ```
   Rechargez le fichier avec la commande :
   ```bash
   source ~/.bashrc
   ```

Vérifiez l'installation :
   ```bash
   java -version
   ```

## Installation d'IntelliJ Ultimate

Télécharger la dernière version d'[IntelliJ Ultimate](https://www.jetbrains.com/idea/download/#section=mac) sur le site officiel de JetBrains.

#### Installation sur macOS
Une fois téléchargé, ouvrez le fichier `.dmg` et glissez IntelliJ dans le dossier `Applications`.
Lancez IntelliJ Ultimate depuis le dossier `Applications`.

#### Installation sur Linux
Téléchargez l'archive `.tar.gz` depuis le site officiel.
Ouvrez un terminal et déplacez-vous dans le répertoire où vous avez téléchargé l'archive :
   ```bash
   tar -xzf ideaIU-*.tar.gz -C /opt/
   ```
Pour lancer IntelliJ, exécutez :
   ```bash
   /opt/idea-IU-*/bin/idea.sh
   ```

### Configurer IntelliJ pour utiliser le JDK 11

Ouvrez IntelliJ et allez dans **File** > **Project Structure** > **SDKs**.
Ajoutez le chemin du JDK 11 :
   - Pour macOS, cela pourrait être `/Library/Java/JavaVirtualMachines/jdk-11.0.17.jdk/Contents/Home`.
   - Pour Linux, cela pourrait être `/usr/lib/jvm/java-11-openjdk-amd64`.

#### Activer IntelliJ Ultimate

Pour utiliser IntelliJ Ultimate (version payante), il faudra activer une licence en se connectant avec un compte JetBrains ou en entrant une clé de licence.

## Installation de Maven

### macOS

Installez Maven via Homebrew :

   - macOS :
     ```bash
     brew install maven
     ```

     
### Configurer les variables d'environnement

Configurez les variables d'environnement en ajoutant ces lignes à votre fichier `~/.bash_profile` ou `~/.zshrc` (selon le shell que vous utilisez) :
   ```bash
	export M2_HOME="/usr/local/apache-maven-3.9.9"
	export PATH=$M2_HOME/bin:$PATH
   ```
   Ensuite, rechargez le fichier avec la commande :
   ```bash
   source ~/.bash_profile  # ou ~/.zshrc si vous utilisez zsh
   ```
Vérifiez l'installation en exécutant :
   ```bash
   mvn -version
   ```
   
### Linux

Installez Maven via le gestionnaire de paquets :

   - Linux :
     ```bash
     sudo apt install maven
     ```

### Configurer les variables d'environnement

Configurez les variables d'environnement en ajoutant ces lignes à votre fichier `~/.bashrc` :
   ```bash
	export M2_HOME="/usr/local/apache-maven-3.9.9"
	export PATH=$M2_HOME/bin:$PATH
   ```
   Rechargez le fichier avec la commande :
   ```bash
   source ~/.bashrc
   ```

Vérifiez l'installation :
   ```bash
   mvn -version
   ```

## Installation et Configuration de Tomcat 9

### macOS/Linux

Téléchargez [Tomcat 9](https://tomcat.apache.org/download-90.cgi).
Décompressez l'archive dans votre dossier `Applications` (macOS) ou `/opt/` (Linux) :
   ```bash
   tar xzf apache-tomcat-9.0.94.tar.gz -C ~/Applications  # Pour macOS
   tar xzf apache-tomcat-9.0.94.tar.gz -C /opt/            # Pour Linux
   ```

Vérifiez que Tomcat est correctement installé en naviguant dans le dossier `bin` de Tomcat et en exécutant le script de démarrage :
   ```bash
   cd ~/Applications/apache-tomcat-9.0.94/bin
   ./startup.sh
   ```

Accédez à Tomcat en ouvrant un navigateur et en visitant :
   ```
   http://localhost:8080
   ```

### Configurer Tomcat dans IntelliJ

Ouvrez IntelliJ et allez dans **File** > **Settings** > **Application Servers**.

Ajoutez un serveur Tomcat et spécifiez

Assurez-vous de sélectionner l'option **war:exploded** et de configurer le contexte avec `/00_ASBank2023`.

Ouvrir le menu `Run` > `Edit Configurations`, cliquer sur le bouton `+`, puis sélectionner le chemin d'installation de Tomcat (par exemple `~/Applications/apache-tomcat-9.0.94` sur macOS ou `/opt/apache-tomcat-9.0.94` sur Linux).

Dans la section `Deployment` > `Deploy at the server startup`,
cliquer sur le bouton `+`, puis sur `Artifact`.

Sélectionner l'artifact `:war:exploded` à déployer.

Le chemin vers le **contexte de l'application** est `/_00_ASBank2023`.

Cliquer enfin sur `Appliquer`, puis `OK` pour valider la configuration.

Pour lancer le serveur applicatif, ouvrir le menu `Run`, puis cliquer sur `Run Tomcat 9.0.80`.

Une fois le serveur démarré, ouvrir le navigateur et taper l'adresse suivante pour vérifier que Tomcat fonctionne : 
    http://localhost:8080/_00_ASBank2023/

## Configuration de la Base de Données MySQL

### Installer MySQL

#### macOS

Installez MySQL via Homebrew :
   ```bash
   brew install mysql
   ```

Démarrez le serveur MySQL :
   ```bash
   brew services start mysql
   ```

#### Linux

Installez MySQL via le gestionnaire de paquets :
   ```bash
   sudo apt update
   sudo apt install mysql-server
   ```

Démarrez le serveur MySQL :
   ```bash
   sudo systemctl start mysql
   ```

### Configurer MySQL

Connectez-vous à MySQL avec l'utilisateur `root` :
   ```bash
   mysql -u root -p
   ```

 Créez la base de données pour l'application :
   ```sql
   CREATE DATABASE bankiut;
   ```

Créez la base de données test pour l'application :
   ```sql
   CREATE DATABASE bankiuttest;
   ```

### Accéder à la base de données MySQL depuis IntelliJ

 Dans IntelliJ, ouvrez l'onglet **Database** dans le panneau latéral.
 Cliquez sur le bouton `+` et sélectionnez **Data Source** > **MySQL**.
 Entrez les informations de connexion suivantes :
   - **Host** : `localhost`
   - **Port** : `3306`
   - **Database** : `bankiut`
   - **User** : `root` (ou `newuser` si vous en avez créé un autre)
   - **Password** : `root` (ou le mot de passe de `newuser`)
 Testez la connexion puis enregistrez-la.
Refaite la même étape en modifiant les informations avec la base de donnée bankiuttest, tester la connexion puis enregistrez-la 

**Pensez bien à adapter les fichiers  XML en fonction de votre User et de votre Password.**

 ### Importer les tables dans IntelliJ

Accédez à l'onglet **Database**.
 Faites un clic droit sur la première base de données (bankiut), puis sélectionnez 
**SQL Script** > **Run SQL Script**.
 Dans la fenêtre qui s'ouvre, sélectionnez le fichier `dumpSQL.sql` qui se trouve dans le dossier `script` de votre projet.
 Validez pour lancer le script et importer les tables dans votre base de données.
 Répéter la même étape poour la seconde base de données (bankiuttest) avec le fichier `dumpSQL_JUnitTest.sql` qui se trouve aussi dans le dossier `script`.

# Votre application est maintenant fonctionnelle et prête à être lancée !

---
