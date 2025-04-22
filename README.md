import math

def afficher_menu():
    print("\n--- CALCULATRICE SCIENTIFIQUE ---")
    print("1 - Addition")
    print("2 - Soustraction")
    print("3 - Multiplication")
    print("4 - Division")
    print("5 - Puissance")
    print("6 - Racine carrée")
    print("7 - Sinus")
    print("8 - Cosinus")
    print("9 - Logarithme")
    print("0 - Quitter")

def calculatrice():
    while True:
        afficher_menu()
        choix = input("Choisissez une opération : ")

        if choix == '0':
            print("Au revoir !")
            break

        if choix in ['1', '2', '3', '4', '5']:
            a = float(input("Entrez le premier nombre : "))
            b = float(input("Entrez le deuxième nombre : "))

            if choix == '1':
                print("Résultat :", a + b)
            elif choix == '2':
                print("Résultat :", a - b)
            elif choix == '3':
                print("Résultat :", a * b)
            elif choix == '4':
                if b == 0:
                    print("Erreur : division par zéro.")
                else:
                    print("Résultat :", a / b)
            elif choix == '5':
                print("Résultat :", a ** b)

        elif choix == '6':
            a = float(input("Entrez un nombre : "))
            if a < 0:
                print("Erreur : racine d’un nombre négatif.")
            else:
                print("Résultat :", math.sqrt(a))

        elif choix == '7':
            angle = float(input("Entrez un angle en degrés : "))
            print("Résultat :", math.sin(math.radians(angle)))

        elif choix == '8':
            angle = float(input("Entrez un angle en degrés : "))
            print("Résultat :", math.cos(math.radians(angle)))

        elif choix == '9':
            a = float(input("Entrez un nombre strictement positif : "))
            if a <= 0:
                print("Erreur : log défini pour x > 0.")
            else:
                print("Résultat :", math.log(a))

        else:
            print("Choix invalide.")

# Lancer la calculatrice
calculatrice()
