# Application de Détection Interactive

## Description
Cette application utilise la vision par ordinateur et l'intelligence artificielle pour détecter en temps réel les expressions faciales et les gestes des mains d'un utilisateur via la webcam. Elle permet également de contrôler le curseur de la souris grâce aux mouvements de la main.

## Fonctionnalités
- **Détection d'expressions faciales** : Sourire, Surprise, Colère
- **Reconnaissance de gestes de mains** : OK, Pouce levé (Like), Cœur, "I Love You"
- **Contrôle de souris** : Déplacement du curseur avec l'index et clic par pincement pouce-index
- **Interface graphique intuitive** pour sélectionner le mode de détection
- Visualisation superposée des points de repère du visage et des mains
- Affichage en temps réel des expressions et gestes détectés

## Prérequis
Pour utiliser cette application, vous devez disposer de:
- Python 3.7 ou supérieur
- Une webcam fonctionnelle
- Les bibliothèques Python listées dans la section Installation

## Installation

### 1. Cloner le dépôt
```bash
git clone https://github.com/votre-username/detection-interactive.git
cd detection-interactive
```

### 2. Créer un environnement virtuel (recommandé)
```bash
python -m venv venv
```

Activation sur Windows:
```bash
venv\Scripts\activate
```

Activation sur macOS/Linux:
```bash
source venv/bin/activate
```

### 3. Installer les dépendances
```bash
pip install -r requirements.txt
```

Ou installez-les manuellement:
```bash
pip install opencv-python
pip install mediapipe
pip install numpy
pip install pillow
pip install pyautogui
```

## Utilisation

### Lancement de l'application
```bash
python detection_app.py
```

### Interface d'accueil
L'écran d'accueil présente quatre options:
- **Détection du Visage**: Active uniquement la reconnaissance des expressions faciales
- **Détection des Mains**: Active uniquement la reconnaissance des gestes de mains
- **Les Deux**: Active simultanément les deux modes de détection
- **Contrôle de la Souris**: Transforme votre main en souris pour contrôler le curseur

### Mode Détection du Visage
Détecte et affiche les expressions faciales suivantes:
- Sourire :)
- Surprise :O
- Fâché >:(

### Mode Détection des Mains
Reconnaît les gestes suivants:
- OK 👌
- Like 👍
- Cœur ❤️
- I Love You 🤟

### Mode Contrôle de la Souris
- Utilisez votre **index** comme pointeur pour déplacer le curseur
- **Pincez** votre pouce et votre index pour effectuer un clic
- Gardez le poignet relativement immobile pour plus de précision
- Effectuez des mouvements lents et contrôlés

### Quitter l'application
- Appuyez sur la touche **Q** pour quitter n'importe quel mode et revenir à l'écran d'accueil
- Utilisez le bouton **Quitter** sur l'écran d'accueil pour fermer l'application

## Personnalisation

Vous pouvez ajuster différents paramètres dans le code pour améliorer l'expérience utilisateur:

### Améliorer le contrôle de la souris
Dans la méthode `control_mouse_with_hand`:
- Modifier `smoothing` (par défaut: 5) pour ajuster la fluidité du mouvement
- Ajuster `amplification` (par défaut: 1.5) pour modifier la sensibilité du mouvement
- Changer le seuil de distance pour le clic (par défaut: 0.05) pour régler la sensibilité du pincement

### Réglages de détection
Dans la méthode `start_detection`:
- Modifier `min_detection_confidence` pour ajuster la précision de la détection
- Ajuster `min_tracking_confidence` pour améliorer la stabilité du suivi
- Changer la résolution de la caméra via `CAP_PROP_FRAME_WIDTH` et `CAP_PROP_FRAME_HEIGHT`

## Limitations connues
- La détection peut être sensible aux conditions d'éclairage
- Les seuils de détection sont fixes et peuvent ne pas convenir à tous les utilisateurs
- Une seule personne peut être détectée à la fois
- Le contrôle de souris nécessite un fond relativement stable pour éviter les mouvements indésirables

## Création d'un exécutable
Pour créer un fichier exécutable autonome:

1. Installer PyInstaller:
```bash
pip install pyinstaller
```

2. Créer l'exécutable:
```bash
pyinstaller --onefile --windowed detection_app.py
```

L'exécutable sera disponible dans le dossier `dist`.

## Dépannage

### La webcam ne démarre pas
- Vérifiez que votre webcam fonctionne avec d'autres applications
- Assurez-vous qu'aucune autre application n'utilise déjà la webcam
- Essayez de modifier la ligne `self.cap = cv2.VideoCapture(0)` en utilisant un autre index (1, 2, etc.)

### L'application est lente ou saccadée
- Réduisez la résolution de la caméra
- Fermez les applications en arrière-plan
- Sur les systèmes moins puissants, évitez d'utiliser le mode combiné

### La détection ne fonctionne pas correctement
- Assurez-vous d'avoir un bon éclairage
- Évitez les arrière-plans trop chargés ou en mouvement
- Positionnez-vous à une distance appropriée de la caméra (environ 50-70 cm)

## Licence
Ce projet est distribué sous licence MIT. Voir le fichier `LICENSE` pour plus d'informations.

## Auteur
zeggane
## Remerciements
- [MediaPipe](https://google.github.io/mediapipe/) de Google pour les modèles de détection
- [OpenCV](https://opencv.org/) pour le traitement d'image
- [PyAutoGUI](https://pyautogui.readthedocs.io/) pour le contrôle de la souris
