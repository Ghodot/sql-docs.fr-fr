---
title: ListIPAddresses, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.suite: pro-bi
ms.topic: conceptual
helpviewer_keywords:
- ListIPAddresses method
ms.assetid: 7e7cf182-fba0-4604-a474-098461e23e9d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 53d44d44760405f41f7de0393996d500a3e52865
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43265312"
---
# <a name="configurationsetting-method---listipaddresses"></a>Méthode ConfigurationSetting - ListIPAddresses
  Répertorie les adresses IP de l'ordinateur serveur de rapports.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub ListIPAddresses (ByRef IPAddress() as String, _  
    ByRef IPVersion()as String, ByRef IsDhcpEnabled () as Boolean, _   
    ByRef Length as Int32, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListIPAddresses (out string[] IPAddress,   
    out string[] IPVersion, out bool[] isDhcpEnabled, out int length,   
    out int HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *IPAddress[]*  
 [out] La liste d'adresses IP de l'ordinateur.  
  
 *IPVersion[]*  
 [out] La version des adresses IP.  
  
 *IsDhcpEnabled[]*  
 [out] Indique si les adresses IP sont compatibles DHCP.  
  
 *Longueur*  
 [out] Longueur du tableau retourné par la méthode.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. La valeur 0 indique que l'appel de la méthode a abouti ; un code d'erreur indique que l'appel n'a pas abouti.  
  
## <a name="remarks"></a>Notes   
 Les chaînes*IPVersion* sont V4, V6.  
  
 Si *IsDhcpEnabled* a la valeur **True**, l' *IPAddress* est dynamique. Elle ne doit pas être utilisée pour les liaisons SSL.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a> Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
