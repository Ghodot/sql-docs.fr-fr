---
title: SetSecureConnectionLevel, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.suite: pro-bi
ms.topic: conceptual
apiname:
- SetSecureConnectionLevel (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SetSecureConnectionLevel method
ms.assetid: 0fac7d5e-2670-4657-9439-331e7d93babb
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 4884c931082b16793f08d314c15b539925f35f36
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43267510"
---
# <a name="configurationsetting-method---setsecureconnectionlevel"></a>Méthode ConfigurationSetting - SetSecureConnectionLevel
  Définit le niveau de connexion sécurisée du serveur de rapports.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub SetSecureConnectionLevel(Level as Integer, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetSecureConnectionLevel(Int32 Level,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *Level*  
 Valeur entière représentant un niveau de connexion sécurisée.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="remarks"></a>Notes   
 Quand cette méthode est appelée, la propriété de serveur de rapports SecureConnectionLevel prend la valeur spécifiée. La valeur 0 indique que le protocole SSL est désactivé. Une valeur supérieure ou égale à 1 indique que le protocole SSL est activé.  
  
-   Quand la valeur est définie, l’élément SecureConnectionLevel dans le fichier de configuration du serveur de rapports est modifié et l’élément **URLRoot** dans le fichier de configuration est configuré de façon à utiliser « https:// » si la valeur *Level* spécifiée est supérieure ou égale à 1, ou « http:// » si la valeur *Level* spécifiée est 0.  
  
 Dans [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], SecureConnectionLevel est un commutateur d’activation ou de désactivation. La valeur par défaut est 0. Pour toute valeur supérieure ou égale à 1 passée par le biais de l’API de la méthode SetSecureConnectionLevel, le protocole SSL est considéré comme activé et la propriété de configuration SecureConnectionLevel est définie en conséquence dans le fichier rsreportserver.config. Les valeurs 2 et 3 sont toujours autorisées pour des raisons de compatibilité descendante.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a> Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
