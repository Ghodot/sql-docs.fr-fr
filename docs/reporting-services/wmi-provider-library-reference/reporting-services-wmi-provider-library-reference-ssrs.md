---
title: Référence de bibliothèque du fournisseur WMI de Reporting Services (SSRS) | Microsoft Docs
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.suite: pro-bi
ms.topic: conceptual
apiname:
- Reporting Services WMI Provider Library
apilocation:
- reportingservices.mof
helpviewer_keywords:
- WMI provider [Reporting Services], library
ms.assetid: 17ba711d-7eff-4423-9168-63dc425a3428
author: markingmyname
ms.author: maghan
ms.openlocfilehash: ad028730c329857cc7072e6bda11966edfa9ba97
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43272719"
---
# <a name="reporting-services-wmi-provider-library-reference-ssrs"></a>Référence de bibliothèque du fournisseur WMI de Reporting Services (SSRS)
  Le fournisseur [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows Management Instrumentation (WMI) prend en charge des opérations WMI qui vous permettent d’écrire des scripts et du code pour modifier des paramètres du serveur de rapports et du Gestionnaire de rapports.  
  
 Par exemple, si vous voulez spécifier que la sécurité intégrée est utilisée quand le serveur de rapports se connecte à la base de données du serveur de rapports, créez une instance de la classe MSReportServer_ConfigurationSetting et utilisez la propriété DatabaseIntegratedSecurity de l’instance de serveur de rapports. Les classes répertoriées dans le tableau suivant représentent des composants [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Les classes sont définies dans l’espace de noms [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)] ou [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)] . Chacune des classes prend en charge des opérations en lecture et en écriture. Les opérations de création ne sont pas prises en charge.  
  
## <a name="classes"></a>Classes  
 [Classe MSReportServer_Instance](../../reporting-services/wmi-provider-library-reference/msreportserver-instance-class.md)  
 Fournit les informations de base nécessaires à un client pour établir la connexion à un serveur de rapports installé.  
  
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
 Représente les paramètres d'installation et d'exécution d'une instance de serveur de rapports. Ces paramètres sont stockés dans le fichier de configuration du serveur de rapports.  
  
 Pour plus d’informations sur les opérations WMI, consultez la documentation du SDK WMI fournie avec le SDK [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
## <a name="see-also"></a> Voir aussi  
 [Accéder au fournisseur WMI de Reporting Services](../../reporting-services/tools/access-the-reporting-services-wmi-provider.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../reporting-services/technical-reference-ssrs.md)  
  
  
