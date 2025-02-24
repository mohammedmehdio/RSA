import math

def is_prime(num):
    """Vérifie si un nombre est premier"""
    if num < 2:
        return False
    for i in range(2, int(num**0.5) + 1):
        if num % i == 0:
            return False
    return True

def factorize(n):
    """Trouve les facteurs premiers p et q de n"""
    if n < 2:
        return None, None
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0 and is_prime(i):
            j = n // i
            if is_prime(j):
                return i, j
    return None, None

def find_private_from_public():
    """Trouve la clé privée à partir de la clé publique"""
    try:
        e = int(input("Entrez e (clé publique): "))
        n = int(input("Entrez n (module): "))
        
        p, q = factorize(n)
        if not p or not q:
            print("Erreur: Impossible de factoriser n en deux nombres premiers!")
            return
        
        phi = (p-1)*(q-1)
        if math.gcd(e, phi) != 1:
            print("Erreur: e doit être premier avec φ(n)!")
            return
        
        d = pow(e, -1, phi)
        print(f"\nClé privée trouvée: (d, n) = ({d}, {n})\n")
        
    except ValueError:
        print("Entrée invalide! Recommencez.")

def find_public_from_private():
    """Trouve la clé publique à partir de la clé privée"""
    try:
        d = int(input("Entrez d (clé privée): "))
        n = int(input("Entrez n (module): "))
        
        p, q = factorize(n)
        if not p or not q:
            print("Erreur: Impossible de factoriser n en deux nombres premiers!")
            return
        
        phi = (p-1)*(q-1)
        if math.gcd(d, phi) != 1:
            print("Erreur: d doit être premier avec φ(n)!")
            return
        
        e = pow(d, -1, phi)
        print(f"\nClé publique trouvée: (e, n) = ({e}, {n})\n")
        
    except ValueError:
        print("Entrée invalide! Recommencez.")

def main():
    """Menu principal interactif"""
    while True:
        print("\n" + "="*30)
        print("1. Générer des clés RSA")
        print("2. Chiffrer un message")
        print("3. Déchiffrer un message")
        print("4. Trouver clé privée depuis clé publique")
        print("5. Trouver clé publique depuis clé privée")
        print("6. Quitter")
        
        choice = input("\nChoisissez une opération (1-6): ")
        
        if choice == "1":
            generate_keys()
        elif choice == "2":
            rsa_encrypt()
        elif choice == "3":
            rsa_decrypt()
        elif choice == "4":
            find_private_from_public()
        elif choice == "5":
            find_public_from_private()
        elif choice == "6":
            print("Au revoir!")
            break
        else:
            print("Choix invalide! Réessayez.")

# Le reste du code original reste inchangé...

if __name__ == "__main__":
    main()
