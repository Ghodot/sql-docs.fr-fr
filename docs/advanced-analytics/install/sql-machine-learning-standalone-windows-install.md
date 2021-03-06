---
title: Installer R Server ou Machine Learning Server (autonome) à l’aide du programme d’installation de SQL Server | Microsoft Docs
description: Configurer un serveur d’apprentissage autonome non-instance-prenant en charge pour le développement R et Python à l’aide de revoscalepy, RevoScaleR, MicrosoftML et autres packages.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/28/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 7cf5cf2d78900c5bbd7607666afecc64aa98267f
ms.sourcegitcommit: e4e9f02b5c14f3bb66e19dec98f38c012275b92c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43118547"
---
# <a name="install-machine-learning-server-standalone-or-r-server-standalone-using-sql-server-setup"></a>Installer Machine Learning Server (autonome) ou R Server (autonome) à l’aide du programme d’installation de SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Le programme d’installation de SQL Server inclut un **fonctionnalité partagée** option pour installer une instance prenant, autonome machine learning serveur qui s’exécute en dehors de SQL Server. Dans SQL Server 2016, cette fonctionnalité est appelée **R Server (autonome)**. Dans SQL Server 2017, elle est appelée **Machine Learning Server (autonome)** et inclut R et Python. 

Un serveur autonome, telle qu’installée par le programme d’installation de SQL Server est fonctionnellement équivalent pour les versions non SQL personnalisée de [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server), prenant en charge les mêmes cas d’usage et scénarios, y compris l’exécution à distance, Opérationnalisation et les services web et la collection complète des fonctions RevoScaleR et revoscalepy.

Comme un serveur indépendant découplé à partir de SQL Server, l’environnement R et Python est configuré, sécurisées et accessibles en utilisant le système d’exploitation sous-jacent et les outils fournis dans le serveur autonome, pas de SQL Server.

En outre à SQL Server, un serveur autonome est utile si vous avez besoin pour développer des hautes performances machine learning solutions qui permettent à distance des contextes de calcul, de commutation de manière interchangeable entre le serveur local et une Machine Learning Server à distance sur un système Spark cluster ou sur un autre serveur SQL Server de l’instance.
  

## <a name="bkmk_prereqs"> </a> Liste de vérification de préinstallation

Si vous avez installé une version antérieure, telles que SQL Server 2016 R Server (autonome) ou Microsoft R Server, désinstallez l’installation existante avant de continuer.

En règle générale, nous recommandons que vous traiter autonome installations de serveur et base de données du moteur dépendant des instances en tant que mutuellement exclusives afin d’éviter les conflits de ressources, mais si vous avez suffisamment de ressources, il n’existe aucune interdiction par rapport à l’installation de tous les deux sur le même ordinateur physique.

Vous ne pouvez avoir qu’un serveur autonome sur l’ordinateur : SQL Server 2017 Machine Learning Server ou SQL Server 2016 R Server (autonome). Vous devez désinstaller manuellement une version avant d’installer une version différente.

::: moniker range="=sql-server-2016"
 ###  <a name="bkmk_ga_instalpatch"></a> Installer le correctif obligatoire 

Pour SQL Server 2016 uniquement : Microsoft a identifié un problème avec la version spécifique des fichiers binaires Microsoft VC ++ 2013 Runtime qui sont installés en tant que composant requis par SQL Server. Si cette mise à jour des fichiers binaires du runtime VC n’est pas installée, SQL Server risque de rencontrer des problèmes de stabilité dans certains scénarios. Avant d’installer SQL Server, suivez les instructions données dans [Notes de publication de SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch) pour voir si votre ordinateur nécessite un correctif pour les fichiers binaires du runtime VC.  
::: moniker-end

## <a name="get-the-installation-media"></a>Obtenir le média d’installation

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
## <a name="run-setup"></a>Exécutez le programme d’installation

Pour des installations locales, vous devez exécuter le programme d'installation en tant qu'administrateur. Si vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un partage distant, vous devez utiliser un compte de domaine qui a les autorisations de lecture et d'exécution sur le partage distant.

1. Démarrer l’Assistant installation.

2. Cliquez sur le **Installation** et sélectionnez **installation de la nouvelle Machine Learning Server (autonome)**.
    
     ![Installer Machine Learning Server (autonome)](media/2017setup-installation-page-mlsvr.png "démarrer l’installation de Machine Learning Server (autonome)")

3. Une fois la vérification des règles terminée, acceptez les termes du contrat de licence de SQL Server, puis sélectionnez une nouvelle installation.

4. Sur le **sélection des fonctionnalités** page, ce qui suit options doivent déjà être sélectionnées :

    - Microsoft Machine Learning Server (autonome)

    - R et Python est sélectionnées par défaut. Vous pouvez désélectionner les deux langues, mais nous vous recommandons d’installer au moins une des langues prises en charge.

     ![Installer Machine Learning Server (autonome)](media/2017setup-features-page-mlsvr-rpy.png "démarrer l’installation de Machine Learning Server (autonome)")
    
    Toutes les autres options peuvent être ignorées. 
    
    > [!NOTE]
    > Évitez d’installer le **fonctionnalités partagées** si l’ordinateur a déjà installé pour l’analytique en base de données de SQL Server Machine Learning Services. Cela crée des bibliothèques en double.
    > 
    > En outre, tandis que les scripts R ou Python en cours d’exécution dans SQL Server sont gérés par SQL Server pour autant en conflit avec la mémoire utilisée par d’autres services de moteur de base de données, serveur autonome machine learning ne comporte aucune contrainte de ce type et peut interférer avec d’autres opérations de base de données . Enfin, l’accès à distance via une session RDP, ce qui est souvent utilisée pour l’Opérationnalisation, est généralement bloqué par les administrateurs de base de données.
    > 
    > Pour ces raisons, nous recommandons généralement que vous installez Machine Learning Server (autonome) sur un ordinateur distinct à partir de SQL Server Machine Learning Services.

5.  Acceptez les termes du contrat de licence pour télécharger et installer des distributions de langue de base. Lorsque le bouton **Accepter** n’est plus disponible, vous pouvez cliquer sur **Suivant**. 

     ![Contrat de licence Python](media/2017setup-python-license.png "contrat de licence de Python")

6.  Sur la page **Prêt pour l’installation** , vérifiez vos sélections, et cliquez sur **Installer**.

Lors de l’installation terminée, consultez [rapports personnalisés pour SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md) pour avec des erreurs ou avertissements, consultez [mise à niveau et installation FAQ - Services Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md).
::: moniker-end

::: moniker range="=sql-server-2016"
## <a name="run-setup"></a>Exécutez le programme d’installation

Pour des installations locales, vous devez exécuter le programme d'installation en tant qu'administrateur. Si vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un partage distant, vous devez utiliser un compte de domaine qui a les autorisations de lecture et d'exécution sur le partage distant.

1. Démarrer l’Assistant installation.

2. Sur le **Installation** , cliquez sur **installation nouvelle R Server (autonome)**.
    
     ![Démarrer le programme d’installation de R Server (autonome)](media/2016-setup-installation-rsvr.png "démarrer le programme d’installation de R Server (autonome)")

3. Une fois la vérification des règles terminée, acceptez les termes du contrat de licence de SQL Server, puis sélectionnez une nouvelle installation.

4.  Dans la page **Sélection de fonctionnalités** , l’option suivante doit déjà être sélectionnée :
    
    **R Server (autonome)**  
    
    ![Sélections pour R Server (autonome) de fonctionnalités](media/2016setup-rserver-features.png "fonctionnalité sélections pour R Server (autonome)")
    
    Toutes les autres options peuvent être ignorées. 
    
    > [!NOTE]
    > Évitez d’installer le **fonctionnalités partagées** si vous exécutez le programme d’installation sur un ordinateur où R Services a déjà été installé pour l’analytique en base de données de SQL Server. Cela crée des bibliothèques en double.
    > 
    > Tandis que les scripts R en cours d’exécution dans SQL Server sont gérés par SQL Server pour autant en conflit avec la mémoire utilisée par d’autres services de moteur de base de données, R Server autonome ne comporte aucune contrainte de ce type et peut interférer avec d’autres opérations de base de données.
    > 
    > Nous recommandons généralement que vous installez R Server (autonome) sur un ordinateur distinct à partir de SQL Server R Services (en base de données).

5.  Acceptez les termes du contrat de licence pour télécharger et installer des distributions de langue de base. Lorsque le bouton **Accepter** n’est plus disponible, vous pouvez cliquer sur **Suivant**. 

6.  Sur la page **Prêt pour l’installation** , vérifiez vos sélections, et cliquez sur **Installer**.

Lors de l’installation terminée, consultez [rapports personnalisés pour SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md) pour avec des erreurs ou avertissements, consultez [mise à niveau et installation FAQ - Services Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md).
::: moniker-end

### <a name="default-installation-folders"></a>Dossiers d’installation par défaut

Pour le développement R et Python, il est courant d’avoir plusieurs versions sur le même ordinateur. Installé par le programme d’installation de SQL Server, la distribution de base est installée dans un dossier associé à la version de SQL Server que vous avez utilisé pour le programme d’installation.

Le tableau suivant répertorie les chemins d’accès pour les distributions de R et Python créées par les programmes d’installation de Microsoft. Par souci d’exhaustivité, la table inclut des chemins d’accès générés par le programme d’installation de SQL Server, ainsi que le programme d’installation autonome de Microsoft Machine Learning Server.

|Version| Méthode d’installation | Dossier par défaut|
|----|----|----|
|SQL Server 2017 Machine Learning Server (autonome) |  Assistant d’installation de SQL Server 2017 |`C:\Program Files\Microsoft SQL Server\140\R_SERVER` <br/>`C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`|
|Microsoft Machine Learning Server (autonome) |  Le programme d’installation de Windows autonome |`C:\Program Files\Microsoft\ML Server\R_SERVER`<br/>`C:\Program Files\Microsoft\ML Server\PYTHON_SERVER`|
|SQL Server 2017 Machine Learning Services (en base de données) |Assistant d’installation de SQL Server 2017, avec l’option de langage R|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES`  <br/>`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES` |
|SQL Server 2016 R Server (autonome) |  Assistant d’installation de SQL Server 2016 |`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|SQL Server 2016 R Services (en base de données) |Assistant d’installation de SQL Server 2016|`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES`|

## <a name="development-tools"></a>Outils de développement

Un IDE de développement n’est pas installé dans le cadre du programme d’installation. Pour plus d’informations sur la façon de configurer un environnement de développement, consultez [configurer les outils R](../r/set-up-a-data-science-client.md) et [configurer Python tools](../python/setup-python-client-tools-sql.md).

## <a name="next-steps"></a>Étapes suivantes

Aux développeurs R peuvent démarrer avec des exemples simples et apprendre les bases du fonctionne de R avec SQL Server. Pour votre prochaine étape, consultez les liens suivants :

+ [Didacticiel : Exécuter R dans T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Didacticiel : De base de données analytique pour les développeurs R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
Les développeurs Python peuvent apprendre à utiliser Python avec SQL Server en suivant ces didacticiels :

+ [Didacticiel : Exécuter Python dans T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Didacticiel : De base de données analytique pour les développeurs Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)
::: moniker-end

Pour afficher des exemples d’apprentissage qui sont basées sur des scénarios réels, consultez [d’apprentissage didacticiels](../tutorials/machine-learning-services-tutorials.md).
