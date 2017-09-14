---
title: "Boîte de dialogue Propriétés du DataSet, Options (Générateur de rapports) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- "10020"
- sql13.rtp.rptdesigner.datasetproperties.options.f1
- "10130"
ms.assetid: 43e50133-45ef-47a2-b575-34dfcc28ec98
caps.latest.revision: 15
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8eea917788cfd0811750a1ffb59888fa7e2a156a
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="dataset-properties-dialog-box-options-report-builder"></a>Boîte de dialogue Propriétés du dataset, Options (Générateur de rapports)
  Sélectionnez **Options** dans la boîte de dialogue **Propriétés du jeu de données** pour modifier les options de données, telles que les options de classement et le traitement des sous-totaux en tant que données de détail, pour la requête. Pour plus d’informations sur les classements, consultez [Prise en charge d’Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md) dans la [documentation en ligne de SQL Server](http://go.microsoft.com/fwlink/?linkid=98335).  
  
 Les options de données qui font partie d'une définition de dataset partagé sur le serveur de rapports affectent tous les rapports qui utilisent le dataset partagé. Vous pouvez remplacer des options pour le dataset partagé après qu'il a été ajouté à un rapport. Ces modifications affectent uniquement le rapport dans lequel elles sont définies.  
  
 Les options de données d'un dataset incorporé affectent uniquement le rapport dans lequel elles sont définies.  
  
 Pour plus d’informations, consultez [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Options  
 **Classement**  
 Sélectionnez des paramètres régionaux qui déterminent la séquence de classement du tri des données. **Par défaut** indique que le serveur de rapports doit tenter de dériver la valeur à partir du fournisseur de données, lors de l’exécution du rapport. Si cette valeur ne peut pas être dérivée, la valeur par défaut est dérivée à partir des paramètres régionaux en vigueur sur l'ordinateur.  
  
 **Respect de la casse**  
 Sélectionnez une valeur qui détermine le respect de la casse. Cette option indique si les données respectent la casse. Vous pouvez affecter les valeurs **True** , **False**ou **Auto**à l’option **Respect de la casse**. La valeur par défaut, **Auto**, indique que le serveur de rapports doit tenter de dériver la valeur à partir du fournisseur de données, lors de l’exécution du rapport. Si le fournisseur de données ne prend pas en charge le type de respect de la casse, le rapport s’exécute comme si la valeur était **False**. Si vous connaissez la valeur et savez qu’elle est prise en charge, choisissez **True**.  
  
 **Respect des accents**  
 Sélectionnez une valeur qui détermine le respect des accents. L’option**Respect des accents** indique si les données respectent les accents ; elle peut prendre les valeurs **True**, **False**ou **Auto**. La valeur par défaut, **Auto**, indique que le serveur de rapports doit tenter de dériver la valeur à partir du fournisseur de données, lors de l’exécution du rapport. Si le fournisseur de données ne prend pas en charge le type de respect des accents, le rapport s’exécute comme si la valeur était **False**. Si vous connaissez la valeur et savez qu’elle est prise en charge, choisissez **True**.  
  
 **Respect du jeu de caractères kana**  
 Sélectionnez une valeur qui détermine le respect du jeu de caractères kana. Cette option indique si les données respectent le jeu de caractères kana ; elle peut prendre les valeurs **True**, **False**ou **Auto**. La valeur par défaut, **Auto**, indique que le serveur de rapports doit tenter de dériver la valeur à partir du fournisseur de données, lors de l’exécution du rapport. Si le fournisseur de données ne prend pas en charge le type de respect du jeu de caractères kana, le rapport s’exécute comme si la valeur était **False**. Si vous connaissez la valeur et savez qu’elle est prise en charge, choisissez **True**.  
  
 **Respect de la largeur**  
 Sélectionnez une valeur qui détermine le respect de la largeur. Cette option indique si les données respectent la largeur et peut prendre les valeurs **True**, **False**ou **Auto**. La valeur par défaut, **Auto**, indique que le serveur de rapports doit tenter de dériver la valeur à partir du fournisseur de données, lors de l’exécution du rapport. Si le fournisseur de données ne prend pas en charge le type de respect de la largeur, le rapport s’exécute comme si la valeur était **False**. Si vous connaissez la valeur et savez qu’elle est prise en charge, choisissez **True**.  
  
 **Interpréter les sous-totaux comme des lignes de détails**  
 Sélectionnez une valeur qui indique si vous souhaitez que les lignes de sous-total soient interprétées comme des lignes de détails au lieu de lignes agrégées. La valeur par défaut, **Auto**, indique que les lignes de sous-total doivent être traitées comme des lignes de détails si le rapport n’utilise pas la fonction **Aggregate**() pour accéder aux champs dans le dataset. Si vous souhaitez que les lignes de sous-total soient interprétées comme lignes agrégées, choisissez **False**. Si vous souhaitez que les lignes de sous-total soient interprétées comme des lignes de détails et que vous savez qu’elles n’utilisent pas la fonction **Aggregate**(), choisissez **True**.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide du Générateur de rapports pour les boîtes de dialogue, les volets et les Assistants](http://msdn.microsoft.com/en-us/2da24891-0b6d-4d3c-8b18-81b98752642f)   
 [Fonction d’agrégation &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/report-builder-functions-aggregate-function.md)   
 [Filtre, groupe et trier des données &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Rapport incorporé des jeux de données et des Datasets partagés &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Boîte de dialogue Propriétés du DataSet, requête &#40; Le Générateur de rapports &#41;](../../reporting-services/report-data/dataset-properties-dialog-box-query-report-builder.md)  
  
  