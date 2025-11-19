# 📚 Guide d’utilisation de l’application

## Présentation Générale
L'application Classifieur de l’activité selon la nomenclature est un outil de classification intelligente qui utilise les algorithmes Naïve Bayes Multinomial, Régression Logistique et Support Vector Machine, optimisés pour CPU. Elle permet de classifier automatiquement des activités déclarées selon une structure hiérarchique à quatre niveaux : Grand poste, Section, Groupe et Classe.

## Démarrage rapide

### Chargement des Données
Méthode 1 : Utilisez le fichier Data.xlsx par défaut (placé dans le répertoire de l'application)
Méthode 2 : Uploadez votre propre fichier Excel via le bouton "Browse files" dans la sidebar

### Structure requise du fichier :
Colonnes obligatoires : reponse, langage, Classe, Grand poste, Section, Groupe

### Configuration Initiale
Niveau de prédiction : Sélectionnez jusqu'à quel niveau hiérarchique vous souhaitez classifier
SMOTE : Activez/désactivez la correction des déséquilibres de classes
Modèles sauvegardés : Utilisez les modèles existants ou forcez un ré-entraînement

## Modes de Prédiction

### Prédiction Manuelle 
Pour classifier un texte unique :
1.	Saisissez votre texte dans la zone de texte dédiée
2.	Choisissez le mode :
Prédiction Libre : Classification sans contraintes
Prédiction Guidée : Respecte les sélections hiérarchiques de la sidebar
3.	Analysez les résultats :
Prédictions par niveau hiérarchique
Niveaux de confiance colorés (🟢 Élevé, 🟡 Moyen, 🔴 Faible)
Différenciation valeurs filtrées vs prédites

### Prédiction par Lot 
Pour classifier plusieurs textes simultanément :
1.	Uploadez votre fichier (formats supportés : CSV, Excel, TXT)
2.	Configurez le traitement :
Sélectionnez la colonne contenant les textes
Ajustez la taille du lot (10-500 textes)
3.	Lancez le traitement et suivez la progression
4.	Exportez les résultats en CSV ou Excel avec :
Prédictions complètes
Niveaux de confiance
Correspondances avec données sources
Métadonnées de traitement

### Mise à Jour du Modèle 
Pour améliorer les performances :
1.	Identifiez une erreur de classification
2.	Ajoutez une correction :
Texte mal classifié
Classification correcte (niveaux hiérarchiques)
3.	Validez la correction dans la liste d'attente
4.	Mettez à jour le modèle pour intégrer les corrections

## Navigation Hiérarchique

### Sélecteurs Hiérarchiques (Sidebar)
La sidebar permet de filtrer et guider les prédictions :
1.	Sélectionnez un Grand poste → les Sections disponibles se mettent à jour
2.	Choisissez une Section → les Groupes correspondants s'affichent
3.	Sélectionnez un Groupe → les Classes disponibles apparaissent

### Fonctionnalités avancées :
"Tous" : Permet de ne pas contraindre un niveau
Classification unique : L'application détecte automatiquement les chemins menant à une seule classe possible
Filtrage contextuel : Les modèles s'entraînent uniquement sur les données filtrées

## Analyse des Résultats

### Indicateurs de Performance
F1-Score par niveau : Qualité des modèles (🟢 >0.9, 🟡 >0.8, 🟠 >0.7, 🔴 <0.7)
Confiance par prédiction : Fiabilité de chaque classification
Correspondances : Comparaison prédictions vs données sources (si disponibles)

### Visualisations
Graphiques de confiance : Diagrammes en barres pour les niveaux prédits
Tableaux comparatifs : Analyse détaillée prédictions vs sélections
Statistiques de lot : Métriques globales pour les traitements par lot

## Gestion des Modèles

### Sauvegarde Automatique
Les modèles sont automatiquement sauvegardés après entraînement
Nommage basé sur le hash des données et niveau de prédiction
Réutilisation possible sans ré-entraînement

### Optimisations
MultinomialNB : Algorithme sélectionné pour performance CPU
SMOTE : Gestion automatique des déséquilibres de classes
Validation croisée : Optimisation des hyperparamètres
Cache intelligent : Évite les recalculs inutiles

## Export des Résultats

### Formats Disponibles
CSV : Format universel, toutes les colonnes
Excel : Formaté avec mise en forme conditionnelle

### Colonnes Incluses
Identifiants : ID_Prediction, Horodatage
Données sources : Toutes les colonnes originales
Prédictions : Par niveau hiérarchique avec confiance
Métadonnées : Contexte de filtrage, type de prédiction
Analyses : Correspondances, statistiques

## Bonnes Pratiques

### Pour de Meilleures Performances
1.	Qualité des données : Textes clairs et non ambigus
2.	Cohérence hiérarchique : Respect de la structure arborescente
3.	Corrections régulières : Améliorez le modèle progressivement
4.	Filtrage contextuel : Utilisez les sélections pour affiner les prédictions

### Dépannage Courant
Fichier non chargé : Vérifiez la structure des colonnes
Modèles non entraînés : Lancez manuellement l'entraînement
Prédictions incorrectes : Ajoutez des corrections
Performances médiocres : Activez SMOTE pour les déséquilibres

## Cas d'Usage Recommandés

### Idéal pour :
Classification de descriptions d'activités économiques
Catégorisation de produits/services
Organisation hiérarchique de contenu textuel
Nettoyage et standardisation de bases de données

### Limitations :
Performance dépendante de la qualité des données d'entraînement
Classification principalement en français et anglais
Structure hiérarchique fixe à 4 niveaux

## Conseils Avancés
1.	Commencez simple : Testez avec la prédiction manuelle avant les lots
2.	Utilisez le filtrage pour les cas complexes ou spécifiques
3.	Exportez systématiquement pour garder une trace des traitements
4.	Corrigez progressivement pour améliorer continuellement le modèle

## Support : Consultez la section "Aide" dans l'interface pour plus d'informations contextuelles.
Dernière mise à jour : 19/11/2025 Version optimisée CPU
