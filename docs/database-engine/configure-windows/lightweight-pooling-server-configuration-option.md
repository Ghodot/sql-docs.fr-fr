---
title: "Regroupement l&#233;ger (option de configuration de serveur) | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "regroupement léger par défaut"
  - "diminution de la charge"
  - "regroupement léger (option)"
  - "charge système [SQL Server]"
  - "performance [SQL Server], regroupement léger"
  - "basculement de contexte [SQL Server], option de regroupement léger"
  - "basculements de contexte excessifs [SQL Server]"
  - "réduction de la charge"
  - "charge [SQL Server]"
ms.assetid: 2dc11b61-d065-4126-8e00-acf40390f9fb
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# Regroupement l&#233;ger (option de configuration de serveur)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Utilisez l’option de **regroupement léger** pour fournir un moyen de réduire la charge système associée aux basculements excessifs de contexte rencontrés parfois en environnement de multitraitement symétrique. En cas de basculements de contexte excessifs, le regroupement léger peut offrir une meilleure capacité de traitement en effectuant le basculement de contexte en ligne, ce qui permet de réduire les permutations circulaires utilisateur/noyau.  
  
 Le mode fibre est prévu pour certaines situations dans lesquelles le basculement de contexte des travailleurs UMS constitue le goulot d'étranglement critique en ce qui concerne les performances. Ces situations étant rares, le mode fibre améliore rarement les performance ou l'évolutivité sur un système ordinaire. L’amélioration du basculement de contexte dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] a également réduit la nécessité du mode fibre. Il n'est pas recommandé d'utiliser la planification du mode fibre pour les opérations courantes. Ceci pour deux raisons : cela peut réduire les performances en inhibant les avantages ordinaires du basculement de contexte et certains composants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui utilisent des objets TLS (Thread Stockage Local) ou possédés par des threads, tels que des mutexes (un type d'objet de noyau Win32), ne peuvent pas fonctionner correctement en mode fibre.  
  
 Quand l’option de **regroupement léger** a la valeur 1, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bascule en planification de mode fibre. La valeur par défaut de cette option est 0.  
  
 L’option de **regroupement léger** est une option avancée. Si vous utilisez la procédure stockée système **sp_configure** pour changer sa valeur, vous ne pouvez modifier l’option de **regroupement léger** que si la valeur 1 a été attribuée à l’option **Afficher les options avancées**. Le paramétrage prend effet une fois le serveur redémarré.  
  
> [!NOTE]  
>  Le regroupement léger n’est pas pris en charge pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 ni [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows XP. [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] fournit une prise en charge complète du regroupement léger.  
  
> [!NOTE]  
>  L'exécution du CLR (Common Language Runtime) n'est pas prise en charge sous l'option Regroupement léger. Désactivez l'une des deux options suivantes : « clr activé » ou « regroupement léger ». Les fonctionnalités qui reposent sur le CLR et qui ne fonctionnent pas correctement en mode fibre incluent le type de données de hiérarchie, la réplication et la Gestion basée sur des stratégies.  
  
## Voir aussi  
 [clr enabled (option de configuration de serveur)](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [clr enabled (option de configuration de serveur)](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)  
  
  