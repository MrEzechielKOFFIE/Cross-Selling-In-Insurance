# **Cross-Selling-En-Assurance**



**I**ntroduction ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.004.png)

L’avancée des moyens de traitement des données permet aux entreprises aujourd’hui de personnaliser leurs stratégies de marketing, leurs permettant ainsi de valoriser les données collectées sur leurs clients. C’est aussi l’objectif du Cross Selling et plus spécifiquement du Cross Selling en assurance. Ainsi, il s’agit de cibler des clients particuliers et leur proposer, de nouveaux produits sur la base de leurs achats passés et de leurs habitudes de consommation afin de générer plus de profit.  

Dans la suite, nous vous détaillerons notre approche dans la résolution du problème de Cross Selling en assurance. Nous commencerons par une analyse exploratoire de la  base de données, ensuite, nous détaillerons la méthodologie utilisée et enfin, l’estimation du modèle final retenu. 

**A**nalyse exploratoire 

La base de données soumise à notre analyse est constituée de 84027 observations et de 11 variables dont huit catégorielle et trois quantitatives. Les variables catégorielles de cette base de données sont : Genre, Driving\_License, Region\_Code, Previously\_Insured, Vehicle\_Age, Vehicle\_Damage, Policy\_Sales\_Channel et Response. Les variables quantitatives de la base de données sont : Age, Annual\_Premium et Vintage. La variable d’intérêt est la variable Response qui permet de savoir si oui ou non l’individu observé à accepter de souscrire à l’assurance. Dans la suite, nous réaliserons des analyse univariée et croisée pour mieux comprendre la base la base de données, les distributions des variables et leurs relations 

**A**nalyse univariée 

*Près de majorité des individus de la base de données ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.005.png)n’est pas intéressée par le produit d’assurance. Par conséquent, l’on remarque ici que la variable réponse et déséquilibrée et que les individus intéressés par le produit sont sous représentés. Ainsi, l’on pourrait penser à appliquer une technique d’oversampling afin de rééquilibrer les données.* 

*La variable Gender est presqu’équitablement ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.006.png)distribuée selon les modalités Female et Male. Par conséquent, on peut dire qu’il y a presqu’autant de femmes que d’hommes dans la base de donnée proportionnellement à la taille de celle-ci* 

*La majorité des individus de la base de données à déjà ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.007.png)![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.008.png)eu un accident qui a endommagé le véhicule. De plus, une proportion non négligeable n’a jamais eu d’accident ayant provoqué un dommage sur le véhicule* 

*La majeure partie des véhicules présents dans la base ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.009.png)est âgée de moins de 2 ans avec une prépondérance des véhicules ayant entre un et deux ans. Il n’y a qu’une très faible proportion de véhicule âgés de plus de deux ans* 

*La plus grande partie des individus de la base de données n’a pas été précédemment assurée. Néanmoins, il y a quand ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.010.png)même une proportion non négligeable d’individus assurés.* 

*En effet, presque tous les individus de la base ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.011.png)possèdent un permis de conduire. Seulement une proportion très négligeable de 0.2% des individus de la base ne possède pas de permis. Par conséquent, cette variable étant presque constante, il apparaît pertinent de la supprimer.* 

*Pour la variable Policy\_Sales\_Channel, les canaux  ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.012.png)![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.013.png)les plus utilisés sont le 152, le 26 et le 124. Les  modalités étant nombreuses, nous avons regroupés  celles qui sont sous-représentées dans la modalité  999 représentant globalement moins de 8% de la  base de données.*  

*En ce qui concerne la variable Region\_Code, la  ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.014.png)région la plus représentées la région 28. De  même, nous avons regroupé les régions sous  représentées sous la modalité 888 qui représente  globalement moins de 10% de la base de données.*  

*On remarque que toutes les variables quantitatives de la base présentent des valeurs extrêmes. ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.015.png)Par conséquent, il convient de les traiter par le procédé de winsorization. De plus, on remarque que ces variables ont des échelles différentes et pour la plupart très élevées ainsi, nous allons éliminer l’effet d’échelle par la standardisation de la base de données.* 

![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.016.png) ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.017.png)

**A**nalyse Croisée  

*Par l’analyse de la variable réponse en fonction  ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.018.png)de l’âge et du genre, il apparaît que celle-ci est  presqu’également distribuée selon le genre en  proportion dans les tranches d’âge de plus de 35  ans et que donc,*   

*On remarque que tous les individus précédemment  ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.019.png)![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.020.png)assurés ont refuser de souscrire à l’assurance de  nouveau. Aussi, une grande partie des individus qui  n’étaient pas assurés a choisi de souscrire à  l’assurance. De plus, tous les individus non  précédemment assurés entre 35 et 50 ans ont souscrit à  l’assurance*  

*Il est clair que tous les individus qui ont souscrit à  ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.021.png)l’assurance sont ceux qui ont eu des véhicules  endommagés. Et tous les individus entre 35 et 50 ans  qui ont eu des véhicules endommagés ont souscrit.*  

*On remarque que ceux qui ont un véhicule âgé de plus  ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.022.png)de deux ans sont presque tous assurés. Aussi, seulement  une proportion marginale des individus ayant des  véhicules de moins d’un an sont assurés.*  

**A**nalyse de la corrélation 

![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.023.png) ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.024.png)

*L’analyse de la corrélation entre les variables nous montre que celle-ci sont faiblement corrélée et qu’il n’y a pas a priori de relations linéaires entre elles* 

**F**eature Ingineering ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.025.png)

**T**ransformation des variables 

Pour la suite du projet, nous avons été amenés à effectuer du One Hot Encoding sur les variables  qualitative de sorte à se retrouver à la fin avec un « Tableau disjonctif Complet ». Il en résultait 56 variables au total dont trois quantitatives. Par suite, nous avons réalisé une standardisation sur les données quantitatives de sorte à éliminer  l’effet d’échelle et améliorer  la convergence des algorithmes.  De plus, nous appliquons le procédé de **winsorization** qui consiste à remplacer  les valeurs en dessous ou au-dessus des quantiles précisés par les valeurs de ces quantiles. 

**S**élection des variables 

Toujours dans l’objectif d’optimiser nos traitements, nous nous sommes basés sur la feature importance  des  modèles  Xgboost  et  LightGBM  afin  de  déterminer  les  20  variables  les  plus importantes. 

*Sur la base de ces modèles, les variables retenues sont ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.026.png)les suivantes : Age, Annual\_Premium, Vintage, Gender, Policy\_Sales\_Channel\_26, Vehicle\_Damage, Policy\_Sales\_Channel\_124, Region\_Code\_28, Vehicle\_Age\_1-2 Year, Policy\_Sales\_Channel\_152, Region\_Code\_8, etc …* 

*Par suite, nous comparons les modèles avec selection de ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.027.png)variable et sans sélection afin de comparer l’avantage relatif de la sélection de variables. Ainsi, la différence de précision entre ces modèles étant marginale, il apparaît alors utile de réduire la dimension de la base (i.e : le nombre de variables)* 

**C**hoix du modèle![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.028.png)

D’après la section précédente, la plupart des modèles a un score relativement similaire, autour de 60%. Par conséquent, il apparait plus approprié de se baser sur le critère de stabilité des modèles et de précision globale afin de sélectionner les meilleurs. Par suite, l’on obtient le graphe suivant : 

*Nous avons réalisé une cross validation avec 20 folds ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.029.png)pour chacun des modèles et enregistré la précision des modèles. Par suite, nous avons affiché la dispersion au niveau des performances de chaque modèle pour analyser le overfitting. Par suite, il apparait que la plupart des modèles a une faible dispersion au niveau de la précision et donc un faible overfitting. Cependant, les modèles les moins variables et les plus précis sont la régression logistique (log) et le light Gradient Boosting (lgb)* 

**T**uning des modèles 

Pour la suite, nous allons nous intéresser à l’optimisation des modèles de régression logistique et de light gradient boosting au travers du tuning des paramètres. Ces modèles à tuner ont été choisis sur la base de la précision et de la variabilité des estimations au travers d’une cross validation à 20 folds. De plus, pour des soucis de ressources, nous choisissons  de réaliser le tuning sur 25% de la base donnée soit 21000 observations choisies de manière aléatoire. Aussi, pour l’entraînement  des différents modèles, nous choisissons d’appliquer la technique d’oversampling afin de rééquilibrer la base de données 

**T**uning Logistic Regression : 

Nous utilisons la méthode GridSearch qui automatise la recherche des paramètres optimaux. Par suite, les paramètres obtenues à la fin de cette méthode sont les suivantes : 

- Type de régularisation : l1, 
- Coefficient de régularisation : 0.1, 
- La méthode d’optimisation : liblinear. 

*Par suite, nous constatons que le modèle optimal obtenu au sens de la GridSearch ne diffère pas grandement du modèle avec les paramètres par défaut ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.030.png)*

**T**uning LightGBM : ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.031.png)

De même, pour tuner le modèle de LightGBM, nous utiliserons aussi la méthode GridSearch. Par suite, nous obtenons les résultats suivants : 

*Par suite, nous constatons que le modèle optimal obtenu au sens de la GridSearch ne diffère pas grandement du modèle avec les paramètres par défaut. ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.032.png)Par conséquent, nous choisissons de conserver le modèle par défaut* 

***C**ombinaison des modèles :* 

Dans la suite, nous choisissons de combiner les deux modèles afin de profiter des forces et faiblesses de chacun d’entre eux. Pour ce faire, nous choisissons de tester le stacking  sur les deux modèles que nous comparons aux modèles initiaux pour évaluer le gain en termes de performances et la pertinence des modèles. Par suite, nous obtenons les résultats suivants : 

*Nous remarquons ici que la combinaison des deux ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.033.png)modèles est peu efficiente par rapport aux modèles précédents. Par conséquent, nous décidons de conserver le modèle lightGBM qui fournit les meilleures performances* 

***M**odel Agnostic du modèle final* : 

A la fin de notre travail, il apparaît important  de savoir comment notre modèle fonctionne. L’approche  de  la  feature  importance  était  une  première  approche  dans  la  compréhension  du fonctionnement  du modèle.  Nous nous baserons  maintenant  sur la  shapley  value afin  de mieux comprendre le modèle retenu. 

*On constate que globalement, les variables ont un impact positif sur la prédiction. Ainsi, la plupart des variables contribuent grandement à la prédiction ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.034.png)de la souscription à l’assurance t celle ayant le plus grand impact est le fait ou non que le véhicule soit endommagé. Cependant, la prime annuelle a des effets* 

*négatifs sur la souscription à l’assurance auto.* *On déduit du directionality impact graph qu’avoir un véhicule ![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.035.png)![](Aspose.Words.947b6ecc-3988-49a0-a3f2-578657a10285.036.png)endommagé et ne pas avoir d’assurance rend l’individu plus susceptible de souscrire à l’assurance auto etc …* 

***E**stimation du modèle final* : 

Le modèle de Light Gradient Boosting étant le modèle finalement retenu, nous l’entraînerons sur toute la base de données, ensuite, nous enregistrerons ce modèle grâce à la librairie joblib de sorte à ne pas le réentraîner à chaque fois. Par ailleurs, nous avons joint un notebook contenant une fonction de préprocessing permettant de reproduire tout le traitement effectué sur la base d’entrainement et la fonction de prédiction dans laquelle nous chargeons le modèle précédemment enregistré pour pouvoir réaliser nos prédictions et enregistrer les livrables. 
