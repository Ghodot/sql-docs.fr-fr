---
title: Paramètres globaux (boîtes de dialogue) (MySQLToSQL) | Documents Microsoft
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 6df20fbb-e92d-475f-a94d-aaf70b06eb9b
caps.latest.revision: 3
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: acf656ac51cd8cb30c3a89bdeb197c767f7bcbc0
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34775975"
---
# <a name="global-settings-dialogs-mysqltosql"></a>Paramètres globaux (boîtes de dialogue) (MySQLToSQL)
Utilisez la page de boîtes de dialogue de la **paramètres globaux** boîte de dialogue pour spécifier l’action de l’utilisateur par défaut et les paramètres d’avertissement pour SSMA.  
  
Pour accéder aux paramètres de la boîte de dialogue sur le **outils** menu, sélectionnez **paramètres globaux**, cliquez sur **GUI** en bas du volet gauche, puis **boîtes de dialogue**.  
  
## <a name="options"></a>Options  
**Avertir avant d’écraser des objets**  
Lorsque SSMA convertit des objets SQL Server, certains objets peuvent déjà exister dans les métadonnées du projet SQL Server. Ces objets peuvent avoir déjà été convertis, ou les objets peuvent tout simplement avoir le même nom dans le schéma cible en tant qu’objets que vous vous apprêtez à convertir.  
  
Utilisez cette option pour spécifier si SSMA vous invite à entrer pour remplacer les définitions d’objet en double :  
  
-   Si vous sélectionnez **True**, SSMA affichera une boîte de dialogue d’avertissement lorsqu’il rencontre un objet dupliqué. Dans cette boîte de dialogue, vous pouvez spécifier pour remplacer des objets individuels ou tous les objets en double ou ignorer des objets individuels ou tous les objets en double.  
  
-   Si vous sélectionnez **False**, le **action de remplacement par défaut de l’objet** option apparaît, où vous spécifiez l’action par défaut.  
  
**Action par défaut de remplacement d’objet**  
Cette option apparaît si vous sélectionnez **False** pour le **avertir avant d’écraser des objets** option.  
  
Utilisez cette option pour spécifier l’objet par défaut de remplacer le comportement :  
  
-   Si vous sélectionnez **True**, SSMA remplace automatiquement dans les métadonnées de projet SQL Server, les objets qui ont le même nom et se trouvent dans le même schéma cible en tant que l’objet à convertir.  
  
-   Si vous sélectionnez **False**, SSMA ne remplace pas les métadonnées de l’objet lors de la conversion.  
  
