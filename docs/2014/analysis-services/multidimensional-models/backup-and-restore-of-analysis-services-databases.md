---
title: Sauvegarde et restauration des bases de données Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.ssmsimbi.Backup.f1
- sql12.asvs.ssmsimbi.Restore.f1
helpviewer_keywords:
- backing up databases [Analysis Services]
- encryption [Analysis Services]
- databases [Analysis Services], restoring
- cryptography [Analysis Services]
- databases [Analysis Services], backing up
- restoring databases [Analysis Services]
- recovery [Analysis Services]
ms.assetid: 947eebd2-3622-479e-8aa6-57c11836e4ec
caps.latest.revision: 52
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3881b600453b66723afae9369fac8b18ca0012aa
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37312629"
---
# <a name="backup-and-restore-of-analysis-services-databases"></a>Sauvegarde et restauration de bases de données Analysis Services
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] inclut la sauvegarde et la restauration afin que vous puissiez récupérer une base de données et ses objets à partir d'une date et heure spécifiques. La sauvegarde et la restauration peuvent également être utiles pour migrer des bases de données vers des serveurs mis à niveau, déplacer des bases de données entre des serveurs ou déployer une base de données sur un serveur de production. Pour la récupération des données, si vous ne possédez pas encore de plan de sauvegarde et si vos données ont de la valeur, vous devez concevoir et mettre en œuvre un plan au plus tôt.  
  
 Les commandes de restauration et sauvegarde sont effectuées sur une base de données Analysis Services déployée. Pour vos projets et solutions dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], vous devez utiliser un contrôle de code source pour garantir la récupération des versions spécifiques de vos fichiers sources, puis créer un plan de récupération de données pour le référentiel du système de contrôle de code source que vous utilisez.  
  
 Pour effectuer une sauvegarde complète incluant des données sources, vous devez sauvegarder la base de données qui contient les données de détail. Spécifiquement, si vous utilisez le mode de stockage de base de données ROLAP ou DirectQuery, les données de détail sont stockées dans une base de données relationnelle SQL Server externe, distincte de la base de données Analysis Services. Sinon, si tous les objets sont tabulaires ou multidimensionnels, la sauvegarde Analysis Services inclut les métadonnées et les données sources.  
  
 L'automatisation de la sauvegarde a comme avantage certain que l'instantané des données sera toujours à jour, comme la fréquence automatisée de sauvegarde le spécifie. Les planificateurs automatisés empêchent tout oubli des sauvegardes. La restauration d'une base de données peut également être automatisée et peut représenter une manière intéressante de répliquer les données, mais assurez-vous de sauvegarder le fichier de clé de chiffrement sur l'instance vers laquelle vous effectuez la réplication. La fonctionnalité de synchronisation est dédiée à la réplication des bases de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , mais uniquement pour les données périmées. Toutes les fonctionnalités mentionnées ici peuvent être implémentées via l'interface utilisateur, à l'aide des commandes XML/A ou s'exécuter par programmation via les objets AMO. Pour plus d'informations sur les stratégies de sauvegarde, consultez [Stratégies de sauvegardes avec SQL Server 2005 Analysis Services](http://go.microsoft.com/fwlink/?LinkId=81888).  
  
 Cette rubrique comprend les sections suivantes :  
  
-   [Préparation de la sauvegarde](#bkmk_prep)  
  
-   [Sauvegarde d'une base de données multidimensionnelle ou tabulaire](#bkmk_cube)  
  
-   [Restauration d'une base de données Analysis Services](#bkmk_restore)  
  
##  <a name="bkmk_prereq"></a> Conditions préalables  
 Vous devez disposer d'autorisations administratives pour l'instance Analysis Services ou d'autorisations Contrôle total (administrateur) pour la base de données que vous sauvegardez.  
  
 L'emplacement de restauration doit être une instance Analysis Services de la même version, ou d'une version plus récente, que l'instance à partir de laquelle la sauvegarde a été effectuée. Bien qu’il soit impossible de restaurer une base de données d’une instance [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] vers une instance d’une version antérieure d’Analysis Services, il est courant de restaurer une base de données de version antérieure, telle que SQL Server 2012, sur une instance [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] plus récente.  
  
 L'emplacement de restauration doit être du même type de serveur. Les bases de données tabulaires ne peuvent être restaurées que vers Analysis Services exécuté en mode tabulaire. Les bases de données multidimensionnelles nécessitent une instance exécutée en mode multidimensionnel.  
  
##  <a name="bkmk_prep"></a> Préparation de la sauvegarde  
 Utilisez la liste de contrôle suivante pour préparer la sauvegarde :  
  
-   Vérifiez l'emplacement où le fichier de sauvegarde sera stocké. Si vous utilisez un emplacement distant, vous devez le spécifier comme dossier UNC. Vérifiez que vous avez accès au chemin UNC.  
  
-   Vérifiez les autorisations sur le dossier pour vous assurer que le compte de service Analysis Services a des autorisations de lecture/écriture sur le dossier.  
  
-   Vérifiez que l'espace disque est suffisant sur le serveur cible.  
  
-   Recherchez des fichiers existants portant le même nom. S'il existe déjà un fichier portant le même nom, la sauvegarde échoue, sauf si vous spécifiez des options pour remplacer le fichier.  
  
##  <a name="bkmk_cube"></a> Sauvegarde d'une base de données multidimensionnelle ou tabulaire  
 Les administrateurs peuvent sauvegarder une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans un seul fichier de sauvegarde [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (.abf), quelle que soit la taille de la base de données. Pour obtenir des instructions détaillées, consultez [How to Backup an Analysis Services Database (TechMantra)](http://www.mytechmantra.com/LearnSQLServer/Backup_an_Analysis_Services_Database.html) [(Comment sauvegarder une base de données Analysis Services Database (TechMantra)] et [Automate Backup an Analysis Services Database (TechMantra)](http://www.mytechmantra.com/LearnSQLServer/Automate_Backup_of_Analysis_Services_Database.html)[Automatiser la sauvegarde d’une base de données Analysis Services (TechMantra)].  
  
> [!NOTE]  
>  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], utilisé pour le chargement et l'interrogation des modèles de données PowerPivot dans un environnement SharePoint, charge ses modèles depuis des bases de données de contenu SharePoint. Ces bases de données de contenu sont relationnelles et s'exécutent sur le moteur de base de données relationnelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Par conséquent, il n'existe aucune stratégie de sauvegarde et de restauration [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour les modèles de données PowerPivot. Si vous avez mis en place un plan de récupération d'urgence pour le contenu SharePoint, ce plan englobe les modèles de données PowerPivot stockés dans les bases de données de contenu.  
  
 **Partitions distantes**  
  
 Si la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] contient des partitions distantes, celles-ci doivent aussi être sauvegardées. Lorsque vous sauvegardez une base de données avec des partitions distantes, toutes les partitions distantes sur chaque serveur distant sont sauvegardées dans un fichier unique sur chacun des serveurs distants correspondants. Ainsi, pour créer ces sauvegardes distantes sur d'autres ordinateurs que leurs ordinateurs hôtes respectifs, vous devez copier manuellement ces fichiers dans les zones de stockage désignées.  
  
 **Contenu d'un fichier de sauvegarde**  
  
 La sauvegarde d'une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] produit un fichier de sauvegarde dont le contenu varie en fonction du mode de stockage utilisé par les objets de la base de données. Cette différence de contenu de sauvegarde résulte du fait que chaque mode de stockage stocke en fait un ensemble différent d'informations dans une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Par exemple, les partitions et les dimensions multidimensionnelles HOLAP (OLAP hybride) stockent les agrégations et les métadonnées dans la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , tandis que les partitions et les dimensions ROLAP (OLAP relationnel) stockent uniquement les métadonnées dans la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Comme le contenu réel d'une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] varie en fonction du mode de stockage de chaque partition, le contenu du fichier de sauvegarde varie également. Le tableau ci-dessous associe le contenu du fichier de sauvegarde au mode de stockage utilisé par les objets.  
  
|Mode de stockage|Contenu du fichier de sauvegarde|  
|------------------|-----------------------------|  
|Partitions et dimensions MOLAP (OLAP multidimensionnel)|Métadonnées, données sources et agrégations|  
|Partitions et dimensions HOLAP multidimensionnel|Métadonnées et agrégations|  
|Partitions et dimensions ROLAP multidimensionnel|Métadonnées|  
|Modèles tabulaires en mémoire|Métadonnées et données sources|  
|Modèles tabulaires DirectQuery|Métadonnées uniquement|  
  
> [!NOTE]  
>  La sauvegarde d'une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne sauvegarde pas les données des sources de données sous-jacentes, telles qu'une base de données relationnelle. Seul le contenu de la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est sauvegardé.  
  
 Lorsque vous sauvegardez une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , vous pouvez choisir parmi les options suivantes :  
  
-   S'il convient de compresser toutes les sauvegardes de base de données. L'option par défaut consiste à compresser les sauvegardes.  
  
-   S'il convient de chiffrer le contenu des fichiers de sauvegarde et de requérir un mot de passe avant de déchiffrer et de restaurer les fichiers. Par défaut, les données sauvegardées ne sont pas chiffrées.  
  
    > [!IMPORTANT]  
    >  Pour chaque fichier de sauvegarde, l'utilisateur qui exécute la commande de sauvegarde doit avoir l'autorisation d'écrire dans l'emplacement de sauvegarde spécifié pour chaque fichier. L’utilisateur doit aussi avoir l’un des rôles suivants : membre d’un rôle serveur pour l’instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou membre d’un rôle de base de données avec les autorisations de contrôle total (Administrateur) sur la base de données à sauvegarder.  
  
 Pour plus d’informations sur la sauvegarde d’une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , consultez [Options de sauvegarde](backup-options.md).  
  
##  <a name="bkmk_restore"></a> Restauration d'une base de données Analysis Services  
 Les administrateurs peuvent restaurer une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à partir d'un ou de plusieurs fichiers de sauvegarde.  
  
> [!NOTE]  
>  Si un fichier de sauvegarde est chiffré, vous devez fournir le mot de passe spécifié pendant la sauvegarde pour pouvoir utiliser ce fichier dans le but de restaurer une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Au cours de la restauration, vous disposez des options suivantes :  
  
-   Vous pouvez restaurer la base de données en utilisant le nom original de la base de données ou vous pouvez spécifier un nouveau nom de base de données.  
  
-   Vous pouvez remplacer une base de données existante. Si vous choisissez de remplacer la base de données, vous devez spécifier de manière expresse que vous souhaitez remplacer la base de données existante.  
  
-   Vous pouvez choisir de restaurer les informations de sécurité existantes ou d'ignorer les informations sur l'appartenance à la sécurité.  
  
-   Vous pouvez décider que la commande de restauration modifie le dossier de restauration pour chaque partition à restaurer. Les partitions locales peuvent être restaurées dans tout emplacement de dossier local pour l'instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans laquelle la base de données est restaurée. Les partitions distantes peuvent être restaurées dans un dossier quelconque, sur un serveur quelconque, autre que le serveur local ; les partitions distantes ne peuvent pas devenir locales.  
  
    > [!IMPORTANT]  
    >  Pour chaque fichier de sauvegarde, l'utilisateur qui exécute la commande de restauration doit avoir l'autorisation de lire à partir de l'emplacement de sauvegarde spécifié pour chaque fichier. Pour restaurer une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui n'est pas installée sur le serveur, l'utilisateur doit également être un membre du rôle serveur pour cette instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Pour remplacer une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , l’utilisateur doit avoir l’un des rôles suivants : membre du rôle serveur pour l’instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou membre d’un rôle de base de données avec les autorisations de contrôle total (Administrateur) sur la base de données à restaurer.  
  
    > [!NOTE]  
    >  Après la restauration d'une base de données existante, l'utilisateur qui a restauré la base de données peut perdre l'accès à la base de données restaurée. Cette perte d'accès peut se produire si, au moment de la sauvegarde, l'utilisateur n'était pas un membre du rôle de serveur ou un membre du rôle de base de données avec les autorisations de contrôle total (Administrateur).  
  
 Pour plus d’informations sur la restauration d’une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , consultez [Options de restauration](restore-options.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde, restauration et synchronisation de bases de données &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)   
 [PowerShell Analysis Services](../analysis-services-powershell.md)  
  
  
