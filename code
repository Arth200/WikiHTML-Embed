import wikipediaapi

def search_wikipedia(search_term):
    # Initialisation de l'API Wikipedia avec un user agent valide
    wiki_wiki = wikipediaapi.Wikipedia(
        language='fr',
        extract_format=wikipediaapi.ExtractFormat.WIKI,
        user_agent='my-application/1.0'
    )
    
    # Recherche de la page correspondant au terme de recherche
    page = wiki_wiki.page(search_term)

    # Vérification si la page existe
    if page.exists():
        print("Titre :", page.title)
        
        # Affichage du résumé de la page
        print("Résumé :\n", page.summary)
        
        # Gestion des pages de désambiguïsation
        if is_disambiguation_page(page):
            print("\nCeci est une page de désambiguïsation.")
            print("Liens vers d'autres pages Wikipedia pertinentes :")
            print_disambiguation_links(page)
    else:
        print("Aucun résultat trouvé.")

def is_disambiguation_page(page):
    # Vérifie si la page contient des sections typiques des pages de désambiguïsation
    return "may refer to" in page.text or "may stand for" in page.text

def print_disambiguation_links(page):
    # Affiche les liens vers d'autres pages Wikipedia pertinentes
    for link in page.links.values():
        print(link.title)

# Demande à l'utilisateur de saisir un terme de recherche
search_term = input("Entrez un terme de recherche : ")

# Appel de la fonction de recherche avec le terme saisi
search_wikipedia(search_term)
