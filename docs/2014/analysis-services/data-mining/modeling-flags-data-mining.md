---
title: Indicateurs de modélisation (exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- attributes [data mining]
- data types [data mining]
- REGRESSOR flag
- MODEL_EXISTENCE_ONLY flag
- REGRESSOR column
- columns [data mining], modeling flags
- NOT NULL modeling flag
- modeling flags [data mining]
- null values [Analysis Services]
- MODEL_EXISTENCE_ONLY column
- coding [Data Mining]
ms.assetid: 8826d5ce-9ba8-4490-981b-39690ace40a4
caps.latest.revision: 48
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 85abe1acb2fa12208ebf83541bd030646c67ddbc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155410"
---
# <a name="modeling-flags-data-mining"></a>Indicateurs de modélisation (Exploration de données)
  Vous pouvez utiliser des indicateurs de modélisation dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour fournir à un algorithme d’exploration de données des informations supplémentaires portant sur les données définies dans une table de cas. Ces informations permettent à l'algorithme de construire un modèle d'exploration de données plus précis.  
  
 Certains indicateurs de modélisation sont définis au niveau de la structure d'exploration de données, tandis que d'autres sont définis au niveau de la colonne du modèle d'exploration de données. Par exemple, le `NOT NULL` indicateur de modélisation est utilisé avec les colonnes de structure d’exploration de données. Vous pouvez définir des indicateurs de modélisation supplémentaires sur les colonnes du modèle d'exploration de données, en fonction de l'algorithme que vous utilisez pour créer le modèle.  
  
> [!NOTE]  
>  Les plug-ins tiers peuvent posséder d'autres indicateurs de modélisation, en plus de ceux prédéfinis par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="list-of-modeling-flags"></a>Liste des indicateurs de modélisation  
 La liste suivante décrit les indicateurs de modélisation pris en charge dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Pour plus d'informations sur les indicateurs de modélisation pris en charge par des algorithmes spécifiques, consultez la rubrique de référence technique relative à l'algorithme qui a été utilisé pour créer le modèle.  
  
 `NOT NULL`  
 Indique que les valeurs de la colonne d'attribut ne doivent jamais contenir de valeur NULL. Une erreur est générée si [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] rencontre une valeur NULL pour la colonne d’attribut au cours du processus d’apprentissage du modèle.  
  
 **MODEL_EXISTENCE_ONLY**  
 Indique que la colonne sera considérée comme ayant deux états : `Missing` et `Existing`. Si la valeur est `NULL`, il est considéré comme manquant. L'indicateur MODEL_EXISTENCE_ONLY est appliqué à l'attribut prédictible et est pris en charge par la plupart des algorithmes.  
  
 En effet, en définissant l’indicateur MODEL_EXISTENCE_ONLY `True` modifie la représentation des valeurs telles qu’il existe seulement deux états : `Missing` et `Existing`. Tous les États autres que missing sont combinés en un seul `Existing` valeur.  
  
 En règle générale, cet indicateur de modélisation est utilisé dans des attributs pour lesquels l'état `NULL` a une signification implicite. En d'autres termes, le fait que la colonne possède une valeur peut revêtir plus d'importance que la valeur explicite de l'état `NOT NULL`. Par exemple, une colonne [DateContractSigned] peut être `NULL` si un contrat n’a jamais été signé et `NOT NULL` si le contrat a été signé. Par conséquent, si l’objectif du modèle est de prédire si un contrat sera signé, vous pouvez utiliser l’indicateur MODEL_EXISTENCE_ONLY pour ignorer la valeur de date exacte dans le `NOT NULL` cas et de faire la distinction entre les cas où un contrat est `Missing` ou `Existing`.  
  
> [!NOTE]  
>  L'état Missing est un état spécial utilisé par l'algorithme qui diffère de la valeur de texte « Manquant » dans une colonne. Pour plus d’informations, consultez [Valeurs manquantes &#40;Analysis Services – Exploration de données&#41;](missing-values-analysis-services-data-mining.md).  
  
 `REGRESSOR`  
 Indique que la colonne est candidate pour être utilisée comme régresseur lors du traitement. Cet indicateur est défini sur une colonne de modèle d'exploration de données et ne peut être appliqué qu'à des colonnes dont le type de données numériques continues. Pour plus d’informations sur l’utilisation de cet indicateur, consultez la section [Utilisations de l’indicateur de modélisation REGRESSOR](#bkmk_UseRegressors)plus loin dans cette rubrique.  
  
## <a name="viewing-and-changing-modeling-flags"></a>Affichage et modification d'indicateurs de modélisation  
 Vous pouvez afficher les indicateurs de modélisation associés à une colonne de la structure d'exploration de données ou à une colonne du modèle en affichant les propriétés de la structure ou du modèle.  
  
 Pour déterminer les indicateurs de modélisation ont été appliqués à la structure d'exploration de données actuelle, vous pouvez créer une requête sur l'ensemble de lignes de schéma d'exploration de données qui retourne les indicateurs de modélisation uniquement pour les colonnes de la structure, en utilisant une requête semblable à la suivante :  
  
```  
SELECT COLUMN_NAME, MODELING_FLAG  
FROM $system.DMSCHEMA_MINING_STRUCTURE_COLUMNS  
WHERE STRUCTURE_NAME = '<structure name>'  
```  
  
 Vous pouvez ajouter ou modifier les indicateurs de modélisation utilisés dans un modèle en utilisant le Concepteur d'exploration de données et en modifiant les propriétés des colonnes associées. De telles modifications requièrent que la structure ou le modèle soient à nouveau traités.  
  
 Vous pouvez spécifier des indicateurs de modélisation dans une nouvelle structure d'exploration de données ou un nouveau modèle d'exploration de données à l'aide de DMX, ou à l'aide de scripts AMO ou XMLA. Cependant, vous ne pouvez pas utiliser DMX pour modifier les indicateurs de modélisation utilisés dans un modèle et une structure d'exploration de données existants. Vous devez créer un modèle d’exploration de données en utilisant la syntaxe `ALTER MINING STRUCTURE….ADD MINING MODEL`.  
  
##  <a name="bkmk_UseRegressors"></a> Utilisations de l’indicateur de modélisation REGRESSOR  
 Lorsque vous définissez l'indicateur de modélisation REGRESSOR sur une colonne, vous indiquez à l'algorithme que la colonne contient des régresseurs potentiels. Les régresseurs actuellement utilisés dans le modèle sont déterminés par l'algorithme. Un régresseur potentiel peut être ignoré s'il ne modélise pas l'attribut prédictible.  
  
 Lorsque vous générez un modèle à l'aide de l'Assistant Exploration de données, toutes les colonnes d'entrée continues sont marquées comme des régresseurs possibles. Par conséquent, même si vous ne définissez pas explicitement l'indicateur REGRESSOR sur une colonne, la colonne peut être utilisée comme régresseur dans le modèle.  
  
 Vous pouvez déterminer les régresseurs utilisés dans le modèle traité en exécutant une requête sur l'ensemble de lignes de schéma pour le modèle d'exploration de données, comme le montre l'exemple suivant :  
  
```  
SELECT COLUMN_NAME, MODELING_FLAG  
FROM $system.DMSCHEMA_MINING_COLUMNS  
WHERE MODEL_NAME = '<model name>'  
```  
  
 **Remarque** Si vous modifiez un modèle d’exploration de données et que vous remplacez le type de contenu continu d’une colonne par un type de contenu discret, vous devez modifier manuellement l’indicateur sur la colonne d’exploration de données, puis retraiter le modèle.  
  
### <a name="regressors-in-linear-regression-models"></a>Régresseurs dans les modèles de régression linéaire  
 Les modèles de régression linéaire sont basés sur l’algorithme MDT ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees). Même si vous n’utilisez pas l’algorithme MLR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression), tout modèle d’arbre de décision peut contenir un arbre ou des nœuds qui représentent une régression sur un attribut continu.  
  
 Par conséquent, dans ces modèles, il est inutile de spécifier qu'une colonne continue représente un régresseur. L’algorithme MDT ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees) partitionne le dataset en régions avec des séquences explicites même si vous ne définissez pas l’indicateur REGRESSOR sur la colonne. La différence réside dans le fait que lorsque vous définissez l'indicateur de modélisation, l'algorithme essaie de rechercher des équations de régression se présentant sous la forme suivante pour faire tenir les séquences dans les nœuds de l'arbre.  
  
 a*C1 + b\*C2 + ...  
  
 La somme des résiduels est alors calculée et, si l'écart est trop grand, l'arbre est fractionné.  
  
 Par exemple, si vous prédisez le comportement d’achat de vos clients en utilisant **Income** comme attribut et que vous définissez l’indicateur de modélisation REGRESSOR sur la colonne, l’algorithme essaie tout d’abord de faire tenir les valeurs **Income** en utilisant une formule de régression standard. Si l'écart est trop grand, la formule de régression est abandonnée et l'arbre est fractionné sur un autre attribut. L'algorithme MDT essaie ensuite de faire tenir un régresseur pour le revenu dans chacune des branches après le fractionnement.  
  
 Vous pouvez utiliser le paramètre FORCE_REGRESSOR pour faire en sorte que l'algorithme utilise un régresseur particulier. Ce paramètre peut être utilisé avec l’algorithme d’arbres de décision et l’algorithme de régression linéaire.  
  
## <a name="related-tasks"></a>Related Tasks  
 Utilisez les liens suivants pour en savoir plus sur l'utilisation des indicateurs de modélisation.  
  
|Tâche|Rubrique|  
|----------|-----------|  
|Modifier les indicateurs de modélisation à l'aide du Concepteur d'exploration de données|[Afficher ou modifier des indicateurs de modélisation &#40;exploration de données&#41;](modeling-flags-data-mining.md)|  
|Fournir une indication à l'algorithme pour recommander des régresseurs potentiels|[Spécifier une colonne à utiliser comme régresseur dans un modèle](specify-a-column-to-use-as-regressor-in-a-model.md)|  
|Voir les indicateurs de modélisation pris en charge par des algorithmes spécifiques (dans la section Indicateurs de modélisation de la rubrique de référence correspondant à chaque algorithme)|[Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining-algorithms-analysis-services-data-mining.md)|  
|En savoir plus sur les colonnes de structure d'exploration de données et les propriétés que vous pouvez définir dessus|[Colonnes de structure d’exploration de données](mining-structure-columns.md)|  
|En savoir plus sur les colonnes du modèle d'exploration de données et les indicateurs de modélisation qui peuvent être appliqués au niveau du modèle|[Colonnes d’un modèle d’exploration de données](mining-model-columns.md)|  
|Voir la syntaxe à utiliser pour travailler avec des indicateurs de modélisation dans des instructions DMX|[Indicateurs de modélisation &#40;DMX&#41;](/sql/dmx/modeling-flags-dmx)|  
|Comprendre les valeurs manquantes et la façon de les utiliser|[Les valeurs manquantes &#40;Analysis Services - Exploration de données&#41;](missing-values-analysis-services-data-mining.md)|  
|En savoir plus sur la gestion des modèles et des structures, et sur la définition de propriétés d'utilisation|[Déplacement d’objets d’exploration de données](moving-data-mining-objects.md)|  
  
  
