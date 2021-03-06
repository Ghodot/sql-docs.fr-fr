---
title: Liste de vérification de préparation pour l’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0e056c95-ba06-413e-8dc1-4d411a447c3b
caps.latest.revision: 9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0bed960058bdc9120089d89a32a3ede0bf2f3160
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37232499"
---
# <a name="checklist-of-preparation-for-data-mining"></a>Liste de vérification : préparation pour l'exploration de données
  Bien que les compléments d'exploration de données facilitent et agrémentent la création de modèles et leur expérimentation, lorsque vous devez obtenir des résultats reproductibles et utilisables, vous devez prévoir suffisamment de temps pour formuler les critères fondamentaux pour l'entreprise, ainsi que pour obtenir et préparer les données. Cette section fournit une liste de vérification pour vous aider à planifier les tâches d'inspection, et décrit les problèmes courants.  
  
## <a name="checklist-of-data-preparation"></a>Liste de vérification de la préparation des données  
 **J’ai identifié un résultat bien défini.**  
 Disposer d'un plan pour la façon dont vous allez utiliser les résultats. Les différents types de modèles génèrent des résultats différents. Un modèle de série chronologique génère des valeurs d'une série dans le futur, qui sont facilement compréhensible et utilisables. D'autres modèles génèrent des jeux complexes qui doivent être analysés par des experts techniques pour obtenir la plus grande valeur.  
  
-   Quel résultat voulez-vous ?  
  
-   Pouvez-vous définir la sortie en tant que colonne ou valeur unique, ou tout autre résultat utilisable ?  
  
-   Quels sont les critères pour savoir que le modèle est utile ?  
  
-   Comment allez-vous utiliser et interpréter ces résultats ?  
  
-   Pouvez-vous mapper les nouvelles données d'entrée aux résultats attendus ?  
  
 **Je sais la signification, types de données et la distribution des données d’entrée.**  
 Prenez le temps d'explorer et comprendre vos données source. Il est important que les personnes qui examinent le modèle comprennent le type de données d'entrée qui a été utilisé et sachent interpréter les types de données et la variabilité, ainsi que l'équilibre et la qualité.  
  
-   De quel volume de données disposez-vous ? Les données sont-elles suffisantes pour la modélisation ?  
  
     Une grande quantité de données n'est pas nécessaire ; un volume plus petit et équilibré peut s'avérer plus approprié.  
  
-   Les données proviennent-elles de plusieurs sources, ou d'une seule source ?  
  
-   Est-ce-que les données sont déjà traitée et nettoyées ? Des données d'entrée supplémentaires sont-elles disponibles ?  
  
-   Savez-vous comment elles ont été manipulées avant réception, comment elles ont été tronquées, synthétisées ou converties ?  
  
-   Les données d'entrée ont-elles des exemples de résultats qui peuvent être utilisés pour l'apprentissage ?  
  
 **Je comprends le niveau de l’intégrité des données que nous avons et le niveau que nous avons besoin.**  
 Des données incorrectes peuvent affecter la qualité du modèle ou empêcher la génération du modèle. Vous devez avoir une bonne compréhension de la distribution et de la signification des données, et de la manière dont elles sont parvenues à cet état. Vous devrez comprendre s'il est possible ou approprié de simplifier les données par étiquetage, en tronquant des types de données numériques ou par synthèse.  
  
-   Étiquettes de données : sont-elles claires et correctes ?  
  
-   Types de données : sont-ils appropriés et ont-ils été modifiés ?  
  
-   Avez-vous trié, nettoyé ou ignoré les données incorrectes ?  
  
     Avez-vous vérifié qu'il n'y a pas de doublons ?  
  
-   Comment allez-vous gérer les valeurs manquantes ? Les valeurs manquantes ont-elles une signification ?  
  
-   Avez-vous vérifié les sources pour déterminer si des erreurs ont été introduites lors du processus d'importation ?  
  
     Où sont stockées les données d'entrée ? Combien de temps resteront-elles disponibles ?  
  
     Existe-t-il un dictionnaire des données ? Pouvez-vous en créer un ?  
  
-   Si vous avez combiné des jeux de données, avez-vous recherché plusieurs colonnes représentant les mêmes données ?  
  
 **Je sais où les données sources sont stockées, d'où elles proviennent et comment elles sont traitées. Le processus peut être répété facilement si nécessaire.**  
 Les jeux de données uniques sont très bien pour les expériences, mais si vous souhaitez déplacer le modèle en production, vous souhaiterez envisager à l'avance la manière dont le processus de nettoyage peut être appliqué aux données opérationnelles. En outre, si vous disposez de données opérationnelles, vous devez savoir comment elles ont été modifiées avant obtention (comment elles ont été arrondies ou synthétisées).  
  
-   Voulez-vous être en mesure de répéter l'expérience ?  
  
-   Quels outils utiliserez-vous pour préparer les données dans un format qui prend en charge l'analyse de données ? Peut-il être automatisé ou avez-vous besoin de quelqu'un pour la vérification et le nettoyage dans Excel ?  
  
-   Si les données proviennent d'un autre système, serez-vous en mesure de capturer et suivre les filtres appliqués ?  
  
-   Votre infrastructure de traitement des données peut-elle également appliquer des algorithmes d'apprentissage automatique, réaliser des tests et visualiser les résultats ?  
  
 **Nous sommes entendus sur la granularité souhaitée des prédictions et nos données ont été modifiées pour ces unités de sortie.**  
 Décidez de la granularité des résultats que vous recherchez avant de préparer des données. Par exemple, avez-vous besoin des prédictions de ventes chaque jour ou pour chaque trimestre ? Envisagez éventuellement de configurer différentes structures de données pour les mêmes données de façon à gérer différents niveaux de résumé.  
  
-   Quelle est l'unité de mesure ou l'unité de temps actuelle ?  
  
     Quelle unité souhaitez-vous utiliser dans les résultats ?  
  
-   Il est possible de définir une unité de base (par exemple, jour / heure / min / appel d’instruction) pour toutes les données d’entrée ?  
  
     Voulez-vous effectuer le cumul aux unités supérieures ?  
  
-   Est-ce-que les catégories sont étiquetées de façon cohérente ? Est-il facile d'ajouter ou de supprimer des catégories ?  
  
 **Notre conception expérimentale est renouvelable et reproductible.**  
 Tenez compte des stratégies pour analyser et valider vos résultats et planifier la capturer d'un instantané des données, pour garantir que vous pouvez tracer les effets sur les données. Si une valeur de départ aléatoire est utilisée, les résultats peuvent légèrement différer. Cela peut rendre la difficile la comparaison et la validation des modèles.  
  
-   Si vous apportez de nombreuses modifications personnalisées aux données, que se passera-t-il la prochaine fois que vous souhaiterez créer le modèle ?  
  
-   Une procédure manuelle ou un processus approuvé que vous devez utiliser pour traiter les données d'entrée et obtenir le résultat souhaité a-t-il déjà été défini ?  
  
-   Avez-vous décidé d'utiliser une valeur initiale pour le modèle ?  
  
 **Nous disposent de connaissances de domaine pour valider les résultats, ou avoir accès à des experts techniques qui peuvent nous conseiller.**  
 Prenez le temps de valider les variables, le modèle et les résultats. Obtenez de l'aide auprès d'experts pour évaluer les interactions et les résultats. Toutefois, ne laissez aucun des hypothèses remplacer une preuve. Soyez ouvert aux résultats nouveaux et inattendus.  
  
-   La connaissance de domaine est-elle disponible pour faciliter le filtrage des données et réduire le bruit des données d'entrée ?  
  
-   Est-ce-que les experts en matière de domaine aident à comprendre et interpréter les résultats et proposent des améliorations ?  
  
## <a name="see-also"></a>Voir aussi  
 [Choix des données pour l’exploration de données](choosing-data-for-data-mining.md)  
  
  
