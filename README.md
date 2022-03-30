# Alien-vs-Predator-episode-4

## context du projet: 
L'épisode 3 a démontré que la technique de "transfer learning" pouvait augmenter de manière drastique les performances d'un CNN à effectuer de la classification d'images même sur un petit jeu de données. Il existe toutefois un léger sur-apprentissage résiduel. L'objectif de ce brief est de combiner la technique de "data augmentation" étudiée dans l'épisode 2 avec la technique de "features extraction" vue dans l'épisode 3 dans le but d'éliminer ce très léger sur-apprentissage résiduel ainsi que d'augmenter encore la précision du CNN.

Pour cela :

- Charger à nouveau le modèle VGG-16
  - N.B. Ne pas oublier de "freezer" VGG-16 !
- Concaténer VGG-16 avec par exemple le perceptron multi-couches suivant
​

  - model.add(layers.Dense(units=256, activation='relu', input_dim=4 * 4 * 512))

  - model.add(layers.Dense(units=1, activation='sigmoid'))

​

N.B. Notons que l'architecture de ce MLP peut être optimisée : vous pouvez notamment tester un autre nombre de neurones dans la couche cachée.

​

- Entrainer l'ensemble en utilisant la technique de "data augmentation"
  - ATTENTION AUX TEMPS DE CALCULS !!!
