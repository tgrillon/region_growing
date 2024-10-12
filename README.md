# Segmentation - Region Growing

This project has been made in the context of the teaching unit *Mif02 - "Informatique Graphique Et Image"* of the master of computer science at the university of Claude Bernard Lyon 1 - France, Villeurbanne. 

This project is focusing on image segmentation using the region growing approach. For more details you can check out *rapport.pdf*.

### Project architecture 

```
.
├── ressources # contains input images 
|   ├── image_couche.png
|   └── image_debout.png
├── src
|   ├── GermsPositioning.hpp
|   ├── GrowAndMerge.hpp
|   ├── ImageProcessor.hpp
|   ├── ImageUtil.hpp
|   ├── main.cpp
|   └── SegmentedRegion.hpp
├── CMakeLists.txt
├── rapport.pdf
└── README.md
```

### Prerequisites

This project is using OpenCV. Please follow this link to install it on your system : https://opencv.org/get-started/

### Generate and build the project 

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

### Arguments de commande 

La commande s'écrit comme ceci: `./seg <path/to/your/image> <mode d'affichage> <mode de colorisation>`
- `<path/to/your/image>`: Chemin de l'image que l'on souhaite traiter (obligatoire)
- `<mode d'affichage>`: 
  - 0: affichage des régions complètes 
  - 1: affichage des contours
- `<mode de colorisation>`:
    - 0: colorisation basé sur l'image de base
    - 1: colorisation aléatoire
