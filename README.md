# TP Segmentation - Region Growing

### Architecture du projet :

```
.
├── GermsPositioning.hpp
├── GrowAndMerge.hpp
├── ImageProcessor.hpp
├── ImageUtil.hpp
├── Makefile
├── README.md
├── SegmentedRegion.hpp
├── bin
├── CMakeLists.txt
├── main.cpp
└── ressources
    ├── image_couche.png
    └── image_debout.png
```

## Instruction d'utilisation

Deux outils de compilation sont utilisables sur nôtre projet. Vous pouvez faire le choix entre Makile et CMake.

### Prérequis

L'installation de la bibliothèque OpenCV c++ est necéssaire pour que le projet compile. Voir ici: https://opencv.org/get-started/

### Arguments de commande 

La commande s'écrit comme ceci: `./seg <path/to/your/image> <mode d'affichage> <mode de colorisation>`
- `<path/to/your/image>`: Chemin de l'image que l'on souhaite traiter (obligatoire)
- `<mode d'affichage>`: 
  - 0: affichage des régions complètes 
  - 1: affichage des contours
- `<mode de colorisation>`:
    - 0: colorisation basé sur l'image de base
    - 1: colorisation aléatoire
### Makefile

1. Ce placer dans le même répertoire que le *main.cpp* et lancer dans le terminal la commande `make`.
2. Executer le programme avec le commnde : `./bin/main.out ./ressources/non_image.png`
    * Cette commande réalise la segmentation de l'image passée en paramètre
    * Vous pouvez ajouter un deuxième paramètre comme suit, pour n'afficher que les contures la segmentation :
        * `./bin/main.out ./ressources/image_couche.png 1`
3. Enjoy !

### CMake

#### Windows

1. **Visual studio 17**:
   * Dans le powershell, ce placer dans le répertoire du projet et exécuter ceci:
      * `mkdir build; cd build`
      * `cmake -G "Visual Studio 17 2022" ..`
   * Ouvrir la solution `RegionGrowing.sln`
   * Générer le projet `seg` et le définir en tant que projet de démarrage.
   * Dans `Déboguer` -> `Propriétés de débogage de seg` -> `Débogage` -> `Arguments de la commande`:
     * Ajouter des arguments de commande:
       * `../ressources/<image à charger> <0 ou 1 pour l'affichage des contours> <0 ou 1 pour le mode de colorisation>`
       * Exemple: `..ressources/image_debout.png 0 1` 
   * Passer en mode `Release` et lancer le programme.

2. **Clion**
   * Ouvrir le projet dans Clion en tant que projet `CMake`
   * Dans `Cmake Profiles` -> `Edit Cmake Profiles`
     * Ajouter un profile `Release` en utilisant Visual studio en `Toolchain`
   * Générer le projet `seg` et le définir en tant que projet de démarrage.
   * Dans `Run` -> `Edit configurations` -> `Débogage` -> `Program arguments`:
       * Ajouter les arguments de commande suivant:
           * Exemple: `..ressources/image_debout.png 0 1`
   * Sélectionner le profil CMake `Release-Visual Studio` et lancer le programme.
   
#### Linux
* Ce placer dans le répertoire du projet et exécuter ceci
  * `mkdir build; cd build`
  * `cmake -DCMAKE_BUILD_TYPE=Release ..`
  * `make`
* L'exécutable a été créé, plus qu'à compiler: 
  * Exemple: `./seg ../ressources/image_debout.png 0 1`

    
