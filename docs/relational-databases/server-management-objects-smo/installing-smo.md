---
title: Installation de SMO | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.prod_service: database-engine
ms.component: smo
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- installing SMO
- SMO [SQL Server], installing
- SQL Server Management Objects, installing
ms.assetid: 140e9971-4940-4866-89b9-5cec938e2a16
caps.latest.revision: 46
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1a684d9a7ca41745c2e6ceb51d585e5420ab6740
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43098436"
---
#<a name="installing-smo"></a>Installation de SMO

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

Cette page fournit des informations sur l’installation de SMO pour une utilisation par les applications et la configuration système requise pour utiliser SMO.

## <a name="smo-nuget-package"></a>Package NuGet SMO

À partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2017 SMO est distribuée en tant que le [Microsoft.SqlServer.SqlManagementObjects](https://www.nuget.org/packages/Microsoft.SqlServer.SqlManagementObjects) package NuGet permettant aux utilisateurs de développer des applications avec SMO.

Il s’agit d’un remplacement pour SharedManagementObjects.msi, ce qui a été précédemment publiée en tant que partie du Feature Pack SQL pour chaque version de SQL Server. Les applications qui utilisent SMO doivent être mises à jour pour utiliser le package NuGet au lieu de cela et seront chargées de s’assurer que les fichiers binaires sont installés avec l’application en cours de développement.

>>[!Important]
>>Comme indiqué sur la [fichiers et numéros de Version](files-and-version-numbers.md) page, vous ne devez pas installer les assemblys SMO dans le GAC. Cela peut entraîner des problèmes avec d’autres applications utilisent également ces versions de SMO (telles que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio).

##<a name="installing-the-package"></a>Installation du Package

Consultez [NuGet Quick Start - utiliser un Package](https://docs.microsoft.com/nuget/quickstart/use-a-package) pour obtenir des instructions et des exemples d’installation et à l’aide d’un package NuGet. 
  
## <a name="system-requirements"></a>Configuration système requise
  
 SMO nécessite [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.0 à exécuter, les applications qui l’utilisent doivent donc vous assurer que les ordinateurs clients cette version ou une version ultérieure installé.
  
