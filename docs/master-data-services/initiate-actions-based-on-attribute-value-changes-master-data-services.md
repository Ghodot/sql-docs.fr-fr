---
title: "Initier des actions en fonction de modifications de valeurs d&#39;attribut (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "règles d’entreprise [Master Data Services], suivi des modifications d’attribut"
  - "groupes de suivi des modifications [Master Data Services], initiation d’actions"
ms.assetid: 5e4402ce-31db-4774-a2a1-552335f87693
caps.latest.revision: 8
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 8
---
# Initier des actions en fonction de modifications de valeurs d&#39;attribut (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], créez une règle d’entreprise pour initier des actions en fonction des modifications apportées aux valeurs d’attribut. Par exemple, lorsqu'une valeur d'attribut spécifique change, vous pouvez modifier une valeur, envoyer une notification, ou démarrer un flux de travail externe.  
  
## Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Vos attributs doivent se trouver dans un groupe de suivi des modifications. Pour plus d’informations, consultez [Ajouter des attributs à un groupe de suivi des modifications &#40;Master Data Services&#41;](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).  
  
### Pour créer une règle d'entreprise afin d'initier des actions en fonction des modifications apportées aux valeurs d'attribut.  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la barre de menus, pointez sur **Gérer** et cliquez sur **Règles d'entreprise**.  
  
3.  Dans la page **Maintenance des règles d’entreprise**, dans la liste **Modèle**, sélectionnez un modèle.  
  
4.  Dans la liste **Entité**, sélectionnez une entité.  
  
5.  Dans la liste **Type de membre**, sélectionnez un type de membre auquel appliquer la règle d’entreprise.  
  
6.  Dans la liste **Attribut**, sélectionnez un attribut ou conservez l’option par défaut **Tout**.  
  
7.  Cliquez sur **Ajouter une règle d’entreprise**.  
  
8.  Cliquez sur **Modifier la règle d’entreprise sélectionnée**.  
  
9. Dans le volet **Composants**, développez le nœud **Conditions**.  
  
10. Sous le nœud **Comparaison de valeur**, faites glisser **a changé** vers l’étiquette **Conditions** du volet **IF**.  
  
11. Dans le volet **Modifier la condition**, dans la zone **Groupe de suivi des modifications**, tapez le numéro du groupe de suivi des modifications que vous avez attribué comme l’un des composants requis.  
  
12. Dans le volet **Modifier la condition**, cliquez sur **Enregistrer l’élément**.  
  
13. Dans le volet **Composants**, développez le nœud **Actions**.  
  
14. Cliquez sur une action et faites-la glisser vers l’étiquette **Action** du volet **THEN**.  
  
15. Dans le volet **Attributs**, cliquez sur un attribut et faites-le glisser vers l’étiquette **Sélectionner un attribut** du volet **Modifier l’action**.  
  
16. Dans le volet ** Modifier l’action**, remplissez tous les champs obligatoires.  
  
17. Dans le volet **Modifier l’action**, cliquez sur **Enregistrer l’élément**.  
  
18. Cliquez sur **Précédent**.  
  
19. (Facultatif) Dans la page **Maintenance des règles d’entreprise**, sur la ligne qui contient votre règle d’entreprise, double-cliquez sur une cellule dans la colonne **Nom**, **Description** ou **Notification** pour mettre à jour la valeur.  
  
    > [!NOTE]  
    >  Des notifications sont envoyées uniquement pour les règles qui incluent une action de validation.  
  
20. Cliquez sur **Publier les règles d’entreprise**.  
  
21. Dans la boîte de dialogue de confirmation, cliquez sur **OK**. L’état de la règle devient **Actif**.  
  
## Étapes suivantes  
  
-   Appliquez des règles d'entreprise aux données en suivant l'une de ces procédures :  
  
    -   [Valider des membres spécifiques par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [Valider une version par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## Voir aussi  
 [Ajouter des attributs à un groupe de suivi des modifications &#40;Master Data Services&#41;](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)   
 [Règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
  