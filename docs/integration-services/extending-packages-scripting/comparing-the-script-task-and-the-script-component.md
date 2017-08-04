---
title: "Comparaison de la tâche de Script et le composant de Script | Documents Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], comparing to Script component
- Script component [Integration Services], comparing to Script task
ms.assetid: 4b73753a-4239-491b-b7a6-abc63ba83d2d
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0413b4b88a1f0326dad1ba261aea647cefd43302
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="comparing-the-script-task-and-the-script-component"></a>Comparaison de la tâche de script et du composant Script
  La tâche de Script, disponible dans la fenêtre de flux de contrôle de la [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] concepteur et le composant Script, disponible dans la fenêtre de flux de données, ont des objectifs très différents dans un [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package. La tâche est un outil de flux de contrôle à usage général, alors que le composant sert de source, de transformation ou de destination dans le flux de données. En dépit de leurs rôles différents, la tâche de script et le composant Script présentent toutefois des similarités dans les outils de codage qu'ils utilisent et les objets du package qu'ils mettent à la disposition des développeurs. Comprendre ces ressemblances et ces différences peut vous aider à utiliser la tâche et le composant de manière plus efficace.  
  
## <a name="similarities-between-the-script-task-and-the-script-component"></a>Similarités entre la tâche de script et le composant Script  
 La tâche de script et le composant Script ont en commun les fonctionnalités suivantes.  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Deux modes au moment du design|Dans la tâche et le composant, vous commencez par spécifier des propriétés dans l'éditeur, puis vous basculez vers l'environnement de développement pour écrire du code.|  
|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA)|La tâche et le composant utilisent le même environnement de développement intégré VSTA et prennent en charge du code écrit dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.|  
|Scripts précompilés|À partir de [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)], tous les scripts sont précompilés. Les versions antérieures permettaient de spécifier si les scripts étaient précompilés.<br /><br /> Le script est précompilé en code binaire, ce qui accélère l'exécution, au détriment d'une augmentation de la taille des packages.|  
|Le débogage|La tâche et le composant prennent en charge les points d'arrêt et l'exécution pas à pas du code pendant le débogage dans l'environnement de conception. Pour plus d’informations, consultez [codage et débogage de la tâche de Script](../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md) et [de codage et débogage du composant Script](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).|  
  
## <a name="differences-between-the-script-task-and-the-script-component"></a>Différences entre la tâche de script et le composant Script  
 La tâche de script et le composant Script présentent les différences importantes suivantes.  
  
|Fonctionnalité|Tâche de script|Composant Script|  
|-------------|-----------------|----------------------|  
|Flux de contrôle / Flux de données|La tâche de script est configurée sous l'onglet Flux de contrôle du concepteur et s'exécute à l'extérieur du flux de données du package.|Le composant Script est configuré dans la page Flux de données du concepteur et représente une source, une transformation ou une destination dans la tâche de flux de données.|  
|Fonction|Une tâche de script peut exécuter quasiment toutes les tâches à caractère général.|Vous devez spécifier si vous souhaitez créer une source, une transformation ou une destination à l'aide du composant Script.|  
|Exécution|Une tâche de script exécute du code personnalisé à un point donné du flux de travail du package. Elle ne s'exécute qu'une seule fois, à moins d'être placée dans un conteneur de boucles ou un gestionnaire d'événements.|Un composant Script s'exécute également une seule fois, mais il exécute généralement sa routine de traitement principale une fois pour chaque ligne de données dans le flux de données.|  
|Éditeur|Le **éditeur de tâche de Script** comporte trois pages : **général**, **Script**, et **Expressions**. Uniquement les **ReadOnlyVariables** et **ReadWriteVariables**, et **ScriptLanguage** propriétés affectent directement le code que vous pouvez écrire.|Le **éditeur de Transformation de Script** a quatre pages : **colonnes d’entrée**, **entrées et sorties**, **Script**, et **gestionnaires de connexions**. Les métadonnées et les propriétés que vous configurez dans chacune de ces pages déterminent les membres des classes de base générées automatiquement et utilisés pour le codage.|  
|Interaction avec le package|Dans le code écrit pour une tâche de Script, vous utilisez la **Dts** propriété pour accéder aux autres fonctionnalités du package. Le **Dts** propriété est un membre de la **ScriptMain** classe.|Dans le code du composant Script, des propriétés d'accesseur typées vous permettent d'accéder à certaines fonctionnalités de package, telles que les variables et les gestionnaires de connexions.<br /><br /> Le **PreExecute** méthode peut accéder uniquement les variables en lecture seule. Le **PostExecute** méthode peut accéder en lecture seule et en lecture/écriture de variables.<br /><br /> Pour plus d’informations sur ces méthodes, consultez [de codage et débogage du composant Script](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).|  
|Utilisation de variables|La tâche de Script utilise le <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> propriété de la **Dts** objet pour accéder aux variables qui sont disponibles par le biais de la tâche <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadOnlyVariables%2A> et <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadWriteVariables%2A> propriétés. Par exemple :<br /><br /> [Visual Basic]<br /><br /> `Dim myVar as String` <br /> `myVar = Dts.Variables(“MyStringVariable”).Value.ToString`<br /><br /> [C#]<br /><br /> `string myVar;` <br /> `myVar = Dts.Variables["MyStringVariable"].Value.ToString();`|Le composant Script utilise des propriétés d'accesseur typées, de la classe de base générée automatiquement, créées à partir des propriétés <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReadOnlyVariables%2A> et <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReadWriteVariables%2A> du composant. Par exemple :<br /><br /> [Visual Basic]<br /><br /> `Dim myVar as String` <br /> `myVar = Me.Variables.MyStringVariable`<br /><br /> [C#]<br /><br /> `string myVar;` <br /> `myVar = this.Variables.MyStringVariable;`|  
|Utilisation de connexions|La tâche de Script utilise le <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> propriété de la **Dts** objet pour les gestionnaires de connexions d’accès définis dans le package. Par exemple :<br /><br /> [Visual Basic]<br /><br /> `Dim myFlatFileConnection As String` <br /> `myFlatFileConnection = _     DirectCast(Dts.Connections("Test Flat File Connection").AcquireConnection(Dts.Transaction), _     String)`<br /><br /> [C#]<br /><br /> `string myFlatFileConnection;` <br /> `myFlatFileConnection = (Dts.Connections["Test Flat File Connection"].AcquireConnection(Dts.Transaction) as String);`|Le composant Script utilise des propriétés d'accesseur typées, de la classe de base générée automatiquement, créées à partir de la liste de gestionnaires de connexions entrée par l'utilisateur dans la page Gestionnaires de connexions de l'éditeur. Par exemple :<br /><br /> [Visual Basic]<br /><br /> `Dim connMgr As IDTSConnectionManager100` <br /> `connMgr = Me.Connections.MyADONETConnection`<br /><br /> [C#]<br /><br /> `IDTSConnectionManager100 connMgr;` <br /> `connMgr = this.Connections.MyADONETConnection;`|  
|Déclenchement d'événements|La tâche de Script utilise le <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> propriété de la **Dts** objet pour déclencher des événements. Par exemple :<br /><br /> [Visual Basic]<br /><br /> `Dts.Events.FireError(0, "Event Snippet", _     ex.Message & ControlChars.CrLf & ex.StackTrace, _     "", 0)`<br /><br /> [C#]<br /><br /> `Dts.Events.FireError(0, "Event Snippet", ex.Message + "\r" + ex.StackTrace, "", 0);`|Le composant Script déclenche des erreurs, des avertissements et des messages d'information à l'aide des méthodes de l'interface <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> retournée par la propriété <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A>. Par exemple :<br /><br /> [Visual Basic]<br /><br /> `Dim myMetadata as IDTSComponentMetaData100 myMetaData = Me.ComponentMetaData myMetaData.FireError(...)`|  
|Journalisation|La tâche de Script utilise le <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> méthode de la **Dts** objet pour enregistrer des informations à activé les modules fournisseurs d’informations. Par exemple :<br /><br /> [Visual Basic]<br /><br /> `Dim bt(0) As Byte Dts.Log("Test Log Event", _     0, _     bt)`<br /><br /> [C#]<br /><br /> `byte[] bt = new byte[0];` <br /> `Dts.Log("Test Log Event", 0, bt);`|Le composant Script utilise la méthode <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> de la classe de base générée automatiquement pour enregistrer des informations dans des modules fournisseurs d'informations actifs. Par exemple :<br /><br /> [Visual Basic]<br /><br /> `Dim bt(0) As Byte`<br /><br /> `Me.Log("Test Log Event", _`<br /><br /> `0, _`<br /><br /> `bt)`<br /><br /> [C#]<br /><br /> `byte[] bt = new byte[0]; this.Log("Test Log Event", 0, bt);`|  
|Retour de résultats|La tâche de Script utilise à la fois le <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> propriété et le paramètre facultatif <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> propriété de la **Dts** objet notifier l’exécution de ses résultats.|Le composant Script s'exécute dans le cadre de la tâche de flux de données et ne communique pas de résultats à l'aide de l'un ou l'autre de ces propriétés.|  
  
## <a name="see-also"></a>Voir aussi  
 [Extension du Package avec la tâche de Script](../../integration-services/extending-packages-scripting/task/extending-the-package-with-the-script-task.md)   
 [Étendre le flux de données avec le composant Script](../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)   
  
  