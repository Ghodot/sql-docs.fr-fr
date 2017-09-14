---
title: "Configurer des règles d’entreprise pour envoyer des Notifications (Master Data Services) | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules [Master Data Services], configuring notifications
- e-mail [Master Data Services], configuring business rules
- notifications [Master Data Services], configuring business rules
ms.assetid: b24f7b11-ab53-4642-999c-e17b543b3558
caps.latest.revision: 10
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 29ff569439e245100befb8e0a515a128aac91f79
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="configure-business-rules-to-send-notifications-master-data-services"></a>Configurer des règles d'entreprise pour envoyer des notifications (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], configurez des règles d'entreprise pour envoyer des notifications lorsque vous souhaitez informer les utilisateurs des modifications apportées aux valeurs d'attribut.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder aux zones fonctionnelles **Administration de système** et **Autorisations d'accès** . Si vous n'avez pas d'autorisation sur la zone fonctionnelle **Autorisations d'accès** , vous ne pouvez pas afficher la liste des utilisateurs et groupes auxquels envoyer des notifications.  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Une règle d'entreprise qui utilise une action de validation doit déjà exister. Pour plus d’informations, consultez [Créer et publier une règle d’entreprise &#40;Master Data Services&#41;](../master-data-services/create-and-publish-a-business-rule-master-data-services.md).  
  
-   L’utilisateur ou le groupe qui reçoit la notification doit avoir au moins l’autorisation **Lecture seule** sur l’attribut qui n’a pas été validé. Les utilisateurs ou les groupes qui se voient refuser explicitement ou implicitement l'autorisation à l'attribut recevront le courrier électronique, mais ne seront pas en mesure d'accéder à l'attribut dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
-   Si un courrier électronique est envoyé à un groupe, seuls les membres du groupe qui ont accédé à [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] le recevront.  
  
### <a name="to-configure-business-rules-to-send-notifications"></a>Pour configurer des règles d'entreprise pour envoyer des notifications  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la barre de menus, pointez sur **Gérer** et cliquez sur **Règles d'entreprise**.  
  
3.  Sur la page **Règles d’entreprise** , sélectionnez un modèle dans la liste déroulante **Modèle** .  
  
4.  Dans la liste déroulante **Entité** , sélectionnez une entité.  
  
5.  Dans la liste déroulante **Types de membres** , sélectionnez un type de membre.  
  
6.  Dans la grille, sélectionnez la ligne de la règle d’entreprise à modifier, puis cliquez sur **Modifier**.  
  
7.  Cochez la case **Envoyer des notifications** puis, dans la liste déroulante, sélectionnez un utilisateur ou un groupe auxquels envoyer la notification par e-mail.  
  
8.  Cliquez sur **Enregistrer**.  
  
9. Cliquez sur **Tout publier**.  
  
10. Dans la boîte de dialogue de confirmation, cliquez sur **OK**. La valeur de la colonne **État de la règle d’entreprise** est redéfinie sur **Active** , et la colonne **Notification** affiche l’utilisateur ou le groupe auxquels envoyer la notification.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   Appliquez des règles d'entreprise aux données en suivant l'une de ces procédures :  
  
    -   [Valider des membres spécifiques par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [Valider une version par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   Configurez le protocole de messagerie comme suit :  
  
    -   [Configurer des notifications par e-mail &#40;Master Data Services&#41;](../master-data-services/configure-email-notifications-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Notifications &#40;Master Data Services&#41;](../master-data-services/notifications-master-data-services.md)   
 [Configurer des notifications par courrier électronique &#40;Master Data Services&#41;](../master-data-services/configure-email-notifications-master-data-services.md)  
  
  