---
title: Exécution de commandes contenant des paramètres table | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, executing commands containing
ms.assetid: 7ecba6f6-fe7a-462a-9aa3-d5115b6d4529
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 20b7c44bb8e1bb27978170a8ccced45a9f871169
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37431588"
---
# <a name="executing-commands-containing-table-valued-parameters"></a>Exécution de commandes contenant des paramètres table
  L'exécution d'une commande qui contient des paramètres table requiert deux phases :  
  
1.  Spécifier les types de paramètres.  
  
2.  Lier les données des paramètres.  
  
## <a name="table-valued-parameter-specification"></a>Spécification des paramètres table  
 Le consommateur peut spécifier le type du paramètre table. Ces informations incluent le nom du type du paramètre table. Elles incluent aussi le nom du schéma et indiquent si le type de table défini par l'utilisateur pour le paramètre table ne figure pas dans le schéma par défaut actuel de la connexion. En fonction de la prise en charge du serveur, le consommateur peut également spécifier des informations de métadonnées facultatives, telles que la classification des colonnes, et mentionner que toutes les lignes de colonnes particulières ont des valeurs par défaut.  
  
 Pour spécifier un paramètre table, le consommateur appelle ISSCommandWithParamter::SetParameterInfo et appelle éventuellement ISSCommandWithParameters::SetParameterProperties. Pour un paramètre table, le *pwszDataSourceType* champ dans la structure DBPARAMBINDINFO a la valeur DBTYPE_TABLE. Le *ulParamSize* champ est défini sur ~ 0 pour indiquer que la longueur est inconnue. Propriétés particulières des paramètres table, telles que le nom de schéma, un nom de type, ordre des colonnes et les colonnes par défaut, peuvent être définies via ISSCommandWithParameters::SetParameterProperties.  
  
## <a name="table-valued-parameter-binding"></a>Liaison de paramètre table  
 Un paramètre table peut être n'importe quel objet d'ensemble de lignes. Le fournisseur effectue la lecture à partir de cet objet tout en envoyant les paramètres table au serveur pendant l'exécution.  
  
 Pour lier le paramètre table, le consommateur appelle IAccessor::CreateAccessor. Le *wType* champ de la structure DBBINDING pour le paramètre table est défini sur DBTYPE_TABLE. Le *pObject* membre de la structure DBBINDING n’est pas NULL et le *pObject*de *iid* membre a la valeur IID_IRowset ou tout autre objet d’ensemble de lignes de paramètre table interfaces. Les champs restants de la structure DBBINDING doivent être définis de la même façon qu'ils le sont pour les BLOB transmis en continu.  
  
 Dans les liaisons du paramètre table et de l'objet d'ensemble de lignes associé à un paramètre table, les restrictions suivantes s'appliquent :  
  
-   Les seules valeurs d'état autorisées pour les données de colonnes d'ensembles de lignes de paramètres table sont DBSTATUS_S_ISNULL et DBSTATUS_S_OK. DBSTATUS_S_DEFAULT se traduit par un échec et la valeur d'état liée est DBSTATUS_E_BADSTATUS.  
  
-   Un paramètre table peut être marqué avec l'état DBSTATUS_S_DEFAULT. Les seules valeurs valides sont DBSTATUS_S_DEFAULT et DBSTATUS_S_OK. Quand l'état est défini sur DBSTATUS_S_DEFAULT, la valeur du paramètre table correspond à une table vide.  
  
-   Les colonnes en lecture seule des paramètres table (colonnes d'identité ou colonnes calculées) doivent être marquées comme valeur par défaut à l'aide de la propriété SSPROP_PARAM_TABLE_DEFAULT_COLUMNS. Les colonnes qui ont une valeur par défaut doivent aussi être marquées comme valeur par défaut via la propriété SSPROP_PARAM_TABLE_DEFAULT_COLUMNS pour autoriser l'utilisation de la valeur par défaut pour les valeurs de données de la colonne d'un paramètre table particulier. Le fournisseur ignore les valeurs de données liées pour les colonnes marquées par défaut.  
  
-   Les données sont envoyées au serveur pour les colonnes avec DBPROP_COL_AUTOINCREMENT ou SSPROP_COL_COMPUTED, à moins que SSPROP_PARAM_TABLE_DEFAULT ne soit également défini.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres table &#40;OLE DB&#41;](table-valued-parameters-ole-db.md)   
 [Utiliser des paramètres table &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
