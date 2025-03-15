# NETFIX
# français
Objectifs
Imaginez un endroit où vous pourriez demander à quelqu'un de réparer votre bidet et de peindre les murs de votre maison. Et tant qu'à faire, le ménage serait bien pratique. Dans ce projet, vous contribuerez à la création d'un site web qui vous permettra de réaliser tout cela et bien plus encore.

Ce site web est encore en cours de création ; toutes les fonctionnalités ne sont donc pas disponibles. Vous allez implémenter certaines des fonctionnalités manquantes.

Sachez également que le site web est développé avec Django, un framework Python pour le développement web. Vous pouvez en apprendre davantage sur ce framework sur son site web . Vous utiliserez Python ; soyez donc attentif à l'indentation. De plus, ce projet a été développé avec v3.1.14Django. Si vous rencontrez des difficultés pour l'exécuter, veuillez vérifier votre version actuelle de Django et apporter les modifications nécessaires.

Instructions
Le site Web doit contenir deux types d'utilisateurs :

Entreprise : capable de créer de nouveaux services
Client : qui peut demander des services existants
Les deux utilisateurs doivent pouvoir s'inscrire et se connecter. Pour se connecter, il suffit de saisir son adresse e-mail et son mot de passe. Cependant, pour s'inscrire, chaque type d'utilisateur doit fournir des informations différentes :

Client:
e-mail
mot de passe
confirmation du mot de passe
nom d'utilisateur
date de naissance
Entreprise:
e-mail
mot de passe
confirmation du mot de passe
nom d'utilisateur
domaine de travail
Chaque utilisateur doit avoir une adresse e-mail et un nom d'utilisateur uniques. Ainsi, lors de son inscription, un utilisateur doit être averti si son adresse e-mail et/ou son nom d'utilisateur ont déjà été enregistrés.

Chaque utilisateur doit disposer de son propre profil, où ses informations doivent être affichées (à l'exception du mot de passe, bien sûr). S'il s'agit d'un client, tous les services précédemment demandés doivent également être affichés. S'il s'agit d'un profil d'entreprise, les services proposés doivent également y figurer, en plus de ses informations personnelles.

L' field of workattribut des entreprises limitera le type de services qu'elles peuvent fournir. Il field of workne doit accepter que les valeurs suivantes :

Climatiseur
Tout en un
Charpenterie
Électricité
Jardinage
Machines domestiques
Ménage
Design d'intérieur
Serrures
Peinture
Plomberie
Chauffe-eau
Une Carpentryentreprise ne peut proposer que des services de menuiserie, tout comme une Housekeepingentreprise ne peut proposer que des services d'entretien ménager. Cependant, les All in Oneentreprises peuvent proposer tout type de services. Mais que comprend un service ? Un service doit inclure :

nom
description
domaine (peut avoir les mêmes catégories de champs que les entreprises, sauf que vous ne pouvez pas avoir un service Tout en un)
prix par heure
date de création (cet attribut devrait automatiquement prendre une valeur lors de la création d'un service)
Le site web devrait comporter une page présentant les services les plus demandés. Il devrait également comporter une page présentant chaque service par ordre de création (le dernier créé en premier) et une page pour chaque catégorie de services, affichant les services disponibles pour cette catégorie.

Chaque service doit disposer de sa propre page, sur laquelle doivent être affichées les informations ci-dessus, ainsi que le nom de l'entreprise qui le fournit. L'utilisateur doit pouvoir consulter chaque service de cette entreprise en cliquant sur le nom affiché pour accéder à son profil.

Une fois qu'un service est créé par une entreprise, chaque utilisateur y a accès. Seuls les clients peuvent demander un service en indiquant le addresslieu et le temps de traitement service time(en heures). Lorsqu'un client demande un service, celui-ci est ajouté à la liste des services déjà demandés. Dans cette liste, pour chaque service demandé, le client peut consulter le nom du service, le champ du service, le coût calculé, la date de la demande et l'entreprise qui l'a fourni.

Vous pouvez consulter cette vidéo pour voir ce qui est attendu de votre projet.

Django
Maintenant que vous connaissez le projet, nous allons vous expliquer l'architecture du système de fichiers. Un projet Django est organisé autour d'un dossier principal et de différentes applications.

Lors du démarrage d'un nouveau projet Django (avec la commande django-admin startproject <// name of project \\>), le dossier principal (portant le même nom que le projet) et un fichier nommé manage.pyget sont créés. Ce fichier permet d'exécuter diverses commandes. Les plus courantes sont :

python3 manage.py runserver-> exécute un serveur sur le port 8000 par défaut et lui sert votre projet.
python3 manage.py startapp <// name of app \\>-> crée une application, en d'autres termes, crée un répertoire avec la plupart des fichiers nécessaires à une application.
python3 manage.py makemigrationset python3 manage.py migrate-> ces deux commandes sont toujours complémentaires. Nous les utilisons pour déclarer les modifications apportées à la base de données Django (généralement dans le models.pyfichier de chaque application).
python3 manage.py createsuperuser-> crée un super utilisateur (admin) qui peut accéder et modifier les informations de la base de données Django (accessible dans l'url localhost:8000/admin).
python3 manage.py-> pour obtenir une liste de toutes les commandes disponibles.
Notez que nous utilisons la commande python3. Vous pouvez simplement l'utiliser, pythonmais vous devez avoir installé la version 3.0 ou supérieure.

Chaque application est généralement liée à un aspect différent du projet. Par exemple, dans ce projet, il y a trois applications :

services : gère les fonctionnalités essentielles liées aux services (création de services, affichage de services, demande de service...)
utilisateurs : gère les fonctionnalités essentielles liées aux utilisateurs (inscription utilisateur, profil utilisateur, connexion utilisateur...)
main : gère les informations communes à tout le projet (page d'accueil, barre de navigation, page de déconnexion...)
Par défaut, au démarrage d'une application, Django crée plusieurs fichiers très utiles au développement d'un site web. Ceux auxquels nous consacrons le plus de temps sont :

models.py-> où vous pouvez ajouter des objets et définir leurs attributs dans la base de données Django
views.py-> où vous pouvez manipuler le backend d'une page Web sur le projet
En plus de ces deux fichiers, en règle générale, d'autres fichiers sont créés manuellement :

urls.py-> Ici, vous pouvez spécifier les URL de votre projet et les associer à une vue (à partir du views.pyfichier) afin d'afficher une page web. Par exemple, l'URL profile/est associée à la vue views.ProfileView.
forms.py-> Ici, vous pouvez créer vos formulaires à utiliser dans votre views.pyfichier. Par exemple, vous pouvez créer un formulaire de connexion par défaut à utiliser dans LoginViewle views.pyfichier.
Nous créons généralement un dossier pour stocker les modèles (au format HTML). Ce dossier suit généralement la structure suivante :

netfix/                     # project directory
  ⌊ users/                  # users app directory
    ⌊ __pycache__/
    ⌊ migrations/
    ⌊ templates/            # users template directory
      ⌊ users/
        ⌊ login.html
        ⌊ profile.html
        ⌊ register.html
        ⌊   ...
    ⌊   ...
    ⌊ urls.py
    ⌊ views.py
Vous utiliserez également ce qu'on appelle Django templates, utilisé dans les fichiers HTML. Il s'agit d'une méthode de codage HTML permettant, entre autres, de parcourir les objets passés (boucle for) ou d'effectuer des vérifications conditionnelles (instruction if/else). Pour en savoir plus, consultez la documentation des templates Django .

Vous pouvez obtenir le code déjà créé ici . Vous constaterez peut-être qu'il manque du code, tant dans les fichiers HTML que Python. Votre tâche consiste à le compléter afin que le site web fonctionne comme expliqué ci-dessus.

Un fichier CSS est déjà fourni (dans le chemin netfix/static/css/style.css), mais n'hésitez pas à le modifier et à créer votre propre design pour votre site. Cela signifie également que vous pouvez modifier le code HTML déjà fourni.

Lors de la première tentative d'exécution du projet avec la python3 manage.py runservercommande, vous constaterez une erreur. Vous devez commencer par définir le modèle client.

Prime
En bonus pour ce projet, il y a quelques choses que vous pourriez faire :

ajouter un système de notation, où les clients pourraient noter les services qu'ils ont demandés
ajouter des pages à la liste des services
n'hésitez pas à mettre en place votre propre bonus


# anglais
Objectives
Imagine there was a place in which you could ask someone to fix your bidet and at the same time ask for a service to paint the walls of your house. And while you are at it, home cleaning would be quite handy. Well, in this project you will help create a website in which all of this and more will be possible.

This website is still in the creation process, so not all features are available. You are going to implement some of the missing features.

You should also know that the website is being created in Django, a Python framework for web development. You can learn more about this framework in its own website. Yes, you will be messing around with Python, so be aware of the indentation. Also, you will need to know that this project was build in the version v3.1.14 of Django, so if you have problems to run this project, please check your current version of Django and make the necessary changes in order to get the project to run.

Instructions
The website should contain two types of users:

Company: that can create new services
Customer: that can request existing services
Both users should be able to register and login. In order to login, users should enter the email and the password to do so. However, to register, each type of user has to provide different information:

Customer:
email
password
password confirmation
username
date of birth
Company:
email
password
password confirmation
username
field of work
Each user should have a unique email and username. So while registering a user should be alerted if the email and/or username has already been registered.

Every user should have his own profile page in which their information should be displayed (apart from the password, obviously). And, in case the user is a customer, all previous requested services have to be displayed as well. In case of a company profile, along with all their information, should also be present the services it provides.

The field of work attribute in the companies will restrict the kind of services it can provide. The field of work attribute should only accept these values:

Air Conditioner
All in One
Carpentry
Electricity
Gardening
Home Machines
Housekeeping
Interior Design
Locks
Painting
Plumbing
Water Heaters
A Carpentry company can only create carpentry services as a Housekeeping company can only provide housekeeping services. However, the All in One companies can create any kind of services. But what does a service include? A service must have:

name
description
field (can have the same categories of fields as the companies, except you can not have an All in One service)
price per hour
date it was created (this attribute should automatically take a value when creating a service)
The website should have a page displaying the most requested services. There should also be a page showing every service in creation order (last created first) and a page for every service category, which displays the services available for that category.

Every service should have its own page, in which should be displayed the above information and also the company name that provides this service. A user should be able to check every service from that company by clicking on the name displayed and seeing the company profile.

Once a service is created by a company, every user has access to it. Only customers can request a service by providing the address where the service is required and the service time (in hours) needed for the service to be completed. Once a customer requires a service, it gets added to the list of previously requested services. In this list, for each service requested, the customer can see the service name, service field, calculated service cost, the date in which the service was requested and the company who provided the service.

You can check out this video to see what is expected from your project.

Django
Now, that you know what the project is about, we will explain you the file system architecture. A Django project is organized by a main folder of the project and different apps.

When starting a new Django project (with the command django-admin startproject <// name of project \\>), the main folder (that has the same name of the project) and a file called manage.py get created. This file is used to run various commands. The most common ones are:

python3 manage.py runserver -> runs a server in the port 8000 by default, and serves your project to it.
python3 manage.py startapp <// name of app \\> -> creates an app, in other words, creates a directory with most of the needed files for an app.
python3 manage.py makemigrations and python3 manage.py migrate -> these two commands are always hand in hand with each other. We use them to declare any changes made to the Django database (usually made in the models.py file of each app).
python3 manage.py createsuperuser -> creates a super user (admin) that can access and change information in the Django database (accessible in the url localhost:8000/admin).
python3 manage.py -> to get a list of all the commands available.
You may note that we use the command python3. You could simply use the command python but you must have the 3.0 version or higher installed.

Each app usually is linked to a different aspect of the project. For example, in this project, there are three apps:

services: handles the essential features related to services (service creation, services display, service request ...)
users: handles the essential features related to the users (user registration, user profile, user login ...)
main: handles the information that is common in all the project (home page, navigation bar, logout page ...)
By default, when starting an app, Django creates several files that are very useful to the development of a website. The ones in which we spend more time in are:

models.py -> where you can add objects and define their attributes to the Django database
views.py -> where you can manipulate the backend of a web page on the project
In addition to these two files, as a rule of thumb other files are manually created:

urls.py -> here you can specify the urls of your project and associate them to a view (from the views.py file), in order to display a web page. For example, the url profile/ is associated to the view views.ProfileView)
forms.py -> here you can create your forms to use in your views.py file. For example, you can create a default login form to use in the LoginView (present in the views.py file).
Usually we also create a folder where we can store templates (in HTML). This folder usually follows the following structure:

netfix/                     # project directory
  ⌊ users/                  # users app directory
    ⌊ __pycache__/
    ⌊ migrations/
    ⌊ templates/            # users template directory
      ⌊ users/
        ⌊ login.html
        ⌊ profile.html
        ⌊ register.html
        ⌊   ...
    ⌊   ...
    ⌊ urls.py
    ⌊ views.py
You will also use what it is known as Django templates, which is used inside of HTML files. It is a way of coding inside of HTML, allowing to go through objects passed in (for loop) or even make conditional verifications (if/else statement), amongst other cool stuff. To learn more about it, you can check the Django templates documentation.

You can get the code which is already done here. You may see that there are some code missing, both in HTML and Python files. Your task is to complete it so that the website works as explained above.

A css file is already provided (in the path netfix/static/css/style.css), but do feel free to change it up and come up with your own design for your site. This also means that you can change the HTML already provided.

When first trying to run the project with the python3 manage.py runserver command, you will notice that you will get an error. You must start there, by defining the customer model.

Bonus
As bonus for this project there are a couple things you could do:

add a rating system, where customers could rate the services they have requested
add pages to the service list
feel free to implement your own bonus
