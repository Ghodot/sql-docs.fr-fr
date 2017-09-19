---
title: "Sécurisation des chaînes de connexion | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69ce8557-5260-4ea4-81b8-d0c5481f0868
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7a69727d252d2e8d51d462a691f65379432096eb
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="securing-connection-strings"></a>Sécurisation de chaînes de connexion
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  La protection de l'accès à votre source de données est l'un des principaux objectifs de la sécurisation d'une application. Pour limiter l'accès à votre source de données, vous devez veiller à sécuriser les informations de connexion, telles que l'ID utilisateur, le mot de passe et le nom de source de données. Le stockage d'un ID utilisateur et d'un mot de passe en texte libre, par exemple dans le code source, constitue un réel problème de sécurité. Même si vous fournissez une version compilée du code contenant des informations d'ID utilisateur et de mot de passe dans une source externe, vous courez le risque que le code compilé soit décompilé afin d'obtenir l'ID utilisateur et le mot de passe. En conséquence, il est impératif que le code ne contienne pas d'informations critiques telles que l'ID utilisateur et le mot de passe.  
  
 Il est vivement déconseillé de stocker le mot de passe avec l'URL de connexion dans le code source de l'application. Au lieu de cela, songez à stocker le mot de passe dans un autre fichier auquel l'accès est restreint. L'accès à ce fichier peut être octroyé au contexte dans lequel l'application s'exécute.  
  
 Une autre approche consiste à stocker le mot de passe crypté dans un fichier. Veillez à utiliser une API de chiffrement ne nécessitant pas l'enregistrement de la clé à un emplacement quelconque et qui ne soit pas dérivée du mot de passe utilisateur. Par exemple, vous pouvez utiliser des paires de clés publiques/privées basées sur un certificat ou une approche où les deux parties utilisent un protocole d'accord de clé (algorithme Diffie-Hellman) pour générer des clés secrètes identiques pour le chiffrement sans devoir les transmettre.  
  
 Si vous utilisez des informations de chaîne de connexion d'une source externe, telle qu'un utilisateur entrant un ID et un mot de passe utilisateur, vous devez valider toute entrée provenant de la source afin de vous assurer qu'elle présente le format approprié et ne contient pas d'autres paramètres susceptibles d'affecter la connexion.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation des Applications du pilote JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  