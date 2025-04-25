# Projet ECG - Débruitage d'électrocardiogrammes

Ce projet vise à restaurer des signaux ECG bruités à l'aide d'un modèle d'autoencodeur hybride combinant convolutions et transformeurs.

---

## Données & Bruit

Les signaux ECG ont été corrompus par différents types de bruits :
- **Bruit gaussien**
- **Bruit de mouvement**
- **Bruit de respiration**
- **Inférences EDF**

Le rapport signal/bruit (SNR) varie **aléatoirement entre 6 et 24 dB**, avec une **pondération en faveur des bruits faibles**.

> **Exemple** : Signal faiblement bruité (SNR = 22 dB) par du mouvement  
> ![signal bruité](https://github.com/user-attachments/assets/b5ecb202-3b36-4ea4-8369-414fee8ddf5b)

---

## Modèle

Le modèle se compose de deux parties :

- **Encodage** : `Convolutions + Transformer`
- **Décodage** : `Convolutions`

- **Fonction de perte** : Mean Squared Error (MSE)

---

## Résultats

- **Entraînement sur 3 epochs** :
  - Train MSE : `0.0046`
  - Validation MSE : `0.0019`
  - Test MSE : `0.0048`

> **Exemple** : Résultat du débruitage par le modèle  
> ![signal reconstruit](https://github.com/user-attachments/assets/54c33e49-252c-4866-b522-a0f991376a6a)

---

## Robustesse aux bruits forts

Le modèle a été testé sur **10 échantillons** avec un SNR compris entre **2 et 7 dB**.

- MSE sur ces échantillons : `0.0039`

> **Exemple** : Reconstruction sur données fortement bruitées  
> ![robustesse](https://github.com/user-attachments/assets/e950e791-28f3-4420-a0c7-ef98f57d067f)

---
