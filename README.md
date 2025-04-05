# 3--CNN_covid

Pour obtenir le dataset cliquez sur ce lien: https://kdrive.infomaniak.com/app/drive/1387336/redirect/7

# 📸 Modèle de Classification d'Images avec Keras

Ce projet utilise un modèle de réseau de neurones convolutif (CNN) pour la classification d'images. Le modèle est entraîné pour différencier deux classes d'images (par exemple, 'covid' et 'normal').

## 🛠️ Prérequis

Avant de commencer, assurez-vous d'avoir les bibliothèques suivantes installées :
- `tensorflow`
- `matplotlib`
- `seaborn`
- `numpy`
- `pandas`
- `sklearn`

Vous pouvez les installer avec la commande suivante :

```bash
pip install tensorflow matplotlib seaborn numpy pandas scikit-learn
```

## 🚀 Fonctionnement

### 1. Construction du Modèle

Le modèle CNN est constitué des étapes suivantes :
- **Convolution** : Filtrage des caractéristiques de l'image.
- **MaxPooling** : Réduction de la dimensionnalité pour plus d'efficacité.
- **Dropout** : Désactivation aléatoire de neurones pour éviter le surapprentissage (overfitting).
- **Flatten** : Conversion des données en vecteur unidimensionnel.
- **Dense** : Couche entièrement connectée avec activation ReLU pour la première couche et Sigmoid pour la dernière couche.

### 2. Compilation du Modèle

Le modèle utilise :
- **Adam** comme optimiseur
- **Binary Crossentropy** comme fonction de perte
- **Accuracy** comme métrique d'évaluation

### 3. Entraînement du Modèle

L'entraînement utilise un `ImageDataGenerator` pour augmenter les images d'entraînement (rotation, zoom, déplacement, etc.) et pour normaliser les pixels. Un modèle est sauvegardé après chaque époque si sa précision est la meilleure (`ModelCheckpoint`), et l'entraînement s'arrête tôt si la perte de validation n'améliore plus après 2 époques (`EarlyStopping`).

### 4. Visualisation des Résultats

Des graphiques sont tracés pour observer l'évolution de la perte et de la précision du modèle pendant l'entraînement. Les graphiques incluent :
- **Loss** : Evolution de la perte durant l'entraînement.
- **Accuracy** : Evolution de la précision durant l'entraînement.

### 5. Évaluation du Modèle

Après l'entraînement, le modèle est évalué avec un rapport de classification (`classification_report`) et une matrice de confusion (`confusion_matrix`) pour observer la performance sur les données d'entraînement.

### 6. Prédictions

Le modèle peut prédire la classe d'une image donnée. Une image est chargée, prétraitée et ensuite prédite pour déterminer si elle appartient à la classe "covid" ou "normal".

## 📊 Exemple de Résultat

Lors de l'évaluation sur les images d'entraînement, les résultats obtenus peuvent être comme suit :

```
              precision    recall  f1-score   support
           0       0.38      1.00      0.55        94
           1       0.00      0.00      0.00       155

    accuracy                           0.38       249
   macro avg       0.19      0.50      0.27       249
weighted avg       0.14      0.38      0.21       249
```

Une matrice de confusion peut également être générée :

![Matrice de confusion](confusion_matrix.png)

### 7. Prédiction d'une Nouvelle Image

Pour prédire la classe d'une nouvelle image :

```python
test_image = image.load_img('pred.jpeg', target_size=(64,64))
test_image = image.img_to_array(test_image)
test_image = np.expand_dims(test_image, axis=0)
result = classifier.predict(test_image)

for key, value in training_set.class_indices.items():
    if result == value:
        print('La classe prédite est:', key)
```

## 📚 Conclusion

Ce modèle de classification d'images permet de différencier des classes basées sur des caractéristiques visuelles. Il peut être amélioré par des techniques supplémentaires comme la régularisation, l'ajustement des hyperparamètres et l'augmentation des données. Utilisez ce modèle comme base pour des applications de reconnaissance d'images.

## 📥 Contribution

Les contributions sont les bienvenues ! Si vous avez des idées d'améliorations ou des corrections, n'hésitez pas à soumettre une pull request.

## 📑 Licence

Ce projet est sous licence MIT.
```

Avec ce `README.md`, vous avez un aperçu complet de l'utilisation et des résultats du modèle de classification d'images ! 😊
```
✍️ Auteur
Fouejio Francky Joël
