---
title: Meilleures pratiques pour Data Migration Assistant (SQL Server) | Microsoft Docs
description: Découvrez les meilleures pratiques pour la migration des bases de données de SQL Server avec Data Migration Assistant
ms.custom: ''
ms.date: 08/29/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Best Practices
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: rajpo
manager: craigg
ms.openlocfilehash: 949576715472f5ad5ff99425635c9ad1d29a9823
ms.sourcegitcommit: fb269accc3786715c78f8b6e2ec38783a6eb63e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43152770"
---
# <a name="best-practices-for-running-data-migration-assistant"></a>Meilleures pratiques pour l’exécution de Data Migration Assistant
Cet article fournit certaines des recommandations pour l’installation, évaluation et la migration.

## <a name="installation"></a>Installation
Évitez d’installer et d’exécuter l’Assistant Migration des données directement sur l’ordinateur hôte de SQL Server.

## <a name="assessment"></a>Évaluation
- Exécuter les évaluations sur les bases de données de production pendant les heures creuses.
- Effectuer la **les problèmes de compatibilité** et **recommandation de nouvelle fonctionnalité** évaluations séparément pour réduire la durée de l’évaluation.

## <a name="migration"></a>Migration
- Migrer un serveur pendant les heures creuses.

- Lorsque vous migrez une base de données, indiquez un emplacement de partage unique accessible par le serveur source et le serveur cible et si possible, évitez une opération de copie. Une opération de copie peut se traduire en fonction de la taille du fichier de sauvegarde. L’opération de copie augmente également le risque qu’une migration échoue en raison d’une étape supplémentaire. Lorsqu’un seul emplacement est fourni, Data Migration Assistant ignore l’opération de copie.
 
    En outre, veillez à ce que pour fournir les autorisations appropriées au dossier partagé pour éviter les échecs de migration. Les autorisations appropriées sont spécifiées dans l’outil. Si une instance de SQL Server s’exécute sous les informations d’identification de Service réseau, vous pouvez accorder les autorisations appropriées sur le dossier partagé pour le compte d’ordinateur pour l’instance de SQL Server.

- Activer chiffrer la connexion lors de la connexion aux serveurs source et cible. À l’aide de SSL chiffrement augmente la sécurité des données transmises sur les réseaux entre Data Migration Assistant et l’instance de SQL Server, ce qui est utile surtout lors de la migration des comptes de connexion SQL. Si le chiffrement SSL n’est pas utilisé et le réseau est compromis par un attaquant, les connexions SQL en cours de migration pourraient intercepter et/ou modifiés à la volée par l’attaquant.

    Toutefois, si tous les accès impliquent une configuration intranet sécurisée, le chiffrement peut s'avérer superflu. L’activation du chiffrement ralentit les performances, car la surcharge supplémentaire qui est nécessaire pour chiffrer et déchiffrer des paquets. Pour plus d’informations, reportez-vous à [chiffrement des connexions à SQL Server](https://go.microsoft.com/fwlink/?linkid=832513).
