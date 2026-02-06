# TP1
Documentation du Lab 1 : Mise en place de Mobexler

Table des matières

1.Téléchargement de Mobexler

2.Vérification d'intégrité

3.Import dans VirtualBox

4.Configuration réseau

5.Tests de connectivité

6.Création du snapshot

7.Connexion du téléphone Android


1. Téléchargement de Mobexler

<img width="687" height="276" alt="Screenshot 2026-02-06 211212" src="https://github.com/user-attachments/assets/27cb1b18-ccf7-4a1c-b760-37680cdca6f3" />
    
    Téléchargement de l'OVA Mobexler depuis Google Drive
    Taille du fichier : 14 Go (trop volumineux pour l'analyse antivirus de Google)
    Utilisation du bouton "Télécharger quand même"


<img width="1377" height="726" alt="Screenshot 2026-02-06 212724" src="https://github.com/user-attachments/assets/921571ac-bc1e-44f6-b764-f91bab22dfcf" />
    
    Fichier Mobexler.ova présent dans le dossier Téléchargements
    Taille : 14,229,472 KB
    Type : Open Virtualization Appliance


2.Vérification d'intégrité

<img width="1683" height="286" alt="Screenshot 2026-02-06 212800" src="https://github.com/user-attachments/assets/09ee6495-2eb2-4997-93f4-878a6af07692" />

    Calcul du hash SHA256 avec PowerShell :
    Get-FileHash .\Mobexler.ova -Algorithm SHA256
    Hash obtenu : 07C4D1D456B564313996F8A8BD5402E9EB825D7B817C5031C52396231DDF188

<img width="847" height="772" alt="Screenshot 2026-02-06 212840" src="https://github.com/user-attachments/assets/4a59b1ac-8657-4bc8-b06d-386331dd6ce9" />

    Vérification sur le site officiel Mobexler
    Hash officiel : 07c40d1456b564313996f8a8bd5402e9ebb825d7b817c5031c52396231ddf188
    Conclusion : Hash identique → fichier intact et authentique


3. Import dans VirtualBox

<img width="945" height="923" alt="Screenshot 2026-02-06 214230" src="https://github.com/user-attachments/assets/572ca717-05e3-4137-89f8-5a1387b4854a" />

Import réussi de Mobexler.ova dans VirtualBox

Configuration système :

    Mémoire : 4096 MB
    Processeurs : 2
    Stockage : 70 GB

Configuration réseau initiale :

    Adapter 1 : NAT (pour Internet)
    Adapter 2 : Host-Only (pour labo isolé)

<img width="1918" height="1078" alt="Screenshot 2026-02-06 215022" src="https://github.com/user-attachments/assets/56be9add-8058-4f6f-843f-2ca4e7ed8619" />

    Premier démarrage de Mobexler
    Terminal ouvert avec utilisateur mobexler
    Interface graphique fonctionnelle


4. Configuration réseau

<img width="1272" height="243" alt="Screenshot 2026-02-06 223445" src="https://github.com/user-attachments/assets/1a34cb40-614d-4cbd-8d31-e81441fc4e7b" />

Sortie de la commande ip a :

    Interface Host-Only (enp0s8) : 192.168.56.103/24 (état UP)
    Interface NAT (enp0s17) : 10.0.2.15/24 (état UP)

Les deux interfaces réseau sont actives et correctement configurées

5. Tests de connectivité

<img width="1258" height="467" alt="Screenshot 2026-02-06 223702" src="https://github.com/user-attachments/assets/9c6c856a-2371-412b-a2e9-70b656c9a470" />

Test de connectivité Internet :
     
     ping -c 2 8.8.8.8
     Résultat : 2 paquets transmis/reçus, 0% de perte
     Temps de réponse : ~123 ms en moyenne

Test DNS :
    
    ping -c 2 google.com
    Résolution DNS fonctionnelle
    Connexion Internet établie via NAT

6. Création du snapshot

<img width="932" height="915" alt="Screenshot 2026-02-06 224700" src="https://github.com/user-attachments/assets/83cd27ff-8a21-4de0-8ed2-0bfaf84d8d16" />


    Création du snapshot "CLEAN_BASELINE_TP1"
    Description : état propre après configuration réussie
    Date : 2/6/2026 10:41 PM
    Utilité : permet de restaurer l'environnement à un état connu après chaque manipulation


7. Connexion du téléphone Android

<img width="1007" height="318" alt="Screenshot 2026-02-06 231304" src="https://github.com/user-attachments/assets/22903ce1-c4f2-4f70-9ec0-75c35c5c2d1c" />

    Vérification d'ADB (Android Debug Bridge) :
        adb version---->Version : 1.0.39

    Détection du téléphone :
        adb devices---->Appareil détecté : R5CW41FKVGN en mode device

