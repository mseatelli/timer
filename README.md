# 🍳 Ma Cuisine - Minuteur Culinaire Mobile-First

Une application web légère et intuitive conçue pour simplifier la gestion des temps de cuisson en cuisine. Optimisée spécifiquement pour **Chrome Mobile**, cette application permet de gérer des favoris, des catégories personnalisées et propose un calculateur de temps de cuisson pour les viandes.

![Version](https://img.shields.io/badge/version-1.2-orange)
![Licence](https://img.shields.io/badge/licence-MIT-green)

## ✨ Fonctionnalités

* **Gestion des Favoris** : Enregistrez vos temps de cuisson habituels (riz, pâtes, œufs coque, etc.).
* **Système de Catégories** : Organisez vos cuissons par type d'aliments.
* **Mode Mobile-First** : Interface conçue pour une utilisation à une main en cuisine.
* **Alarme Intelligente** : Alertes sonores et visuelles (clignotement rouge) une fois le temps écoulé.
* **Calculateur de Viandes** : Temps automatique selon le type de viande (bœuf, poulet, veau) et le poids.
* **Sauvegarde Persistante** : Utilise le `LocalStorage` pour conserver vos données sans serveur.
* **Portabilité** : Fonctions d'exportation et d'importation (via JSON) pour transférer vos données entre appareils.

## 🛠️ Solutions aux contraintes Chrome Mobile

Ce projet intègre des solutions spécifiques pour surmonter les limitations des navigateurs mobiles :
* **AudioContext API** : Utilisation d'oscillateurs pour générer des bips sonores, contournant les restrictions de chargement de fichiers audio sur mobile.
* **Interface Adaptative** : Remplacement des listes horizontales par des menus déroulants (`<select>`) pour une compatibilité tactile 100%.
* **Import Manuel** : Système de copier-coller JSON pour l'importation, évitant les blocages de sécurité des sélecteurs de fichiers Android/iOS.

## 🚀 Installation rapide

1.  Téléchargez le fichier `index.html`.
2.  Ouvrez-le simplement dans votre navigateur mobile.
3.  **Astuce Chrome** : Pour une expérience optimale, utilisez l'option "Ajouter à l'écran d'accueil" dans le menu de Chrome pour l'utiliser comme une application native.

## 📋 Comment utiliser l'import/export ?

1.  **Export** : Dans l'onglet **Réglages**, cliquez sur **Exporter**. Un fichier `sauvegarde.json` sera téléchargé.
2.  **Import** : 
    * Ouvrez votre fichier de sauvegarde avec un éditeur de texte.
    * Copiez l'intégralité du code.
    * Collez-le dans la zone "Importation Manuelle" de l'application et validez.

## 💻 Technologies utilisées

* **HTML5**
* **CSS3** (Variables CSS, Animations @keyframes)
* **JavaScript Vanilla** (Pas de bibliothèques externes pour une légèreté maximale)
* **Web Audio API**

---
Développé avec ❤️ pour les passionnés de cuisine.
