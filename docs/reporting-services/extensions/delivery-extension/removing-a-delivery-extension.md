---
title: Suppression d’une extension de remise | Microsoft Docs
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.suite: pro-bi
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- removing delivery extensions
- deleting delivery extensions
- delivery extensions [Reporting Services], removing
ms.assetid: dcb7caf2-d19a-4bc5-afb3-2b61ad11cac5
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 24036ae33b6b6a8da46b988189a055f5b17cca46
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43274941"
---
# <a name="removing-a-delivery-extension"></a>Suppression d'une extension de remise
  Pour supprimer une extension de remise [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], supprimez simplement l’élément **Extension** de votre extension de remise du fichier de configuration. Une fois les informations de configuration supprimées, l'extension de remise n'est plus disponible pour le serveur de rapports.  
  
 Une fois que l’élément **Extension** correspondant d’une extension de remise est supprimé du fichier de configuration, il n’est plus inscrit auprès du serveur de rapports. Le serveur de rapports supprime l'entrée dans la liste d'extensions de remise et désactive tous les abonnements qui utilisent cette extension de remise. Lorsqu'une extension de remise est supprimée, les utilisateurs ne sont plus en mesure de le sélectionner comme méthode de notification.  
  
## <a name="see-also"></a> Voir aussi  
 [Implémentation d’une extension de remise](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Bibliothèque d'extensions Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
