# PyBuddy

PyBuddy est une bibliothèque Python moderne pour contrôler les périphériques iBuddy USB. Cette version est un portage Python 3.10+ du projet original PyBuddy, avec des améliorations pour une meilleure compatibilité avec les systèmes modernes.

![iBuddy Device](https://incubaweb.com/wp-content/uploads/2007/10/ibuddy.jpg) 

## 🚀 Fonctionnalités

- Contrôle complet de votre périphérique iBuddy :
  - Mouvements des ailes (haut/bas)
  - Rotation du corps (gauche/droite)
  - Contrôle des LED RGB de la tête
  - Contrôle du cœur lumineux
- Interface Python simple et intuitive
- Support des animations et séquences
- Gestion avancée des erreurs USB

## 📋 Prérequis

- Python 3.10 ou supérieur
- PyUSB (`pip install pyusb`)
- Accès aux périphériques USB (voir la section Installation pour les permissions)

## 💻 Installation

1. Installez les dépendances système :

```bash
# Debian/Ubuntu
sudo apt-get install libusb-1.0-0

# Fedora
sudo dnf install libusb

# Arch Linux
sudo pacman -S libusb

# macOS (via Homebrew)
brew install libusb
```

2. Installez PyBuddy :

```bash
pip install pyusb
git clone https://github.com/yourusername/pybuddy.git
cd pybuddy
pip install -e .
```

3. Configurez les permissions USB (Linux uniquement) :

Créez un fichier de règles udev :

```bash
sudo nano /etc/udev/rules.d/99-ibuddy.rules
```

Ajoutez la ligne suivante :

```
SUBSYSTEM=="usb", ATTRS{idVendor}=="1130", ATTRS{idProduct}=="0001", MODE="0666"
```

Rechargez les règles udev :

```bash
sudo udevadm control --reload-rules
sudo udevadm trigger
```

## 🎮 Utilisation

Voici un exemple simple d'utilisation de PyBuddy :

```python
from pybuddylib import iBuddyDevice

# Créez une instance de iBuddy
buddy = iBuddyDevice()

# Faites clignoter le cœur 3 fois
buddy.doHeartbeat()

# Changez la couleur de la tête en rouge
buddy.doColorName(iBuddyDevice.RED)

# Faites battre les ailes
buddy.doFlap()

# Faites pivoter le corps de gauche à droite
buddy.doWiggle()

# Réinitialisez toutes les positions
buddy.doReset()
```

## 🎨 Couleurs disponibles

Les constantes de couleur prédéfinies sont :
- `RED`
- `GREEN`
- `BLUE`
- `YELLOW`
- `PURPLE`
- `LTBLUE` (Bleu clair)
- `WHITE`

## 🛠️ API

### Classe principale : `iBuddyDevice`

#### Méthodes de contrôle basiques :
- `setHeart(status)` : Contrôle la LED du cœur (ON/OFF)
- `setWing(direction)` : Contrôle la position des ailes (UP/DOWN)
- `setSwivel(direction)` : Contrôle la rotation (LEFT/RIGHT)
- `setHeadColors(red, green, blue)` : Contrôle la couleur de la tête

#### Macros d'animation :
- `doHeartbeat(times=3, seconds=0.3)` : Animation du cœur
- `doFlap(times=3, seconds=0.2)` : Animation des ailes
- `doWiggle(times=3, seconds=0.2)` : Animation de rotation
- `doColorName(rgb, seconds=WAITTIME)` : Change la couleur avec pause
- `doReset()` : Réinitialise toutes les positions

## 🤝 Contribution

Les contributions sont les bienvenues ! N'hésitez pas à :

1. Fork le projet
2. Créer une branche pour votre fonctionnalité
3. Commit vos changements
4. Push vers la branche
5. Ouvrir une Pull Request

## 📝 Licence

Ce projet est sous licence MIT - voir le fichier [LICENSE](LICENSE) pour plus de détails.

## 🙏 Remerciements

- Projet original PyBuddy par Jose.Carlos.Luna@gmail.com et luis.peralta@gmail.com
- Basé sur le travail de ewall <e@ewall.org>
- Inspiration du projet [PyMissile](http://scott.weston.id.au/software/pymissile/)

---
*Note : Ce projet n'est pas affilié avec les fabricants originaux de iBuddy.*
