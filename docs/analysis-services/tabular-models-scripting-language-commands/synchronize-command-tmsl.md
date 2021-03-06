---
title: Synchroniser la commande (TMSL) | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4265e6fa1e2214fae53cacdb084e152005eb3647
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38033272"
---
# <a name="synchronize-command-tmsl"></a>Synchroniser la commande (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

  Synchronise une base de données Analysis Services avec une autre base de données existante.  
  
## <a name="request"></a>Demande  
 Commande de synchronisation les propriétés acceptées par le code JSON sont les suivantes.  
  
```  
{   
   "synchronize":{   
      "database":"AdventureWorksDW_Production",  
      "source":"Provider=MSOLAP.7;Data Source=localhost;Integrated Security=SSPI;Initial Catalog=AdventureWorksDW_Dev",  
      "synchronizeSecurity":"copyAll",  
      "applyCompression":true  
   }  
}  
```  
  
 Commande de synchronisation les propriétés acceptées par le code JSON sont les suivantes.  
  
||||  
|-|-|-|  
|**Propriété**|**Default**|**Description**|  
|base de données||Le nom de l’objet de base de données à synchroniser.|  
|source||La chaîne de connexion à utiliser pour se connecter au serveur source.|  
|synchronizeSecurity|skipMembership|Valeur d’énumération qui spécifie comment restaurer des définitions de sécurité, notamment les rôles et autorisations. Les valeurs valides inclut skipMembership, copyAll, ignoreSecurity.|  
|applyCompression|True|Valeur booléenne qui, si true, indique que la compression sera appliquée pendant l’opération de synchronisation ; Sinon, false.|  
  
## <a name="response"></a>Réponse  
 Retourne un résultat vide quand la commande aboutit. Sinon, une exception XMLA est retournée.  
  
## <a name="usage-endpoints"></a>Utilisation (points de terminaison)  
 Cet élément de commande est utilisé dans une instruction de la [méthode Execute &#40;XMLA&#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) appel via un point de terminaison XMLA, exposée comme suit :  
  
-   Dans une fenêtre XMLA dans SQL Server Management Studio (SSMS)  
  
-   En tant que fichier d’entrée dans le **invoke-ascmd,** applet de commande PowerShell  
  
-   En tant qu’entrée pour une tâche SSIS ou d’un travail SQL Server Agent  
  
 Vous pouvez générer un script prêtes à l’emploi pour cette commande à partir de SSMS en cliquant sur le bouton de Script dans la boîte de dialogue Synchroniser la base de données.  
  
 Le [ \[MS-SSAS-T\]: QL Server tabulaires Analysis Services (SQL Server technique Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) document inclut section 3.1.5.2.2 qui décrit la structure des commandes de métadonnées tabulaires JSON et des objets. Actuellement, ce document traite des commandes et des fonctionnalités non encore implémentées dans un script TMSL. Reportez-vous à la rubrique [Tabular Model Scripting Language &#40;TMSL&#41; référence](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) pour des explications sur ce qui est pris en charge  
  
## <a name="see-also"></a>Voir aussi  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Informations de référence sur TMSL &#40;Tabular Model Scripting Language&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
