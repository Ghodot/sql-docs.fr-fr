---
title: Didacticiel de Analysis Services Adventure Works (1400) | Microsoft Docs
ms.date: 08/27/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7abd968db3aacbb71ed238e3f6ae6b857c8b1d99
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43084712"
---
# <a name="tabular-modeling-1400-compatibility-level"></a>Modélisation tabulaire (niveau de compatibilité 1400)

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

Ce didacticiel inclut des leçons sur la façon de créer et déployer un modèle tabulaire à le [niveau de compatibilité 1400](../tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md). Si vous découvrez Analysis Services et la modélisation tabulaire, suivre ce didacticiel est le moyen le plus rapide pour savoir comment créer et déployer un modèle tabulaire de base à l’aide de Visual Studio. Une fois que vous disposez des prérequis sur place, il doit prendre deux ou trois heures.  
  
## <a name="what-you-learn"></a>Vous découvrez   
  
-   Comment créer un nouveau projet de modèle tabulaire à le **niveau de compatibilité 1400** dans Visual Studio avec SSDT.
  
-   Comment importer des données à partir d’une base de données relationnelle dans une base de données espace de travail de projet modèle tabulaire.  
  
-   Créer et gérer des relations entre des tables dans le modèle.  
  
-   Comment créer des colonnes calculées, les mesures et indicateurs de Performance clés qui permettent aux utilisateurs d’analyser des métriques métier critiques.  
  
-   Comment créer et gérer des perspectives et des hiérarchies qui permettent aux utilisateurs plus facilement parcourir les données de modèle en fournissant des entreprises et les points de vue spécifiques à l’application.  
  
-   Créer des partitions qui divisent les données des tables en plus petites parties logiques pouvant être traitées indépendamment des autres partitions.  
  
-   Sécuriser les objets et les données du modèle en créant des rôles à l'aide des membres utilisateurs.  
  
-   Comment déployer un modèle tabulaire sur un **Azure Analysis Services** server ou **SQL Server Analysis Services 2017** serveur à l’aide de SSDT.  
  
## <a name="prerequisites"></a>Prérequis  

Pour suivre ce didacticiel, vous devez :  
  
-   Un serveur Azure Analysis Services ou un serveur SQL Server 2017 Analysis Services en mode tabulaire. Inscrivez-vous pour bénéficier d’un [version d’évaluation d’Azure Analysis Services](https://azure.microsoft.com/services/analysis-services/) et [créer un serveur](https://docs.microsoft.com/azure/analysis-services/analysis-services-create-server) ou téléchargez gratuitement [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).

-   Un [Azure SQL Data Warehouse](https://docs.microsoft.com/azure/sql-data-warehouse/create-data-warehouse-portal) avec la **base de données exemple AdventureWorksDW**, ou un serveur local SQL Data Warehouse avec un [base de données exemple AdventureWorksDW](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Lorsque vous installez une base de données AdventureWorksDW à un entrepôt de données locale SQL Server, utilisez la version de base de données d’exemple qui correspond avec votre version de serveur. 

    **Important :** si vous installez la base de données à un entrepôt de données locale SQL Server et que vous déployez votre modèle sur un serveur Azure Analysis Services, un [passerelle de données locale](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway) est requis.

-   La dernière version de [SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx). Ou, si vous disposez déjà de Visual Studio 2017, vous pouvez télécharger et installer [projets Microsoft Analysis Services](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects) package (VSIX). Pour ce didacticiel, les références à SSDT et Visual Studio sont synonymes. 

-   La dernière version de [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).    

-   Une application cliente telle que [Power BI Desktop](https://powerbi.microsoft.com/desktop/) ou Excel. 

## <a name="scenario"></a>Scénario  

Ce didacticiel est basé sur Adventure Works Cycles, une société fictive. Adventure Works est une société de fabrication volumineuse, multinationale qui produit et distribue des bicyclettes, des parties et des accessoires pour les marchés d’Amérique du Nord, Europe et Asie. La société emploie 500 personnes. En outre, Adventure Works emploie plusieurs équipes commerciales régionales pour couvrir son marché. Votre projet consiste à créer un modèle tabulaire pour les utilisateurs ventes et marketing analyser les données des ventes Internet dans la base de données AdventureWorksDW.  
  
Pour suivre ce didacticiel, vous devez suivre plusieurs leçons. Dans chaque leçon, il existe des tâches. Chaque tâche dans l’ordre est nécessaire pour terminer la leçon. Tandis que dans une leçon donnée il peut y avoir plusieurs tâches qui aboutissent au même résultat, mais comment vous effectuez chaque tâche est légèrement différente. Cette méthode affiche il existe souvent plusieurs façons d’effectuer une tâche et à vous demander à l’aide des compétences que vous avez appris dans les tâches et les leçons précédentes.  
  
L’objectif des leçons consiste à vous guide tout au long de la création d’un modèle tabulaire de base à l’aide de la plupart des fonctionnalités incluses dans SSDT. Chaque leçon découle de la leçon précédente, c'est pourquoi vous devez effectuer les leçons dans l'ordre.
  
Ce didacticiel ne fournit pas de leçons sur la gestion d’un serveur dans le portail Azure, la gestion d’un serveur ou une base de données à l’aide de SSMS, ou à l’aide d’une application cliente pour parcourir les données de modèle. 


## <a name="lessons"></a>Leçons  

Ce didacticiel inclut les leçons suivantes :  
  
|Leçon|Durée estimée|  
|----------|------------------------------|  
|[1 - créer un nouveau projet de modèle tabulaire](../tutorial-tabular-1400/as-lesson-1-create-a-new-tabular-model-project.md)|10 minutes|  
|[2 - Obtenir des données](../tutorial-tabular-1400/as-lesson-2-get-data.md)|10 minutes|  
|[3 - Marquer comme table de dates](../tutorial-tabular-1400/as-lesson-3-mark-as-date-table.md)|3 minutes|  
|[4 - Créer des relations](../tutorial-tabular-1400/as-lesson-4-create-relationships.md)|10 minutes|  
|[5 - Créer des colonnes calculées](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md)|15 minutes|
|[6 - Créer des mesures](../tutorial-tabular-1400/as-lesson-6-create-measures.md)|30 minutes|  
|[7 - créer des indicateurs de Performance clés (KPI)](../tutorial-tabular-1400/as-lesson-7-create-key-performance-indicators.md)|15 minutes|  
|[8 - Créer des perspectives](../tutorial-tabular-1400/as-lesson-8-create-perspectives.md)|5 minutes|  
|[9 - Créer des hiérarchies](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md)|20 minutes|  
|[10 - Créer des partitions](../tutorial-tabular-1400/as-lesson-10-create-partitions.md)|15 minutes|  
|[11 - Créer des rôles](../tutorial-tabular-1400/as-lesson-11-create-roles.md)|15 minutes|  
|[12 - Analyser dans Excel](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md)|5 minutes| 
|[13 - Déployer](../tutorial-tabular-1400/as-lesson-13-deploy.md)|5 minutes|  
  
## <a name="supplemental-lessons"></a>Leçons supplémentaires  

Ces leçons ne sont pas nécessaires pour suivre ce didacticiel, mais il peuvent être utiles pour mieux comprendre avancés modèles tabulaires fonctionnalités de création.  
  
|Leçon|Durée estimée|  
|----------|------------------------------|  
|[Lignes de détails](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md)|10 minutes|
|[Sécurité dynamique](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)|30 minutes|
|[Hiérarchies déséquilibrées](../tutorial-tabular-1400/as-supplemental-lesson-ragged-hierarchies.md)|20 minutes| 

  
## <a name="next-steps"></a>Étapes suivantes  

Pour commencer, consultez [leçon 1 : créer un nouveau projet de modèle tabulaire](../tutorial-tabular-1400/as-lesson-1-create-a-new-tabular-model-project.md).  
  
  
  

