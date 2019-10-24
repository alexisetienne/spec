# spec

Expression des besoins
Votre client travaille dans le domaine touristique, il vous demande de réaliser un portail web permettant de mettre en avant tous les hotels partenaires et d'offrir aux visiteurs, une fois connecté, la possibilitée de réserver en ligne une ou plusieurs chambres disponibles pour une ou plusieurs personnes.
Il aimerait dans un premier temps, que vous lui présentiez rapidement une première version qui affiche les hotels répertoriés par ville, par exemple en cliquant sur une ville, nous aurions tous les hotels accessibles par notre appli pour cette ville.
Le client imagine que le visiteur pourra donc naviguer et visualiser plusieurs hotels d'une ville donnée, il faudra prévoir aussi d'afficher des informations détaillées par hotel telles que : tel, adresse, nombre d'étoiles et le nomdre de chambres disponibles !
Il souhaite offrir des accès privilégiés aux hoteliers afin d'ajouter/modifier une image pour chaque hotel et de modifier les informations détaillées (nom de l'Hotel, tel, adresse, nombre d'étoiles)

SPECIFICATION GENERALE
Nous devons réaliser une application touristique en ligne permettant de mettre en avant tous les hôtels partenaires et d'offrir aux visiteurs, une fois connecté, la possibilitée de réserver en ligne une ou plusieurs chambres disponibles pour une ou plusieurs personnes.
L'appli propose d'afficher tous les hôtels classés par catégories accessibles via notre api, d'en selectionner un ou plusieurs pour constituer un caddy avec la possibilitée de passer commande à tout moment à condition d'être aunthentifié, enfin de "régler en ligne".
On doit distinguer 3 rôles dans l'application :
    utilisateur non connecté ou individu lambda qui peut naviguer sur votre site et consulter les infos des produits proposés par catégorie
    utilisateur connecté donc authentifié qui peut réaliser un panier constitué d'un ou plusieurs produits puis passer commande
    administrateur qui peut changer les photos des produits, modifier les infos.



SPECIFICATIONS TECHNIQUES / CONCEPTION
    Spring au niveau du back (java 8, api Rest)
    Angular 8 pour le front (bootstrap3, Bootstrap Material Design (BMD), jquery)
    Intégration continue avec Git, 2 repos (back & front)
    Gestion des photos : elles ne seront pas stocké en base pour ne pas alourdir celle-ci, chaque produit aura un attribut qui pointe sur le fichier correspondant (chemin)
    la gestion de l'authentification se fera côté front avec des données fictives locales (tableau avec noms des utilisateurs et leurs rôles : USER et(ou) ADMIN)
    L'utilisateur ou token (user + roles) sera stocké en local storage afin de permettre la navigation sans déconnexion

SPECIFICATIONS FONCTIONELLES -> POUR LES VISITEURS DU SITE :
    afficher la liste des produits selectionnable (ou accessible) au niveau du back (page d'accueil ou home)
      -> afficher les photos de chaque hôtel, prévoir une photo de substitution
    afficher la liste des hôtel correspondant à une catégorie par le simple clic sur celle ci
    afficher le pointer vers la catégorie ou hôtel survolée avec la souris (pour clic)
    afficher la liste des hôtels d'une catégorie cliqué
    les catégories non selectionnés doivent apparaitre en grisées
    afficher sous chaque hôtel des icones signifiant s'ils sont selectionnés
    lorsqu'on clic sur une photo, afficher les informations détaillées sur l'hôtel correspondant
      -> (nom de l'hôtel, téléphone, adresse, description, prix, nombre d'étoiles o/n, nombre de chambres).

SPECIFICATIONS FONCTIONELLES -> POUR LES ADMINISTRATEURS :
    considérant ici, qu'ils ont déjà un compte, il faut proposer un formulaire d'authentification (côté front uniquement)
    une fois authentifié, il doit le rester tant qu'il ne se déconnecte pas (stockage dans le local storage)
    de changer la photo d'un hôtel par l'accès à l'explorateur de fichiers côté front :
      -> cela provoquera l'envoi de la photo au niveau du back ou elle sera stocké
      -> la nouvelle photo devra instantanément être affiché sur le front
    l'admin peut acceder naturellement aux infos d'un hôtel mais en plus, il peut les modifier, ce qui met à jour le back...
    les photos des hôtels seront stockés dans un dossier respectant ce chemin : "user.home" + /ecom/products
    les photos des catégories seront dans : "user.home" + /ecom/categories
    vous ne devez pas accepter les photos de plus de 2.5MB (back)

SPECIFICATIONS FONCTIONELLES -> POUR LES UTILISATEURS authentifiés :
    considérant ici, qu'ils ont déjà un compte, il faut proposer un formulaire d'authentification (côté front uniquement)
    une fois authentifié, il doit le rester tant qu'il ne se déconnecte pas (stockage dans le local storage)
    permettre de créer un panier/caddy dans le local storage, composé d'un ou plusieurs hôtels
    afficher le contenu d'un caddy (id,liste des hôtels, quantité, prix(qté*prix hôtel), total caddy)
    prévoir un bouton pour supprimer un ou plusieurs éléments de notre caddy
    revenir à tout moment sur la liste des hôtels pour ajouter dans le caddy en cours
      -> si l'ajout concerne un hôtel déjà présent dans le caddy, il faut juste augmenter la quantité de celui-ci
