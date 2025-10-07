📋 CAHIER DES CHARGES - Chronomulti-Cuisson
🎯 Objectif
Application web de gestion de minuteries multiples pour la cuisson, permettant de gérer plusieurs préparations culinaires simultanément.

🏗️ ARCHITECTURE GÉNÉRALE
Technologies

HTML5 - Structure
CSS3 - Design responsive et moderne
JavaScript Vanilla - Logique applicative
Aucune dépendance externe

Design

Thème sombre (fond #1a1a1a)
Couleur principale : Orange (#ff6b35)
Police : Segoe UI
Responsive : Adapté mobile/tablette/desktop


📑 STRUCTURE EN ONGLETS
1️⃣ Onglet "⏱️ Minuteries"
Fonction : Afficher toutes les minuteries actives
Éléments affichés par minuterie :

Nom de la minuterie
Temps restant (format HH:MM:SS ou MM:SS)
Barre de progression visuelle
Boutons de contrôle :

⏸️ Pause / ▶️ Reprendre
⏹️ Arrêter



État par défaut : "Aucune minuterie active"

2️⃣ Onglet "⭐ Favoris"
Fonction : Accès rapide aux recettes pré-configurées
Catégories présentes :
🥚 Cuisson des Œufs

Œuf à la coque : 3 min
Œuf mollet : 6 min
Œuf dur : 9 min
Œuf poché : 3 min
Œuf au plat : 4 min

🍝 Pâtes & Riz

Pâtes al dente : 10 min
Riz basmati : 12 min
Riz complet : 25 min

🥦 Légumes

Pommes de terre vapeur : 20 min
Brocolis vapeur : 5 min
Carottes vapeur : 8 min

🥩 Steaks à la Poêle

Steak bleu : 1 min
Steak saignant : 2 min
Steak à point : 3 min
Steak bien cuit : 3 min 30

Interaction : Clic sur un favori → Lance la minuterie automatiquement et bascule sur l'onglet "Minuteries"

3️⃣ Onglet "➕ Nouvelle Minuterie"
Fonction : Créer une minuterie personnalisée
Champs du formulaire :

Nom de la minuterie (texte libre)
Durée :

Heures (nombre)
Minutes (nombre)
Secondes (nombre)



Validation :

Durée totale > 0 secondes obligatoire
Affichage d'une alerte si durée invalide

Action : Bouton "🚀 Démarrer la minuterie"

Crée la minuterie
Réinitialise le formulaire
Bascule sur l'onglet "Minuteries"


4️⃣ Onglet "🥩 Cuisson au Poids"
Fonction : Calculer automatiquement le temps de cuisson selon le type et le poids
Champs du formulaire :

Type de viande (select) :

Bœuf
Agneau
Porc
Poulet


Morceau (select) :

Rôti
Filet
Gigot
Épaule


Poids (nombre, en kg, step 0.1)
Cuisson désirée (select) :

Bleu (bœuf uniquement)
Saignant
À point
Bien cuit



Base de données des temps (minutes/kg) :
Bœuf : Bleu 30, Saignant 40, À point 50, Bien cuit 60
Agneau : Saignant 45, À point 55, Bien cuit 65
Porc : À point 55, Bien cuit 70
Poulet : Bien cuit 45
Calcul automatique :

Temps = Poids × Temps/kg
Affichage : "Xh Ymin" ou "Ymin"

Action : Bouton "📌 Créer la minuterie"

Génère un nom automatique : "[Morceau] [Type] [Poids]kg ([Cuisson])"
Lance la minuterie
Bascule sur l'onglet "Minuteries"


⚙️ FONCTIONNALITÉS TECHNIQUES
Gestion des Minuteries
Structure de données :
javascript{
  id: timestamp unique,
  name: string,
  totalSeconds: number,
  remainingSeconds: number,
  isRunning: boolean,
  interval: setInterval reference
}
Mécanisme :

Décompte : setInterval à 1 seconde
Mise à jour affichage en temps réel
Stockage en mémoire (tableau activeTimers)

Contrôles

Pause : isRunning = false (l'interval continue mais le décompte s'arrête)
Reprendre : isRunning = true
Arrêter : clearInterval + suppression du tableau

Notifications de fin
Audio :

Génération d'un son via Web Audio API
Oscillateur sinusoïdal 800Hz pendant 0.5s

Notification navigateur :

Si permission accordée
Titre : "⏰ [Nom minuterie]"
Corps : "Votre minuterie est terminée !"

Alerte visuelle :

Animation pulse (opacité 1 → 0.5 → 1)
Alert JavaScript

Permission notifications : Demandée au chargement de la page

🎨 ÉLÉMENTS VISUELS
Cartes de minuterie

Fond #3d3d3d
Bordure gauche orange 4px
Padding 15px
Border-radius 10px

Barre de progression

Hauteur 6px
Fond #555
Remplissage orange progressif
Transition 1s linear

Boutons favoris

Grid responsive (min 150px par carte)
Icône emoji grande taille (2.5em)
Effet hover : scale 1.05 + bordure orange
Transition 0.3s

Boutons de contrôle

Pause : Orange (#ffa500)
Stop : Rouge (#ff4444)
Reprendre : Vert (#44ff44)
Effet hover : translateY(-2px)


📱 RESPONSIVE
Breakpoint : 600px
En dessous de 600px :

Onglets : flex-direction column
Inputs temps : flex-direction column
Contrôles minuterie : flex-direction column


🔒 RESTRICTIONS
Stockage

PAS de localStorage/sessionStorage
Données uniquement en mémoire (variables JavaScript)
Perte des données au rechargement

Format temps

Affichage HH:MM:SS si ≥ 1 heure
Affichage MM:SS si < 1 heure
Padding zéro (exemple : 09:05)


🎯 PARCOURS UTILISATEUR
Scénario 1 : Minuterie rapide

Clic onglet "Favoris"
Clic sur "Œuf dur"
→ Minuterie 9 min lancée
Notification à la fin

Scénario 2 : Minuterie personnalisée

Clic onglet "Nouvelle Minuterie"
Saisie nom + durée
Clic "Démarrer"
→ Minuterie lancée

Scénario 3 : Cuisson au poids

Clic onglet "Cuisson au Poids"
Sélection viande/poids/cuisson
Calcul automatique affiché
Clic "Créer la minuterie"
→ Minuterie lancée avec nom auto

Scénario 4 : Multi-cuisson

Lancer plusieurs minuteries
Vue simultanée dans onglet "Minuteries"
Contrôle individuel (pause/stop)
Notifications successives


🐛 GESTION DES ERREURS

Durée = 0 → Alerte "Veuillez définir une durée valide"
Combinaison viande/cuisson invalide → Masquer résultat calcul
Audio non supporté → Log console (pas d'erreur bloquante)


✅ POINTS DE VALIDATION

✅ 4 onglets fonctionnels
✅ Création minuterie simple
✅ 20+ favoris pré-configurés
✅ Calcul automatique au poids
✅ Gestion simultanée multiple minuteries
✅ Pause/Reprendre/Arrêter
✅ Barre de progression
✅ Notifications (son + navigateur + alerte)
✅ Design responsive
✅ Aucune dépendance externe


Version : 1.0
Date : Octobre 2025
Statut : ✅ Complet et fonctionnel
