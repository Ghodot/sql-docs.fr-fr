---
title: Always Encrypted (développement client) | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: 9595eb66-284c-4474-828f-8961a05ce989
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c75bb08f0c96c386db8a9eee307e696b31c67160
ms.sourcegitcommit: 010755e6719d0cb89acb34d03c9511c608dd6c36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43239787"
---
# <a name="always-encrypted-client-development"></a>Always Encrypted (développement client)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

[Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) est une technologie de chiffrement côté client qui garantit que les données sensibles (et les clés de chiffrement liées) ne soient jamais révélées à SQL Server et à Azure SQL Database. Grâce à Always Encrypted, un pilote client peut chiffrer des données sensibles de manière transparente avant de les transmettre au moteur de base de données, et peut déchiffrer de manière transparente des données récupérées à partir de colonnes de base de données chiffrées.

Pour plus d’informations sur le développement d’applications qui utilisent des bases de données protégées par Always Encrypted, et sur les pilotes clients et les versions de pilotes prises en charge par Always Encrypted, consultez :

- [Utilisation d’Always Encrypted avec le fournisseur de données .NET Framework pour SQL Server](../../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)
- [Utilisation du chiffrement intégral avec le pilote JDBC](../../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)
- [Utilisation d’Always Encrypted avec ODBC Driver](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
- [Utilisation d’Always Encrypted avec les pilotes PHP](../../../connect/php/using-always-encrypted-php-drivers.md)

> [!NOTE]
> Actuellement, Always Encrypted n’est pas pris en charge dans [.NET CORE](https://docs.microsoft.com/dotnet/core/).

## <a name="see-also"></a> Voir aussi

[Always Encrypted (moteur de base de données)](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)

