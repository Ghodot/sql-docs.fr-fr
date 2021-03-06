---
title: Découverte des composants de flux de données par programmation | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- PipelineComponentInfos collection
- data flow task [Integration Services], components
- discovering data flow components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: ff92a96a-8af6-4532-82cc-c0bbff92401b
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: df04c8b47d4f803281e07a5f106b2756c2cc0fce
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37285665"
---
# <a name="discovering-data-flow-components-programmatically"></a>Découverte des composants de flux de données par programme
  Une fois que vous avez ajouté une tâche de flux de données à un package, l'étape suivante consiste peut-être à déterminer de quels composants de flux de données vous disposez. Vous pouvez découvrir par programme les sources, transformations et destinations de flux de données installées et disponibles sur l'ordinateur local. Pour plus d’informations sur l’ajout d’une tâche de flux de données au package, consultez [Ajout de la tâche flux de données par programmation](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md).  
  
## <a name="discovering-components"></a>Découverte des composants  
 La classe <xref:Microsoft.SqlServer.Dts.Runtime.Application> fournit la collection <xref:Microsoft.SqlServer.Dts.Runtime.Application.PipelineComponentInfos%2A>, qui contient un objet <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> pour chaque composant installé correctement sur l'ordinateur local. Chaque objet <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> contient des informations sur un composant, telles que son nom, sa description et son nom de création. Vous pouvez utiliser la valeur retournée dans la propriété <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo.CreationName%2A> pour définir la propriété <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> de l'objet <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> lorsque vous ajoutez un composant à un package.  
  
## <a name="next-step"></a>Étape suivante  
 Après avoir découvert les composants disponibles, l’étape suivante consiste à ajouter et configurer les composants, ce qui est décrit dans la nouvelle rubrique, [Ajout de composants de flux de données par programmation](../building-packages-programmatically/adding-data-flow-components-programmatically.md).  
  
## <a name="sample"></a>Exemple  
 L'exemple de code suivant indique comment énumérer la collection <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfos> de l'objet <xref:Microsoft.SqlServer.Dts.Runtime.Application> pour découvrir par programme les composants de flux de données disponibles sur l'ordinateur local. Cet exemple requiert une référence à l’assembly Microsoft.SqlServer.ManagedDTS.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Application application = new Application();  
      PipelineComponentInfos componentInfos = application.PipelineComponentInfos;  
  
      foreach (PipelineComponentInfo componentInfo in componentInfos)  
      {  
        Console.WriteLine("Name: " + componentInfo.Name + "\n" +  
          " CreationName: " + componentInfo.CreationName + "\n");  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim application As Application = New Application()  
  
    Dim componentInfos As PipelineComponentInfos = application.PipelineComponentInfos  
  
    For Each componentInfo As PipelineComponentInfo In componentInfos  
      Console.WriteLine("Name: " & componentInfo.Name & vbCrLf & _  
        " CreationName: " & componentInfo.CreationName & vbCrLf)  
    Next  
  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
![Icône Integration Services (petite)](../media/dts-16.gif "icône Integration Services (petite)")**rester jusqu'à la Date avec Integration Services  **<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout de composants de flux de données par programmation](../building-packages-programmatically/adding-data-flow-components-programmatically.md)  
  
  
