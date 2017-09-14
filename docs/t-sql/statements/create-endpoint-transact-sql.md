---
title: "CRÉER le point de terminaison (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ENDPOINT
- CREATE ENDPOINT
- ENDPOINT_TSQL
- CREATE_ENDPOINT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database mirroring [SQL Server], endpoint
- HTTP SOAP support [SQL Server]
- CREATE ENDPOINT statement
- Availability Groups [SQL Server], configuring
- endpoints [SQL Server], creating
- SOAP [SQL Server built-in support], endpoints
- SOAP [SQL Server built-in support], sqlbatch
- DATABASE_MIRRORING option
- HTTP protocol option [SQL Server]
- SOAP [SQL Server built-in support], ad hoc
- TCP protocol option [SQL Server]
- SERVICE_BROKER option
- Availability Groups [SQL Server], endpoint
ms.assetid: 6405e7ec-0b5b-4afd-9792-1bfa5a2491f6
caps.latest.revision: 135
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 072e142531102533d278ec57573079f5bd90c99e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-endpoint-transact-sql"></a>CREATE ENDPOINT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Permet de créer des points de terminaison et de définir leurs propriétés, ainsi que les méthodes à la disposition des applications clientes. Pour plus d’informations des autorisations, consultez [accorder des autorisations de point de terminaison &#40; Transact-SQL &#41; ](../../t-sql/statements/grant-endpoint-permissions-transact-sql.md).  
  
 La syntaxe de l'instruction CREATE ENDPOINT peut être logiquement subdivisée en deux parties :  
  
-   La première partie commence par AS et se termine avant la clause FOR.  
  
     Dans cette partie, vous fournissez des informations propres au protocole de transport (TCP), vous définissez un numéro de port d'écoute pour le point de terminaison et vous précisez la méthode d'authentification du point de terminaison et/ou une liste d'adresses IP (le cas échéant) que vous souhaitez empêcher d'accéder au point de terminaison.  
  
-   La seconde partie commence par la clause FOR.  
  
     Dans cette partie, vous définissez la charge utile prise en charge sur le point de terminaison. La charge utile peut être de divers types parmi ceux pris en charge : [!INCLUDE[tsql](../../includes/tsql-md.md)], Service Broker, mise en miroir de bases de données. Dans cette partie, vous préciserez également des informations propres à la langue.  
  
> **Remarque :** les Services de Web XML natifs (points de terminaison SOAP/HTTP) a été supprimée dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CREATE ENDPOINT endPointName [ AUTHORIZATION login ]  
[ STATE = { STARTED | STOPPED | DISABLED } ]  
AS { TCP } (  
   <protocol_specific_arguments>  
        )  
FOR { TSQL | SERVICE_BROKER | DATABASE_MIRRORING } (  
   <language_specific_arguments>  
        )  
  
<AS TCP_protocol_specific_arguments> ::=  
AS TCP (  
  LISTENER_PORT = listenerPort  
  [ [ , ] LISTENER_IP = ALL | ( 4-part-ip ) | ( "ip_address_v6" ) ]  
  
)  
  
<FOR SERVICE_BROKER_language_specific_arguments> ::=  
FOR SERVICE_BROKER (  
   [ AUTHENTICATION = {   
            WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ]   
      | CERTIFICATE certificate_name   
      | WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ] CERTIFICATE certificate_name   
      | CERTIFICATE certificate_name WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ]   
    } ]  
   [ [ , ] ENCRYPTION = { DISABLED | { { SUPPORTED | REQUIRED }   
       [ ALGORITHM { AES | RC4 | AES RC4 | RC4 AES } ] }   
   ]  
   [ [ , ] MESSAGE_FORWARDING = { ENABLED | DISABLED } ]  
   [ [ , ] MESSAGE_FORWARD_SIZE = forward_size ]  
)  
  

<FOR DATABASE_MIRRORING_language_specific_arguments> ::=  
FOR DATABASE_MIRRORING (  
   [ AUTHENTICATION = {   
            WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ]   
      | CERTIFICATE certificate_name   
      | WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ] CERTIFICATE certificate_name   
      | CERTIFICATE certificate_name WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ]   
   [ [ [ , ] ] ENCRYPTION = { DISABLED | { { SUPPORTED | REQUIRED }   
       [ ALGORITHM { AES | RC4 | AES RC4 | RC4 AES } ] }   
  
    ]   
   [ , ] ROLE = { WITNESS | PARTNER | ALL }  
)  
```  
  
## <a name="arguments"></a>Arguments  
 *endPointName*  
 Correspond au nom affecté au point de terminaison que vous créez. À utiliser lors de la mise à jour ou la suppression du point de terminaison.  
  
 AUTORISATION *connexion*  
 Indique une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou Windows valide qui détient l'objet de point de terminaison qui vient d'être créé. Si l'argument AUTHORIZATION n'est pas spécifié, l'appelant devient, par défaut, le propriétaire de l'objet qui vient d'être créé.  
  
 Pour affecter la propriété en spécifiant d’autorisation, l’appelant doit avoir l’autorisation IMPERSONATE sur le *connexion*.  
  
 Pour réaffecter la propriété, consultez [ALTER ENDPOINT &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-endpoint-transact-sql.md).  
  
 ÉTAT  **=**  {DÉMARRÉ | **ARRÊTÉ** | DÉSACTIVÉ}  
 Correspond à l'état du point de terminaison lors de sa création. Si l'état n'est pas précisé lors de la création du point de terminaison, STOPPED est la valeur par défaut.  
  
 STARTED  
 Le point de terminaison est lancé et écoute activement les connexions.  
  
 DISABLED  
 Le point de terminaison est désactivé. Dans cet état, le serveur écoute les requêtes du port mais renvoie des erreurs aux clients.  
  
 **ARRÊTÉ**  
 Le point de terminaison est arrêté. Dans cet état, le serveur n'écoute pas le port du point de terminaison et ne répond à aucune tentative de requête visant l'utilisation du point de terminaison.  
  
 Pour modifier l’état, utilisez [ALTER ENDPOINT &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-endpoint-transact-sql.md).  
  
 AS { TCP }  
 Spécifie le protocole de transport à utiliser.  
  
 FOR { TSQL | SERVICE_BROKER | DATABASE_MIRRORING }  
 Spécifie le type de charge utile.  
  
 Actuellement, il n'existe pas d'argument [!INCLUDE[tsql](../../includes/tsql-md.md)] spécifique à une langue à passer au paramètre `<language_specific_arguments>`.  
  
 **Option de protocole TCP**  
  
 Les arguments suivants s'appliquent uniquement à l'option du protocole TCP.  
  
 LISTENER_PORT  **=**  *listenerPort*  
 Spécifie le numéro du port écouté pour les connexions par le protocole TCP/IP Service Broker. Par convention, 4022 est utilisé mais n'importe quel numéro entre 1024 et 32767 est valide.  
  
 LISTENER_IP  **=**  tous les | **(***4-partie-ip* **)** | **(** »*ip_address_v6*» **)**  
 Spécifie l'adresse IP que le point de terminaison va écouter. La valeur par défaut est ALL. Ce qui signifie que l'écouteur acceptera une connexion sur n'importe quelle adresse IP valide.  
  
 Si vous configurez la mise en miroir de bases de données avec une adresse IP au lieu d'un nom de domaine complet (`ALTER DATABASE SET PARTNER = partner_IP_address` ou `ALTER DATABASE SET WITNESS = witness_IP_address`), vous devez spécifier `LISTENER_IP =IP_address` au lieu de `LISTENER_IP=ALL` lorsque vous créez des points de terminaison de mise en miroir.  
  
 **Options SERVICE_BROKER et DATABASE_MIRRORING**  
  
 Les arguments AUTHENTICATION et ENCRYPTION suivants sont communs aux options SERVICE_BROKER et DATABASE_MIRRORING.  
  
> [!NOTE]  
>  Pour les options propres à SERVICE_BROKER, consultez la section « Options SERVICE_BROKER » ci-dessous. Pour les options propres à DATABASE_MIRRORING, consultez la section « Options DATABASE_MIRRORING » ci-dessous.  
  
 AUTHENTIFICATION  **=**  \<authentication_options > Spécifie les conditions d’authentification TCP/IP pour les connexions pour ce point de terminaison. Le paramètre par défaut est WINDOWS.  
  
 Parmi les méthodes d'authentification prises en charge figurent NTLM et/ou Kerberos.  
  
> [!IMPORTANT]  
>  Toutes les connexions de mise en miroir situées sur une instance du serveur utilisent un point de terminaison de mise en miroir de bases de données unique. Toutes les tentatives de création d'un autre point de terminaison de mise en miroir de bases de données échouent.  
  
 **\<authentication_options > :: =**  
  
 **WINDOWS** [{NTLM | KERBEROS | **NEGOTIATE** }]  
 Indique que le point de terminaison doit se connecter à l'aide du protocole d'authentification Windows pour authentifier les points de terminaison. Il s'agit du paramètre par défaut.  
  
 Si vous spécifiez une méthode d'autorisation (NTLM ou KERBEROS), cette méthode est utilisée en tant que protocole d'authentification. Avec la valeur par défaut, NEGOTIATE, le point de terminaison utilise le protocole de négociation Windows pour choisir NTLM ou Kerberos.  
  
 CERTIFICAT *nom_certificat*  
 Spécifie que le point de terminaison doit authentifier la connexion à l’aide du certificat spécifié par *nom_certificat* pour établir l’identité d’autorisation. Le point de terminaison éloigné doit disposer d'un certificat dont la clé publique correspond à la clé privée du certificat spécifié.  
  
 WINDOWS [{NTLM | KERBEROS | **NEGOTIATE** }] CERTIFICAT *nom_certificat*  
 Indique que le point de terminaison doit essayer de se connecter à l'aide de l'authentification Windows et qu'en cas d'échec, il doit essayer en utilisant le certificat spécifié.  
  
 CERTIFICAT *nom_certificat* WINDOWS [{NTLM | KERBEROS | **NEGOTIATE** }]  
 Indique que le point de terminaison doit essayer de se connecter à l'aide du certificat spécifié et qu'en cas d'échec, il doit essayer en utilisant l'authentification Windows.  
  
 CHIFFREMENT = {DÉSACTIVÉ | PRISE EN CHARGE | **REQUIRED** } [ALGORITHME { **AES** | RC4 | AES RC4 | RC4 AES}]  
 Spécifie si le chiffrement est utilisé dans le processus. La valeur par défaut est REQUIRED.  
  
 DISABLED  
 Spécifie que les données envoyées sur une connexion ne sont pas chiffrées.  
  
 SUPPORTED  
 Spécifie que les données sont chiffrées uniquement si le point de terminaison opposé spécifie SUPPORTED ou REQUIRED.  
  
 REQUIRED  
 Indique que les connexions à ce point de terminaison doivent recourir au chiffrement. Par conséquent, pour se connecter à ce point de terminaison, un autre point de terminaison doit avoir l'argument ENCRYPTION défini sur SUPPORTED ou REQUIRED.  
  
 Vous pouvez éventuellement utiliser l'argument ALGORITHM pour spécifier le type de chiffrement utilisé par le point de terminaison, comme suit :  
  
 **AES**  
 Indique que le point de terminaison doit utiliser l'algorithme AES. Ceci est la valeur par défaut dans [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] et versions ultérieures.  
  
 RC4  
 Indique que le point de terminaison doit utiliser l'algorithme RC4. Ceci est la valeur par défaut via [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
> [!NOTE]  
>  L'algorithme RC4 est uniquement pris en charge pour des raisons de compatibilité descendante. Le nouveau matériel ne peut être chiffré à l'aide de RC4 ou de RC4_128 que lorsque la base de données se trouve dans le niveau de compatibilité 90 ou 100. (Non recommandé.) Utilisez à la place un algorithme plus récent, tel qu'un des algorithmes AES. Dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et versions ultérieures, le matériel chiffré à l’aide de RC4 ou RC4_128 peut être déchiffré dans n’importe quel niveau de compatibilité.  
  
 AES RC4  
 Indique que les deux points de terminaison négocieront un algorithme de chiffrement avec ce point de terminaison, en donnant la préférence à l'algorithme AES.  
  
 RC4 AES  
 Indique que les deux points de terminaison négocieront un algorithme de chiffrement avec ce point de terminaison, en donnant la préférence à l'algorithme RC4.  
  
> [!NOTE]  
>  L'algorithme RC4 est déconseillé. [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Nous vous recommandons d'utiliser AES.  
  
 Si les deux points de terminaison spécifient les deux algorithmes mais dans des ordres différents, le point de terminaison acceptant la connexion a le dernier mot.  
  
 **Options SERVICE_BROKER**  
  
 Les arguments suivants sont propres à l'option SERVICE_BROKER.  
  
 MESSAGE_FORWARDING  **=**  {ACTIVÉ | **DÉSACTIVÉ** }  
 Détermine si les messages reçus par ce point de terminaison qui sont destinés à des services situés ailleurs seront transférés.  
  
 ENABLED  
 Transfère les messages si une adresse de transfert est disponible.  
  
 DISABLED  
 Annule les messages destinés à des services situés ailleurs. Il s'agit du paramètre par défaut.  
  
 MESSAGE_FORWARD_SIZE  **=**  *forward_size*  
 Indique l'espace de stockage maximal, en mégaoctets, à allouer au point de terminaison lors du stockage des messages à transférer.  
  
 **Options DATABASE_MIRRORING**  
  
 L'argument suivant est propre à l'option DATABASE_MIRRORING.  
  
 RÔLE  **=**  {TÉMOIN | PARTENAIRE | TOUS LES}  
 Spécifie le ou les rôles de mise en miroir de bases de données pris en charge par le point de terminaison.  
  
 WITNESS  
 Permet au point de terminaison de remplir le rôle de témoin dans le processus de mise en miroir de bases de données.  
  
> [!NOTE]  
>  Pour [!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)], WITNESS est la seule option disponible.  
  
 PARTNER  
 Permet au point de terminaison de remplir le rôle de partenaire dans le processus de mise en miroir de bases de données.  
  
 ALL  
 Permet au point de terminaison de remplir le rôle de témoin et de partenaire dans le processus de mise en miroir de bases de données.  
  
 Pour plus d’informations sur ces rôles, consultez [mise en miroir de base de données &#40; SQL Server &#41; ](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
> [!NOTE]  
>  Aucun port par défaut n'est associé à DATABASE_MIRRORING.  
  
## <a name="remarks"></a>Notes  
 Les instructions ENDPOINT DDL ne peuvent pas être exécutées au sein d'une transaction utilisateur. Les instructions ENDPOINT DDL n'échouent pas, même si une transaction active au niveau d'isolement d'instantané utilise le point de terminaison faisant l'objet d'une modification.  
  
 Les requêtes peuvent être exécutées sur un ENDPOINT par :  
  
-   Membres de **sysadmin** rôle serveur fixe  
  
-   le propriétaire du point de terminaison ;  
  
-   les utilisateurs ou groupes disposant de l'autorisation CONNECT sur le point de terminaison.  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation CREATE ENDPOINT ou l'appartenance au rôle serveur fixe **sysadmin** . Pour plus d’informations, consultez [Autorisations de point de terminaison GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-endpoint-permissions-transact-sql.md).  
  
## <a name="example"></a>Exemple  
  
### <a name="creating-a-database-mirroring-endpoint"></a>Création d'un point de terminaison pour la mise en miroir de bases de données  
 L'exemple suivant crée un point de terminaison pour la mise en miroir de bases de données. Le point de terminaison utilise le port numéro `7022`, bien que tout numéro de port disponible convienne. Ce point est configuré en vue d'utiliser l'authentification Windows associée uniquement à Kerberos. L'option `ENCRYPTION` est paramétrée sur la valeur non définie par défaut `SUPPORTED` afin de prendre en charge les données chiffrées ou non. Le point de terminaison est configuré pour prendre en charge les rôles de partenaire et de témoin.  
  
```  
CREATE ENDPOINT endpoint_mirroring  
    STATE = STARTED  
    AS TCP ( LISTENER_PORT = 7022 )  
    FOR DATABASE_MIRRORING (  
       AUTHENTICATION = WINDOWS KERBEROS,  
       ENCRYPTION = SUPPORTED,  
       ROLE=ALL);  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/alter-endpoint-transact-sql.md)   
 [Choisir un algorithme de chiffrement](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [DROP ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/drop-endpoint-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

