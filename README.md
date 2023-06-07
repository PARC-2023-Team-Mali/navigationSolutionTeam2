TEAM1_RobotsMali: PARC Engineers League

Introduction:</BR>

    Le défi de cette phase de simulation consiste à créer un logiciel pour rendre autonome le PARC AgRobot (Robot agricole) qui est un véhicule terrestre autonome (UGV). Le robot doit être capable de se déplacer de manière autonome sur le terrain pour inspecter les cultures et détecter les mauvaises herbes. Il peut utiliser des capteurs tels que des caméras, des lidars et des modules GPS pour se déplacer avec précision dans un environnement dont les etapes se divise en deux taches qui sont: le deplacemnt du robot jusqu'à atteindre un but précis et la detection des coordonnées GPS de chaque herbe présent sur l'environnement, au cours du trajet le robot effectue des virages sur un terrain accidenté suivant un ittineraire précis  jusqu’à ce que l’emplacement du but soit atteint.
    
L'utilisation de PARC AgRobot (Robot agricole)  en Afrique présente plusieurs avantages convaincants. Le PARC AgRobot peut être programmé pour effectuer des tâches agricoles spécifiques telles que la plantation, l'arrosage, la fertilisation la récolte et la diminution de l'utilisation des produits chimiques. Ils peuvent travailler de manière plus rapide et plus efficace que les travailleurs humains, ce qui peut augmenter la production et la diminution du prix des produits agricole. Malgré ces défis, l'utilisation de robots peut contribuer à améliorer la productivité et la durabilité de l'agriculture en Afrique et dans le monde entier.

    

Pays de l’équipe: MALI

Noms des membres de l’équipe:

    Nom et Prénom (Coach): 
      Sanogo Hamidou

    Nom et Prénom (Capitain): 
      Kamate Panga Azazia 

    Nom et Prénom (Membre): 
      Diarra Yacouba 

    Nom et Prénom (Membre):
      Lansar Alpha Abdoulaye 
    
    Nom et Prénom (Membre): 
      Diallo Seydou 
    
Dépendances
    Les Packages nécessaires sont:    (requis Python version 3)

    rospy: 
         rospy est une bibliothèque client Python pure pour ROS. L’API client Rospy permet aux programmeurs Python d’interagir rapidement avec ROS Topics, Services et Parameters. La conception de rospy favorise la vitesse d’implémentation (i.developer time) sur les performances d’exécution afin que les algorithmes puissent être rapidement prototypés et testés au sein de ROS. Il est également idéal pour le code de chemin non critique, comme le code de configuration et d’initialisation. De nombreux outils ROS sont écrits en rose pour profiter des capacités d’introspection de type. De nombreux outils de ROS, tels que rostopic et rosservice, sont construits sur le dessus de rospy.


    actionlib:
       La pile actionlib fournit une interface normalisée pour l’interfaçage avec les tâches pré-emptables. 
       Par exemple, déplacer la base vers un emplacement cible, effectuer un balayage laser et retourner le nuage de points résultant, détecter la poignée d’une porte, etc.

    Dans tout grand système basé sur ROS, il y a des cas où quelqu’un voudrait envoyer une demande à un noeud pour effectuer une tâche, et aussi recevoir une réponse à la demande. Cela peut actuellement être réalisé via les services ROS.

    Dans certains cas, cependant, si le service prend beaucoup de temps à exécuter, l’utilisateur peut vouloir la possibilité d’annuler la demande pendant l’exécution ou obtenir des commentaires périodiques sur la façon dont la demande progresse. Le paquet actionlib fournit des outils pour créer des serveurs qui exécutent des objectifs de longue durée qui peuvent être pré-exemptés. Il fournit également une interface client afin d’envoyer des requêtes au serveur.


    actionlib_msgs:
      La pile actionlib fournit une interface normalisée pour l’interfaçage avec les tâches pré-emptables. Par exemple, déplacer la base vers un emplacement cible, effectuer un balayage laser et retourner le nuage de points résultant, détecter la poignée d’une porte, etc.

    sensor_msgs:
      Cet ensemble définit les messages pour les capteurs couramment utilisés, y compris les caméras et les télémètres à balayage laser.

    geometry_msgs:
       geometry_msgs fournit des messages pour les primitives géométriques courantes telles que les points, les vecteurs et les poses. Ces primitives sont conçues pour fournir un type de données commun et faciliter l’interopérabilité dans l’ensemble du système.


    tf:
       tf est un paquet qui permet à l’utilisateur de garder une trace de plusieurs trames de coordonnées au fil du temps. tf maintient la relation entre les cadres de coordonnées dans une arborescence tamponnée dans le temps, et permet à l’utilisateur de transformer des points, des vecteurs, etc., entre deux cadres de coordonnées à tout moment souhaité.
    
    nav_msgs : 

      Le package nav_msgs dans ROS contient des définitions de messages standardisés pour la navigation et la planification de trajectoire des robots. Ces messages sont utilisés pour la communication entre les différents composants logiciels d'un système robotique, tels que les capteurs, les algorithmes de localisation, les planificateurs de trajectoire, etc.

    math : 
      la bibliothèque math est un module intégré qui fournit un ensemble de fonctions et de constantes mathématiques pour effectuer des opérations mathématiques avancées. Cette bibliothèque est largement utilisée pour effectuer des calculs numériques, des transformations mathématiques et d'autres opérations mathématiques courantes.



Tache 1:

   Dans cette tâche, notre robot autonome navigue en toute sécurité sur les trottoirs à travers differents procéssus succéssives.
   Notre approche est une approche Mathématiques basées sur les nombres complexes, plus précisement les transformations du plan à savoir la translation et la rotation. On fournit des points cibles au robot  et le robot fait la translation et la rotation nécessaire pour atteindre ces points, Chaque point est transformé en nombre complexe à savoir les points cibles et la position du robot à chaque instant.
   La translation étant effectuée entre un point cible et la position du robot à chaque instant, on soustrait la partie réelle du point cible de la partie réelle de la position du robot à chaque instant et la même chose est faite sur les parties imaginaires.
   La rotation étant effectuée en utilisant le resultat précedent effectuer dans la translation.  On calcule l'angle entre les parties réelles soustraites et les parties imaginaires soustraites en utilisant les fonctions trigonométriques appropriées. Une contrainte est ensuite appliquée  sur l'angle trouvé pour qu'il soit toujours dans [-π, π] , permettant au robot de tourner dans la direction la plus courte vers le point souhaité.

      Exécutez la commande suivante pour exécuter task1
      $ roslaunch team_mali_two task1_solution.launch


Tache 2:

   Dans cette tâche, notre robot détecte la différence entre les herbes et les salades afin de localiser la position des herbes dans le champ cela ce fait en différent etapes succéssives qui sont:
   
1) Détection des mauvaises herbes
     Pour la détection des mauvaises herbes, nous avons utilisé un masque basé sur la couleur opérant dans l'espace colorimétrique pour isoler les mauvaises herbes dans les images.
     Ensuite, nous avons utilisé le "bwconncomp" qui effectue une analyse des composants connectés pour supprimer le bruit des images masquées (composants connectés qui sont trop petits pour être désherbés)
     Nous avons fusionné les pixels de rappel suffisamment proches pour le faire afin d'obtenir des objets cohérents qui seront considérés comme des mauvaises herbes (sinon toutes les feuilles de la mauvaise herbe auraient été considérées comme une seule mauvaise herbe).
     Ensuite, et après avoir converti les indices de pixels linéaires des mauvaises herbes en coordonnées de pixels, nous avons trouvé les coordonnées des mauvaises herbes (u, v) en calculant le centroïde de ces listes de coordonnées
     Ce processus sera répété pour chaque image acceptée par le nœud task2_solution.m

2) De l'image au cadre de la caméra (Transformation de perspective)
     Nous avons effectué un calibrage de caméra avec le nœud camera_calibrator du package ROS camera_calibration et obtenu les matices de caméra, de rectification et de projection.
     Pour cela, nous avons créé un fichier .sdf simulant un échiquier dans le belvédère.
     Ensuite nous avons utilisé la projection perspective faite en utilisant la matrice de projection obtenue en implémentant cette relation
     Considérant que la matrice de projection est la combinaison de la matrice de caméra (A), de la matrice de rotation | translation (R | t)

3) Du cadre de la caméra au cadre base_link
     Nous venons d'utiliser la structure matlab rostf et les transformations existantes entre les caméras et base_link pour transformer les coordonnées des mauvaises herbes du cadre de la caméra au cadre base_link

4) De Base_link à World Frame
     Puisqu'il n'y a pas de transformation disponible entre base_link et world_frame, nous avons créé une matrice de transformation cartographiant la matrice de rotation et le vecteur de translation du robot dans world_frame au moment de prendre la photo.
     Ensuite, nous multiplions simplement cette matrice par les coordonnées homogènes des mauvaises herbes dans le cadre base_link pour obtenir leurs coordonnées dans world_frame

Défis rencontrés :

    Au sujet du défi, nous avons eu des problèmes avec les installations et la prise en main de ROS. Nous avons également eu des erreurs avec l'aquisition et le traitement des données, l'application de filtre de couleur, la calibration de la camera, les transformation suvant des cadres de coordonnées, la localisation d'herbe dans diverce image fourni par la camera,l'utilisation de different biblothèque comme: geometry_msgs, sensor_msgs... mais en fin de compte, une solution a été trouvée pour la configuration du fichier rplidar.xacro (parce que nous utilisons le CPU et non le GPU)
    Avec le CPU, la machine prend beaucoup de temps lors de l’exécution d’une tâche à chaque fois ou parfois la machine se plante et elle devra être redémarrée.
    
    
