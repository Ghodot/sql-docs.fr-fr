---
title: "Propri&#233;t&#233;s du serveur (page Connexions) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.serverproperties.connections.f1"
ms.assetid: 33be8ac5-12dd-4b8a-99e0-68261c219dd2
caps.latest.revision: 27
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 27
---
# Propri&#233;t&#233;s du serveur (page Connexions)
  Utilisez cette page pour consulter ou modifier vos options de connexion.  
  
## Connexions  
 **Nombre maximal de connexions simultanées (0 = illimité)**  
 Si la valeur spécifiée est différente de zéro, cette option limite le nombre de connexions autorisées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!CAUTION]  
>  Une petite valeur, comme 1 ou 2, peut empêcher les administrateurs de se connecter pour administrer le serveur ; toutefois, la connexion administrateur dédiée pourra toujours se connecter.  
  
## Options de connexion par défaut  
 **Options de connexion par défaut**  
 Indique les options de connexion par défaut qui sont décrites dans le tableau suivant.  
  
|Option de configuration|Description|  
|--------------------------|-----------------|  
|**désactiver le contrôle de contrainte différée**|Contrôle les opérations de vérification des contraintes provisoires ou différées.|  
|**transactions implicites**|Contrôle si une transaction est lancée de façon implicite lors de l'exécution d'une instruction.|  
|**fermer le curseur lors de la validation**|Contrôle le comportement des curseurs après une opération de validation.|  
|**avertissements ANSI**|Contrôle la troncature et la valeur NULL dans les avertissements relatifs aux fonctions d'agrégat.|  
|**remplissage ANSI**|Contrôle le remplissage de variables à longueur fixe.|  
|**valeurs ANSI NULL**|Contrôle la gestion des valeurs `NULL` lors de l'utilisation d'opérateurs d'égalité.|  
|**abandon de l'arithmétique**|Arrête une requête lorsqu'un dépassement de capacité ou une division par zéro se produit durant son exécution.|  
|**ignorer l'arithmétique**|Renvoie NULL lorsqu'un dépassement de capacité ou une division par zéro se produit durant une requête.|  
|**identificateur entre guillemets**|Établit la distinction entre les guillemets simples et doubles lors de l'évaluation d'une expression.|  
|**aucun nombre**|Supprime le message qui indique, à la fin de chaque instruction, le nombre de lignes affectées par l'instruction.|  
|**valeur par défaut ANSI NULL activée**|Modifie le comportement de la session de façon à utiliser la compatibilité ANSI pour la possibilité de valeur NULL. Les nouvelles colonnes définies sans possibilité de valeur NULL explicite sont définies comme autorisant les valeurs NULL.|  
|**valeur par défaut ANSI NULL désactivée**|Modifie le comportement de la session afin de ne pas utiliser la possibilité de valeur NULL compatible ANSI. Les nouvelles colonnes définies sans possibilité de valeur NULL explicite sont définies de façon à ne pas accepter les valeurs NULL.|  
|**la concaténation de la valeur NULL donne NULL**|Renvoie NULL lors de la concaténation d'une valeur NULL avec une chaîne.|  
|**abandon en cas d'arrondi numérique**|Génère une erreur lors d'une perte de précision dans une expression.|  
|**abandon xact**|Annule une transaction si une instruction Transact-SQL déclenche une erreur d’exécution.|  
  
 Pour plus d'informations sur les options de connexion, recherchez l'option qui vous intéresse dans la documentation en ligne.  
  
## Connexions au serveur distant  
 **Autoriser les accès distants à ce serveur**  
 Contrôle l'exécution des procédures stockées à partir de serveurs distants exécutant des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cocher cette case revient à affecter la valeur 1 à l’option **sp_configureremote access**. La désactiver empêche l'exécution de procédures stockées à partir d'un serveur distant.  
  
 **Délai d'attente de la requête distante (en secondes, 0 = aucun délai)**  
 Spécifie le temps (en secondes) imparti à une opération distante avant l'expiration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La valeur par défaut est de 600 secondes, soit un délai d'attente de 10 minutes.  
  
 **Nécessite des transactions distribuées pour la communication de serveur à serveur**  
 Protège les actions d'une procédure de serveur à serveur par le biais d'une transaction MS DTC ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator). Pour plus d'informations, consultez [Configure the remote proc trans Server Configuration Option](../../database-engine/configure-windows/configure-the-remote-proc-trans-server-configuration-option.md).  
  
## Options d'affichage de la page Propriétés  
 **Valeurs configurées**  
 Affiche les valeurs configurées pour les options de ce volet. Si vous modifiez ces valeurs, cliquez sur **Valeurs en cours d’exécution** pour vérifier si les modifications ont été prises en compte. Si ce n'est pas le cas, l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être d'abord redémarrée.  
  
 **Valeurs en cours d’exécution**  
 Affiche les valeurs en cours d'exécution pour les options de ce volet. Ces valeurs sont en lecture seule.  
  
## Voir aussi  
 [Options &#40;Exécution de requête : SQL Server : Page Avancé&#41;](../Topic/Options%20\(Query%20Execution:%20SQL%20Server:%20Advanced%20Page\).md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  