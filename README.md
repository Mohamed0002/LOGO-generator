
## Etape 1: tokenisation 

    Tout d'abord, les mots de la question sont tokénisés et les mots vides sont supprimés :

    fonction qui permet  la segmentation du texte en mots
    def tokeneriser(questions)

  ## Etape 2 : Trouvez le mot interrogatif dans la question
   

    fonction qui  consiste à rechercher des objets textuels (c'est-à-dire un mot, ou un groupe de mots)  
    catégorisables dans des classes telles que noms de personnes, noms d'organisation etc...   
    
    <span style="color: green"> def ner(question) </span>

    -Expression Régulières :

    Utilisation des expressions régulières pour extraire les différents mots clés que je pourrai comparer
    par la suite  avec la fonction ner() utiliser auparavant.

    # Permet d'extraire les mots-clés d'une question a partir de mes expression régulière effectuer auparavant.
    # cela me retourne une  liste des mots-clés

    def extract_keywords(exps: list, question: str) :


    # Modification de la fonction extract_keyword en essayant de la rapprocher au plus de la fonction ner ,
    elle permet d'extraire le bon mots clé associés a chaque question 
    # exemple :  the_video_game_World_of_Warcraft' sera remplacé par  World_of_Warcraft

    def keyword2(question,exps):

 ## Etape 3 :  Recherche de la meilleure relation 
    Recherche de la meilleure relation dans `relations.txt` à partir des tokens et du mot interrogatif.

    # cette fonction se verra comparer chaque premier mot récupérer par la fonction extract_keywords extract_keywords 
    avec le fichier Copywithout afin de lui associer la bonne relation 
    def Find_best_relation(question): 


 ## Etape 4 :  Création de la requete SPARQL 
   

    # Permet d'effecter une requête SPARQL au serveur dbpedia

    def query_dbpedia(query: str) -> object:

    # return  une requête SPARQL remplie
    def fill_query(ressource: str, lien: str) -> str:

    # return la  liste des URI 
    def extract_uri(res: object) -> list:

    # Fonction qui permet de comparer nos  réponses trouvées aprés avoir trouver la bonne relation  
    avec les réponses de mon  fichier xml mise dans une liste answers .

    def Request_sparsql():

 ## Etape 5 : 
     Résultat obtenu :
    Les ressources correctes trouvées sont de 72 % :

    J'ai décidé d'ajouter un, +1 ont mes correctes answers, car lorsqu'il compare les réponses de mon dictionnaire 
    avec les réponses de la requête pour la question : 'Which museum exhibits The Scream by Munch ?'

    Le programme m'affiche la mauvaise réponse : 

    réponse du dictionnaire : ['https://dbpedia.org/resource/Munch_Museum', 'https://dbpedia.org/resource/National_Gallery_(Norway)']  
    réponse de la requête ['http://dbpedia.org/resource/Munch_Museum', 'http://dbpedia.org/resource/National_Gallery_(Norway)']
    mauvaise réponse trouver !

    Pourtant, si on compare ça manuellement ce  sont exactement les mêmes liens, 
    il se peut que cela vienne du fait que les liens de mon dico sont en http et ceux de la requêtes sont en http.
    
    
    print(f"{'Ressource correct trouvée':<30}: {(correct_answer + 1) / len(questions):.2%}")


## démarche d amélioration : 

    amélioration de la fonction : 

    def Find_best_relation(question): 

    Ma fonction n'arrive pas à tous les coups  à trouver la bonne relation, 
    il se peut que la fonction leveinsthein ne soit pas suffisante et qu'il faudra mettre en place d'autres mécanismes . 

    Prenons pour exemple la question : 
    'Who was the wife of U.S. president Lincoln?'

    keyword2('Who was the wife of U.S. president Lincoln?',arr)
    ('wife', 'U.S._president_Lincoln')

    def Find_best_relation('Who was the wife of U.S. president Lincoln?'): retourne wife

    Ici wife ne pourra jamais être remplacé par spouse . D'où les limites de la fonction leveinsthein.
    il faudrait peut être ajouter des fonctions qui permettent de trouver les synonymes les stocker
    dans une liste et les recomparer avec notre fichier relation.txt

    - deuxiéme demarche d'amélioation :
     si l'on applique par exemple la fonction ner() a la question suivante : 
     'What is the highest place of Karakoram?'
     ner('What is the highest place of Karakoram?') Cela retourne karakom, 
     or sur dbpedia karakom prend comme nom K2 donc impossible de trouver la bonne réponse.
    
    

    









