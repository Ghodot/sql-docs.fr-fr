---
title: Après installation de Configuration (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7f4417b2-0efb-4361-a79e-fa56e43ee054
caps.latest.revision: 7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1c4f7dea428950957d267c929e36627f40e0b7d9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37151650"
---
# <a name="post-install-configuration-analysis-services"></a>Configuration consécutive à l'installation (Analysis Services)
  Après avoir installé Analysis Services, des tâches de configuration supplémentaires sont requises pour rendre le serveur complètement opérationnel et disponible en vue d'une utilisation générale. Cette section présente les autres tâches qui complètent l'installation. Selon les exigences en matière de connexion, vous devrez peut-être aussi configurer l’authentification (consultez [Se connecter à Analysis Services](connect-to-analysis-services.md)).  
  
 Plus tard, des étapes supplémentaires devront être réalisées une fois que vous aurez des bases de données prêtes à déployer. Vous devrez notamment configurer les appartenances au rôle sur la base de données afin d'accorder à l'utilisateur l'accès aux données, concevoir une stratégie de sauvegarde et de restauration des bases de données et déterminer si vous avez besoin d'une charge de travail de traitement planifiée afin que les données soient actualisées à intervalles réguliers. Pour plus d’informations sur le déploiement et l’administration des bases de données, consultez ces liens : [Bases de données de modèle multidimensionnel &#40;SSAS&#41;](../multidimensional-models/multidimensional-model-databases-ssas.md) et [Bases de données model tabulaires &#40;SSAS Tabulaire&#41;](../tabular-models/tabular-model-databases-ssas-tabular.md).  
  
## <a name="instance-configuration"></a>Configuration de l'instance  
 Analysis Services est un service réplicable, ce qui signifie que vous pouvez installer plusieurs instances du service sur un seul serveur. Chaque instance supplémentaire est installée séparément en tant qu'instance nommée, à l'aide du programme d'installation de SQL Server, et configurée indépendamment afin de prendre en charge le rôle prévu. Par exemple, un serveur de développement peut exécuter Boîte noire ou utiliser les valeurs par défaut pour le stockage des données, valeurs que vous pouvez aussi modifier sur des serveurs acceptant les charges de production. Autre exemple justifiant la configuration du système : l'installation de l'instance Analysis Services sur du matériel partagé par d'autres services. Lorsque vous hébergez plusieurs applications grandes consommatrices de données sur le même matériel, vous pouvez configurer des propriétés de serveur qui abaissent les seuils de mémoire afin d'optimiser les ressources disponibles pour toutes les applications.  
  
## <a name="post-installation-tasks"></a>Tâches consécutives à l'installation  
  
|Lien|Description de la tâche|  
|----------|----------------------|  
|[Configurer le Pare-feu Windows pour autoriser l’accès à Analysis Services](configure-the-windows-firewall-to-allow-analysis-services-access.md)|Créez une règle de trafic entrant dans le Pare-feu Windows afin que les demandes puissent être routées via le port TCP utilisé par l'instance d'Analysis Services. Cette tâche est obligatoire. Personne ne peut accéder à Analysis Services depuis un ordinateur distant tant qu'une règle entrante de pare-feu n'est pas définie.|  
|[Accorder des autorisations administrateur du serveur &#40;Analysis Services&#41;](grant-server-admin-rights-to-an-analysis-services-instance.md)|Pendant l'installation, vous deviez ajouter au moins un compte d'utilisateur au rôle Administrateur de l'instance Analysis Services. Les autorisations administratives sont obligatoires pour de nombreuses opérations courantes de serveur, telles que le traitement des données à partir de bases de données relationnelles externes. Utilisez les informations de cette rubrique pour ajouter ou modifier l'appartenance du rôle Administrateur.|  
|[Configurer les comptes de Service &#40;Analysis Services&#41;](configure-service-accounts-analysis-services.md)|Pendant l'installation, le compte de service Analysis Services a été configuré avec les autorisations appropriées pour permettre l'accès contrôlé aux fichiers exécutables du programme et aux fichiers de la base de données. En tant que tâche consécutive à l'installation, vous devez déterminer s'il faut autoriser l'utilisation du compte de service lors de l'exécution de tâches supplémentaires. Les charges de travail de traitement et de requête peuvent être exécutées sous le compte de service. Ces opérations réussissent uniquement quand le compte de service dispose des autorisations appropriées.|  
|[Inscrire une Instance Analysis Services dans un groupe de serveurs](register-an-analysis-services-instance-in-a-server-group.md)|SQL Server Management Studio (SSMS) permet de créer des groupes de serveurs pour organiser vos instances de SQL Server. Il est plus facile de gérer des déploiements évolutif constitués de plusieurs instances de serveurs au sein de groupes de serveurs. Utilisez les informations de cette rubrique pour organiser les instances d'Analysis Services en groupes dans SSMS.|  
|[Déterminer le mode serveur d’une instance Analysis Services](determine-the-server-mode-of-an-analysis-services-instance.md)|Pendant l'installation, vous deviez sélectionner un mode serveur pour déterminer le type de modèle (multidimensionnel ou tabulaire) s'exécutant sur le serveur. Si vous avez des doutes quant au mode serveur, utilisez les informations de cette rubrique pour déterminer le mode qui a été installé.|  
|[Renommer une instance Analysis Services](rename-an-analysis-services-instance.md)|Un nom descriptif peut vous aider à faire la distinction entre plusieurs instances ayant des modes serveur différents, ou entre des instances principalement utilisées par des services ou des équipes de votre organisation. Si vous souhaitez remplacer le nom de l'instance par un nom qui vous aide à mieux gérer vos installations, utilisez les informations de cette rubrique pour savoir comment procéder.|  
  
## <a name="next-steps"></a>Étapes suivantes  
 Découvrez comment se connecter à Analysis Services depuis des applications Microsoft ou des applications personnalisées à l'aide de bibliothèques clientes. Selon les besoins de votre solution, vous devrez peut-être également configurer le service pour l'authentification Kerberos. Les connexions s'établissant au-delà des limites de domaine nécessitent l'accès HTTP. Consultez [Connect to Analysis Services](connect-to-analysis-services.md) pour obtenir des instructions concernant les étapes suivantes.  
  
## <a name="see-also"></a>Voir aussi  
 [Installation de SQL Server 2014](../../../2014/database-engine/install-windows/installation-for-sql-server.md)   
 [Installer Analysis Services en mode multidimensionnel et exploration de données](../../sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md)   
 [Installer Analysis Services en Mode tabulaire](install-windows/install-analysis-services.md)   
 [Installation de PowerPivot pour SharePoint 2013](install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
  
