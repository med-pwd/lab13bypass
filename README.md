# LAB13-Bypass-de-la-D-tection-de-Root-Android-avec-Objections

analyste:souaid med amine

Sur Android, de nombreuses applications intègrent des mécanismes de sécurité pour détecter si l’appareil est rooté. Le root peut en effet permettre à un utilisateur d’accéder à des fichiers système sensibles, de modifier le comportement d’une application ou d’intercepter des données. Pour se protéger, certaines applications utilisent des vérifications basées sur des fichiers système (comme su), des commandes shell ou des bibliothèques de sécurité telles que RootBeer.

Dans le cadre du test de sécurité des applications mobiles, il devient nécessaire de comprendre ces mécanismes de détection et d’évaluer leur robustesse. Des outils comme Objection, reposant sur Frida, permettent d’intercepter et de modifier le comportement des fonctions Java ou natives afin de simuler un environnement non rooté. Cette approche est utilisée dans les tests de sécurité pour analyser les applications sans être bloqué par ces restrictions.

## Étape 1 — Installer Objection et Frida côté PC


<img width="950" height="371" alt="image" src="https://github.com/user-attachments/assets/7ce0297d-e5d9-4552-8da5-65bb5df39011" />


<img width="222" height="41" alt="image" src="https://github.com/user-attachments/assets/404b082b-9097-4477-af19-002059483740" />


<img width="433" height="158" alt="image" src="https://github.com/user-attachments/assets/2fc5352f-ffce-4c15-b453-b56fee29c759" />


<img width="932" height="477" alt="image" src="https://github.com/user-attachments/assets/97de38e3-e87f-4f5b-abd3-2163d407faf5" />


<img width="398" height="492" alt="image" src="https://github.com/user-attachments/assets/cd2b6155-3592-489d-b217-2c85ac8c4f8c" />


<img width="525" height="488" alt="image" src="https://github.com/user-attachments/assets/982612e0-11c6-499a-8dfc-9fda4f2d9a4f" />


<img width="347" height="70" alt="image" src="https://github.com/user-attachments/assets/747141c3-7ff9-4a1a-a7f8-0cebad90e91a" />

## Étape 2 — Préparer l’appareil et démarrer frida-server


<img width="414" height="122" alt="image" src="https://github.com/user-attachments/assets/63e401d2-f3f7-4cce-b2fe-a622b0ecc138" />


<img width="284" height="46" alt="image" src="https://github.com/user-attachments/assets/0314fcc4-7522-4a6b-855b-64eaffd3cdc1" />


<img width="647" height="29" alt="image" src="https://github.com/user-attachments/assets/e0407e99-1d72-4607-91d5-0217b1da161f" />


<img width="392" height="491" alt="image" src="https://github.com/user-attachments/assets/8f11e9a9-7637-4ea0-8140-4cabfe8c8a34" />


## Étape 3 — Démarrer Objection sur l’app cible


<img width="317" height="167" alt="image" src="https://github.com/user-attachments/assets/951e795c-acd8-412a-b16d-60a26ad8c269" />

## Étape 4 — Que fait android root disable ?

Objection utilise des hooks via Frida afin de modifier le comportement des applications et masquer les signes de root.

Cette commande permet de simuler un environnement Android « normal » en interceptant les vérifications système utilisées par les applications. Elle bloque notamment la détection de fichiers ou de commandes liés au root (comme su), et peut également tromper certaines bibliothèques de sécurité (par exemple RootBeer) pour qu’elles indiquent que l’appareil n’est pas rooté.

## Étape 5 — Valider le bypass

<img width="527" height="494" alt="image" src="https://github.com/user-attachments/assets/17be1300-8025-42f5-9d5d-d83f7dd600a1" />

<img width="437" height="176" alt="image" src="https://github.com/user-attachments/assets/61d76047-d59e-4d17-9742-712f4f4a1d0a" />

## Étape 6 — Automatiser : injection au démarrage avec plusieurs commandes

<img width="613" height="164" alt="image" src="https://github.com/user-attachments/assets/2f9bcd57-3aa7-4152-9776-710cc77b1cf8" />

# Conclusion

Le contournement de la détection de root sur Android repose principalement sur l’interception des mécanismes utilisés par les applications pour vérifier l’intégrité de l’environnement. Grâce à des outils comme Objection et Frida, il est possible de masquer les traces de root en modifiant dynamiquement les réponses des fonctions de vérification.

Cependant, il est important de souligner que ces techniques ne suppriment pas réellement le root du système, mais ne font que tromper l’application cible. Elles sont principalement utilisées dans un cadre de test, d’audit de sécurité et de recherche en cybersécurité afin d’évaluer la résistance des applications face à des environnements modifiés.
