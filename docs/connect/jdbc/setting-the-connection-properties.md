---
title: "Définition des propriétés de connexion | Documents Microsoft"
ms.custom: 
ms.date: 04/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1b62700-f046-488d-bd6b-a5cd8fc345b7
caps.latest.revision: 154
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 56dbb81f9d30ccb41a6247c4fefda9d6ecd703a6
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="setting-the-connection-properties"></a>Définition des propriétés de connexion
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Les propriétés de chaîne de connexion peuvent être spécifiées de plusieurs manières :  
  
-   En tant que nom = propriétés de valeur dans l’URL de connexion lorsque vous vous connectez à l’aide de la classe DriverManager.  
  
-   En tant que nom = valeur des propriétés dans le *propriétés* paramètre de la méthode de connexion dans la classe DriverManager.  
  
-   En tant que valeurs dans la méthode setter appropriée de la source de données du pilote. Exemple :  
  
    ```  
  
    datasource.setServerName(value)  
    datasource.setDatabaseName(value)  
  
    ```  
  
## <a name="remarks"></a>Notes  
 Les noms de propriétés ne sont pas sensibles à la casse et les noms de propriétés dupliqués sont résolus dans l'ordre suivant :  
  
1.  Arguments API (utilisateur et mot de passe)  
  
2.  Collection de propriétés.  
  
3.  Dernière instance de la chaîne de connexion.  
  
 Par ailleurs, des valeurs inconnues sont autorisées dans les noms de propriétés et leurs valeurs ne sont pas validées par le pilote JDBC concernant la sensibilité à la casse.  
  
 Les synonymes sont autorisés et sont résolus dans l'ordre, tout comme les noms de propriétés dupliqués.  
  
 Le tableau suivant répertorie toutes les propriétés de chaîne de connexion actuellement disponibles pour le pilote JDBC.  
  
|Propriété|Type|Valeur par défaut| Description|  
|--------------|----------|-------------|-----------------|  
|accessToken|Chaîne|Null|Utilisez cette propriété pour se connecter à une base de données SQL à l’aide d’un jeton d’accès. **accessToken** ne peut pas être définie à l’aide de l’URL de connexion.|  
|applicationIntent|Chaîne|ReadWrite|Déclare le type de la charge de travail de l'application lors de la connexion à un serveur. Les valeurs possibles sont **ReadOnly** et **ReadWrite**. Pour plus d’informations, consultez [prise en charge du pilote JDBC pour la haute disponibilité, la récupération d’urgence](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md).|  
|applicationName|Chaîne<br /><br /> [<=128 char]|Null|Le nom de l’application, ou «[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]» si aucun nom n’est fourni. Utilisé pour identifier l’application dans différentes [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] profilage et outils de journalisation.|  
|authentification|Chaîne|NotSpecified|À partir de Microsoft JDBC Driver 6.0 pour SQL Server, cette propriété facultative indique quelle méthode d’authentification SQL à utiliser pour la connexion. Les valeurs possibles sont **ActiveDirectoryIntegrated**, **ActiveDirectoryPassword**, **SqlPassword** et la valeur par défaut **NotSpecified**.<br /><br /> Utilisez **ActiveDirectoryIntegrated** pour se connecter à une base de données SQL à l’aide de l’authentification Windows intégrée.<br /><br /> Utilisez **ActiveDirectoryPassword** pour se connecter à une base de données SQL à l’aide d’un nom principal de Azure AD et un mot de passe.<br /><br /> Utilisez **SqlPassword** pour se connecter à un à l’aide de SQL Server **nom d’utilisateur**/**utilisateur** et **mot de passe** propriétés.<br /><br /> Utilisez **NotSpecified** si aucune de ces méthodes d’authentification est nécessaire.<br /><br /> **Important :** si l’authentification est définie sur ActiveDirectoryIntegrated, les deux bibliothèques suivantes doit être installé : **SQLJDBC_AUTH. DLL** (disponible dans le package de pilotes JDBC) et Azure Active Directory Authentication Library pour SQL Server (**ADALSQL. DLL**) il n’est disponible dans plusieurs langues (x86 et amd64) dans le centre de téléchargement [Microsoft Active Directory Authentication Library pour Microsoft SQL Server](https://www.microsoft.com/en-us/download/details.aspx?id=48742). Le pilote JDBC prend uniquement en charge la version **1.0.2028.318 et versions ultérieures** pour la ADALSQL. DLL.<br /><br /> **Remarque :** lorsque la propriété d’authentification est définie à toute valeur autre que **NotSpecified**, le pilote par défaut utilise le chiffrement Secure Sockets Layer (SSL).<br /><br /> Pour plus d’informations sur la façon de configurer l’authentification Azure Active Directory, visitez [la connexion à SQL de base de données en utilisant authentification Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/sql-database-aad-authentication/).|  
|authenticationScheme|Chaîne|« NativeAuthentication »|Indique le type de sécurité intégrée de votre application à utiliser. Les valeurs possibles sont **Java Kerberos** et la valeur par défaut **NativeAuthentication**.<br /><br /> Lorsque vous utilisez **authenticationScheme = Java Kerberos**, vous devez spécifier le nom de domaine complet (FQDN) dans le **nom_serveur** ou **serverSpn** propriété. Sinon, une erreur se produira (serveur introuvable dans la base de données Kerberos).<br /><br /> Pour plus d’informations sur l’utilisation de **authenticationScheme**, consultez [à l’aide de l’authentification intégrée Kerberos pour se connecter à SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md).|  
|columnEncryptionSetting|Chaîne<br /><br /> [« Activé » &#124; » Désactivé] »|Désactivé|Défini sur « Activé » pour utiliser le début de la fonctionnalité Always Encrypted (AE) avec le pilote Microsoft JDBC 6.0 pour SQL Server. Quand la fonctionnalité AE est activée, le pilote JDBC chiffre et déchiffre de manière transparente les données sensibles stockées dans des colonnes de base de données chiffrées sur l’ordinateur SQL Server.<br /><br /> Consultez [à l’aide d’Always Encrypted avec le pilote JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md) pour plus d’informations.<br /><br /> **Remarque :** Always Encrypted est disponible avec SQL Server 2016 ou versions ultérieures.|  
|databaseName, base de données|Chaîne<br /><br /> [<=128 char]|Null|Nom de la base de données à laquelle se connecter. S'il n'est pas indiqué, une connexion à la base de données par défaut est établie.|  
|disableStatementPooling|boolean<br /><br /> [« true » &#124; » False] »|true|Actuellement, seule la valeur « true » est prise en charge. En cas de définition sur « false », une exception se produit.|  
|encrypt|boolean<br /><br /> [« true » &#124; » False] »|false|Affectez la valeur « true » pour spécifier que le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] utilise le chiffrement Secure Sockets Layer (SSL) pour toutes les données envoyées entre le client et le serveur si le serveur possède un certificat installé. La valeur par défaut est false.<br /><br /> À partir de Microsoft JDBC Driver 6.0 pour SQL Server, il existe une nouvelle connexion paramètre « authentification » qui utilise le chiffrement SSL par défaut. Pour plus d’informations, consultez la propriété « authentification ».|  
|failoverPartner|Chaîne|Null|Nom du serveur de basculement utilisé dans la configuration de la mise en miroir de bases de données. Cette propriété est utilisée en cas d'échec de la connexion initiale au serveur principal ; après avoir établi la connexion initiale, cette propriété est ignorée. Elle doit être utilisée avec la propriété databaseName.<br /><br /> **Remarque :** le pilote ne prend pas en charge en spécifiant le numéro de port instance pour l’instance de serveur partenaire de basculement dans le cadre de la propriété failoverPartner dans la chaîne de connexion. Toutefois, la spécification des propriétés serverName, instanceName et portNumber de l'instance du serveur principal et la propriété failoverPartner de l'instance du partenaire de basculement dans la même chaîne de connexion est prise en charge.<br /><br /> Si vous spécifiez un nom de réseau virtuel dans le **Server** propriété de connexion, vous ne pouvez pas utiliser la mise en miroir de base de données. Consultez [prise en charge du pilote JDBC pour la haute disponibilité, la récupération d’urgence](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md) pour plus d’informations.|  
|hostNameInCertificate|Chaîne|Null|Nom d’hôte à utiliser pour valider la [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] certificat SSL.<br /><br /> Si la propriété hostNameInCertificate n’est pas spécifié ou défini comme null, le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] utilisera le **nom_serveur** valeur de propriété de l’URL de connexion comme nom d’hôte pour valider la [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] certificat SSL.<br /><br /> **Remarque :** cette propriété est utilisée en association avec le **chiffrer**/**authentification** propriétés et le **trustServerCertificate**propriété. Cette propriété affecte la validation du certificat si et seulement si la connexion utilise le chiffrement Secure Sockets Layer (SSL) et le **trustServerCertificate** a la valeur « false ». Assurez-vous que la valeur passée à **hostNameInCertificate** correspond exactement au nom DNS ou le nom commun (CN) dans l’autre nom de l’objet dans le certificat de serveur pour une connexion SSL réussisse. Pour plus d’informations, consultez [prise en charge de SSL compréhension](../../connect/jdbc/understanding-ssl-support.md).|  
|INSTANCENAME|Chaîne<br /><br /> [<=128 char]|Null|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] pour se connecter au nom de l’instance. S'il n'est pas spécifié, une connexion à l'instance par défaut est établie. Si l'instanceName et le port sont tous deux spécifiés, consultez les notes relatives au port.<br /><br /> Si vous spécifiez un nom de réseau virtuel dans le **Server** propriété de connexion, vous ne pouvez pas utiliser **instanceName** propriété de connexion. Consultez [prise en charge du pilote JDBC pour la haute disponibilité, la récupération d’urgence](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md) pour plus d’informations.|  
|integratedSecurity|boolean<br /><br /> [« true » &#124; » False] »|false|Affectez la valeur « true » pour indiquer que les informations d’identification Windows seront utilisées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sur les systèmes d’exploitation Windows. Si la valeur est « true », le pilote JDBC recherche des références déjà fournies lors de la connexion à l'ordinateur ou au réseau dans la mémoire cache des références de l'ordinateur local.<br /><br /> La valeur « true » (avec **authenticationscheme = Java Kerberos**), pour indiquer que les informations d’identification Kerberos seront utilisées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Pour plus d’informations sur l’authentification Kerberos, consultez [à l’aide de l’authentification intégrée Kerberos pour se connecter à SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md). <br /><br /> Si la valeur est « false », le nom d'utilisateur et le mot de passe doivent être fournis.| 
|keyStoreAuthentication|Chaîne|Null| À partir de Microsoft JDBC Driver 6.0 pour SQL Server, cette propriété identifie le magasin de clés à configurer en toute transparence pour la connexion avec le chiffrement intégral et détermine le mécanisme d’authentification utilisé pour s’authentifier auprès du magasin de clés. Microsoft JDBC Driver 6.0 pour SQL Server prend en charge le paramètre de du magasin de clés de Java en toute transparence à l’aide de cette propriété pour laquelle vous devez définir «**keyStoreAuthentication = JavaKeyStorePassword**». Notez que pour utiliser cette propriété, vous devez également définir le **keyStoreLocation** et **keyStoreSecret** propriétés pour le magasin de clés de Java. <br/><br/>Pour plus d’informations, visitez [à l’aide d’Always Encrypted avec le pilote JDBC](https://msdn.microsoft.com/library/mt591987%28v=sql.110%29.aspx?f=255&MSPPError=-2147217396). 
|keyStoreLocation|Chaîne|Null|Lorsque **keyStoreAuthentication = JavaKeyStorePassword**, le **keyStoreLocation** propriété identifie le chemin d’accès au fichier keystore Java qui stocke la clé principale de colonne à utiliser avec Always Encrypted données. Notez que le chemin d’accès doit inclure le nom de fichier du magasin de clés.<br/><br/>Pour plus d’informations, visitez [à l’aide d’Always Encrypted avec le pilote JDBC](https://msdn.microsoft.com/library/mt591987%28v=sql.110%29.aspx?f=255&MSPPError=-2147217396).
|keyStoreSecret|Chaîne|Null|Lorsque **keyStoreAuthentication = JavaKeyStorePassword**, le **keyStoreSecret** propriété identifie le mot de passe à utiliser pour le keystore ainsi que pour la clé. Notez que pour utiliser le magasin de clés le keystore Java et le mot de passe de clé doit être identiques.<br/><br/>Pour plus d’informations, visitez [à l’aide d’Always Encrypted avec le pilote JDBC](https://msdn.microsoft.com/library/mt591987%28v=sql.110%29.aspx?f=255&MSPPError=-2147217396).
|lastUpdateCount|boolean<br /><br /> [« true » &#124; » False] »|true|Une valeur « true » retourne uniquement le dernier nombre de mises à jour à partir d'une instruction SQL transmise au serveur et peut être utilisée dans des instructions uniques SELECT, INSERT ou DELETE pour ignorer les nombres de mises à jours supplémentaires causés par les déclencheurs du serveur. La définition de cette propriété sur « false » provoque le retour de tous les nombres de mises à jour, y compris ceux retournés par les déclencheurs du serveur.<br /><br /> **Remarque :** cette propriété s’applique uniquement lorsqu’elle est utilisée avec la [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md) méthodes. Tous les autres exécuter les méthodes retournent tous les résultats et mettre à jour des nombres. Cette propriété affecte uniquement les nombres de mises à jour retournés par les déclencheurs du serveur. Elle n'affecte pas les jeux de résultats ou les erreurs provenant de l'exécution du déclencheur.|  
|lockTimeout|int|-1|Nombre de millisecondes à attendre avant que la base de données ne rapporte l'expiration d'un délai de verrouillage. Par défaut, la durée de l'attente est indéterminée. Si elle est spécifiée, cette valeur devient la valeur par défaut pour toutes les instructions de la connexion. Notez que **Statement.setQueryTimeout()** peut être utilisé pour définir le délai d’attente pour des instructions spécifiques. La valeur peut être 0, ce qui signifie aucune attente.|  
|loginTimeout|int [0..65535]|15|Nombre de secondes que le pilote doit attendre avant l'expiration d'une connexion qui a échoué. La valeur zéro indique que le délai d'attente correspond au délai d'attente système par défaut, lequel est de 15 secondes. Une valeur différente de zéro correspond au nombre de secondes que le pilote doit attendre avant l'expiration d'une connexion échouée.<br /><br /> Si vous spécifiez un nom de réseau virtuel dans le **Server** propriété de connexion, vous devez spécifier une valeur de délai d’attente de trois minutes ou plus pour permettre suffisamment de temps pour une connexion de basculement réussisse. Consultez [prise en charge du pilote JDBC pour la haute disponibilité, la récupération d’urgence](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md) pour plus d’informations.|  
|multiSubnetFailover|Booléen|false|Toujours spécifier **multiSubnetFailover = true** lors de la connexion à l’écouteur de groupe de disponibilité d’un [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] groupe de disponibilité ou un [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] Instance de Cluster de basculement. **multiSubnetFailover = true** configure [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] pour fournir une détection plus rapide et la connexion au serveur (actuellement) actif. Les valeurs possibles sont true et false. Consultez [prise en charge du pilote JDBC pour la haute disponibilité, la récupération d’urgence](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md) pour plus d’informations.<br /><br /> Vous pouvez accéder par programme le **multiSubnetFailover** propriété de connexion avec [getPropertyInfo](../../connect/jdbc/reference/getpropertyinfo-method-sqlserverdriver.md), [getMultiSubnetFailover](../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md), et [ setMultiSubnetFailover](../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md).<br /><br /> **Remarque :** commençant par le pilote Microsoft JDBC 6.0 pour SQL Server, il n’est plus requis pour définir multiSubnetFailover sur « True » lors de la connexion à un écouteur de groupe de disponibilité. Une nouvelle propriété, **transparentNetworkIPResolution**, qui est activé par défaut, fournit la détection et la connexion au serveur (actuellement) actif.|  
|packetSize|int [-1 &#124; 0 &#124; 512..32767]|8000|Taille de paquet du réseau utilisée pour communiquer avec SQL Server, spécifiée en octets. Une valeur de -1 indique l'utilisation de la taille de paquet par défaut du serveur. Une valeur de 0 indique la valeur maximale, à savoir 32767. Si cette propriété est définie sur une valeur située en dehors des limites acceptables, une exception se produit.<br /><br /> **Important :** nous ne recommandons pas à l’aide de la propriété packetSize lorsque le chiffrement est activé (chiffrer = true). Sinon, le pilote risque de générer une erreur de connexion. Pour plus d’informations, consultez la [setPacketSize](../../connect/jdbc/reference/setpacketsize-method-sqlserverdatasource.md) méthode de la [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) classe.|  
|password|Chaîne<br /><br /> [<=128 char]|Null|Le mot de passe, en cas de connexion avec l’utilisateur SQL et le mot de passe.<BR/>Pour les connexions Kerberos avec le nom de principal et le mot de passe, cette propriété est définie pour le mot de passe Principal Kerberos.|  
|portNumber, port|int [0..65535]|1433|Le port où [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] est à l’écoute. Si le numéro du port est spécifié dans la chaîne de connexion, aucune demande n'est formulée à sqlbrowser. Lorsque le port et instanceName sont spécifiés, la connexion se fait vers le port spécifié. Toutefois, le **instanceName** est validé et une erreur est générée s’il ne correspond pas au port.<br /><br /> **Important :** nous recommandons que le numéro de port toujours être spécifié, comme cela est plus sûre que l’utilisation de sqlbrowser.|  
|responseBuffering|Chaîne<br /><br /> [« complet » &#124; » Adaptive »]|adaptive|Si cette propriété a la valeur « adaptive », les données possibles minimales sont mises en mémoire tampon en cas de nécessité. Le mode par défaut est « adaptive ».<br /><br /> Lorsque cette propriété a la valeur « full », le jeu de résultats entier est lu à partir du serveur lorsqu'une instruction est exécutée.<br /><br /> **Remarque :** après la mise à niveau le pilote JDBC à partir de la version 1.2, comportement de mise en mémoire tampon par défaut sera « adaptive ». Si votre application n’a jamais défini la propriété « responseBuffering » et que vous souhaitez conserver le comportement par défaut de la version 1.2 dans votre application, vous devez définir la valeur « Full » la propriété responseBufferring dans les propriétés de connexion ou à l’aide de la [ setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) méthode de la [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) objet.|  
|selectMethod|Chaîne<br /><br /> [« direct » &#124; » curseur »]|direct|Si cette propriété a la valeur « cursor », un curseur de base de données est créé pour chaque requête créée sur la connexion pour les curseurs TYPE_FORWARD_ONLY et CONCUR_READ_ONLY. Cette propriété n'est généralement requise que si l'application génère de très grands jeux de résultats qui ne peuvent pas être entièrement contenus dans la mémoire du client. Si cette propriété est définie sur « curseur », seul un nombre restreint de lignes de jeux de résultats est conservé dans la mémoire du client. Par défaut, toutes les lignes de jeux de résultats sont conservées dans la mémoire du client. Ce comportement est le plus rapide si l'application doit traiter toutes les lignes.|  
|sendStringParametersAsUnicode|boolean<br /><br /> [« true » &#124; » False] »|true|Si le **sendStringParametersAsUnicode** est définie sur « true », les paramètres String sont envoyés au serveur au format Unicode.<br /><br /> Si le **sendStringParametersAsUnicode** est définie sur « false », les paramètres de chaîne sont envoyés au serveur dans un format non-Unicode, par exemple ASCII/MBCS au lieu d’Unicode.<br /><br /> La valeur par défaut pour le **sendStringParametersAsUnicode** propriété est « true ».<br /><br /> **Remarque :** le **sendStringParametersAsUnicode** propriété est uniquement vérifiée lors de l’envoi d’une valeur de paramètre avec **CHAR**, **VARCHAR**, ou **LONGVARCHAR** types JDBC. Les nouvelles méthodes de caractères nationaux JDBC 4.0, telles que les méthodes setNString, setNCharacterStream et setNClob de [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) et [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) des classes, toujours envoyer leurs valeurs de paramètre sur le serveur au format Unicode, quel que soit le paramètre de cette propriété.<br /><br /> Pour des performances optimales avec les **CHAR**, **VARCHAR**, et **LONGVARCHAR** les types de données JDBC, une application doit affecter la ** sendStringParametersAsUnicode** propriété à « false » et utilisez le setString, setCharacterStream et méthodes de caractères non nationaux setClob de la [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) et [ SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) classes.<br /><br /> Lorsque l’application définit la **sendStringParametersAsUnicode** à la valeur « false » et utilise une méthode de caractères non nationaux pour accéder aux données Unicode types côté serveur (tel que **nchar**, **nvarchar** et **ntext**), certaines données peuvent être perdues si le classement de base de données ne prend pas en charge les caractères dans les paramètres de chaîne passés par la méthode des caractères non nationaux.<br /><br /> Notez qu’une application doit utiliser les méthodes de caractères nationaux setNString, setNCharacterStream et setNClob de la [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) et [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) des classes pour le **NCHAR**, **NVARCHAR**, et **LONGNVARCHAR** types de données JDBC.|  
|sendTimeAsDatetime|boolean<br /><br /> [« true » &#124; » False] »|true|Cette propriété a été ajoutée dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] version 3.0 du pilote JDBC.<br /><br /> Lorsque la valeur est true, les valeurs java.sql.Time être envoyées au serveur en tant que [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **datetime** valeurs.<br /><br /> Si la valeur est false, les valeurs java.sql.Time être envoyées au serveur en tant que [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **temps** valeurs.<br /><br /> **sendTimeAsDatetime** peut également être modifié par programmation avec [SQLServerDataSource.setSendTimeAsDatetime](../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).<br /><br /> La valeur par défaut de cette propriété sera éventuellement modifiée dans une prochaine version.<br /><br /> Pour plus d’informations sur la façon dont [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] des valeurs java.sql.Time avant de les envoyer au serveur, consultez [configurer comment les valeurs java.sql.Time sont envoyées au serveur](../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).|  
|serverName, serveur|Chaîne|Null|L’ordinateur exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].<br /><br /> Vous pouvez également spécifier le nom de réseau virtuel d’un [!INCLUDE[ssHADR](../../includes/sshadr_md.md)] groupe de disponibilité. Consultez [prise en charge du pilote JDBC pour la haute disponibilité, la récupération d’urgence](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md) pour plus d’informations.|  
|serverSpn|Chaîne|Null|À compter de Microsoft JDBC Driver 4.2 pour SQL Server, cette propriété facultative peut être utilisée pour spécifier le nom de principal du service (SPN) pour une connexion Java Kerberos.  Il est utilisé conjointement avec **authenticationScheme**.<br /><br /> Pour spécifier le nom principal de service, il peut être sous la forme : «MSSQLSvc/fqdn:port@REALM» où fqdn désigne le nom de domaine complet, le port est le numéro de port et REALM désigne le domaine Kerberos du serveur SQL en majuscules.<br /><br /> Remarque : le @REALM est facultatif si le domaine par défaut du client (comme spécifié dans la configuration de Kerberos) est le même que le domaine Kerberos pour SQL Server.<br /><br /> Pour plus d’informations sur l’utilisation de **serverSpn** avec Java Kerberos, consultez [à l’aide de l’authentification intégrée Kerberos pour se connecter à SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md).|  
|serverNameAsACE|boolean<br /><br /> [« true » &#124; » False] »|false|À compter de Microsoft JDBC Driver 6.0 pour SQL Server, affectez la valeur « true » pour indiquer que le pilote doit traduire le nom du serveur Unicode en codage compatible ASCII (Punycode) pour la connexion. Si ce paramètre a la valeur « false », le pilote se connecte à l’aide du nom de serveur tel qu’il est fourni par l’utilisateur.<br /><br /> Consultez [fonctionnalités internationales du pilote JDBC](../../connect/jdbc/international-features-of-the-jdbc-driver.md) pour plus d’informations.|  
|TransparentNetworkIPResolution|boolean<br /><br /> [« true » &#124; » False] »|true|À partir de Microsoft JDBC Driver 6.0 pour SQL Server, de cette propriété, transparentNetworkIPResolution, fournit une détection plus rapide et la connexion au serveur (actuellement) actif. Les valeurs possibles sont true et false par true comme valeur par défaut.<br /><br /> Avant le pilote Microsoft JDBC 6.0 pour SQL Server, une application devait définir la chaîne de connexion à inclure « multiSubnetFailover = true » pour indiquer qu’elle était connectée à un groupe de disponibilité AlwaysOn. Sans définir le mot clé de connexion multiSubnetFailover sur true, une application peut rencontrer un délai d’attente lors de la connexion à un groupe de disponibilité AlwaysOn. À partir de Microsoft JDBC Driver 6.0 pour SQL Server, une application n’a pas besoin définir multiSubnetFailover sur « true » plus. <br /><br />**Remarque :** lorsque transparentNetworkIPResolution = true, la première tentative de connexion utilise 500 ms en tant que le délai d’attente. N’importe quel attemps suivantes utilisent la même logique de délai d’attente que celle utilisée par la propriété multiSubnetFailover.|  
|columnEncryptionSetting|boolean<br /><br /> [« true » &#124; » False] »|false|Affectez la valeur « true » pour utiliser la fonctionnalité Always Encrypted (AE) à compter de Microsoft JDBC Driver 6.0 pour SQL Server. Quand la fonctionnalité AE est activée, le pilote JDBC chiffre et déchiffre de manière transparente les données sensibles stockées dans des colonnes de base de données chiffrées sur l’ordinateur SQL Server.<br /><br /> Consultez [à l’aide d’Always Encrypted avec le pilote JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md) pour plus d’informations.<br /><br /> **Remarque :** Always Encrypted est disponible avec SQL Server 2016 ou des versions plus récentes.|  
|trustServerCertificate|boolean<br /><br /> [« true » &#124; » False] »|false|Affectez la valeur « true » pour spécifier que le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] ne validera pas le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] certificat SSL.<br /><br /> Si « true », le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] certificat SSL est automatiquement approuvé lorsque la couche de communication est chiffrée à l’aide de SSL.<br /><br /> Si « false », le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] validera le certificat SSL du serveur. Si la validation du certificat de serveur échoue, le pilote génère une erreur et met fin à la connexion. La valeur par défaut est « false ». Assurez-vous que la valeur passée à **nom_serveur** correspond exactement au nom DNS ou le nom commun (CN) dans l’autre nom du sujet du certificat de serveur pour une connexion SSL réussisse. Pour plus d’informations, consultez [prise en charge de SSL compréhension](../../connect/jdbc/understanding-ssl-support.md).<br /><br /> **Remarque :** cette propriété est utilisée en association avec le **chiffrer**/**authentification** propriétés. Cette propriété affecte uniquement la validation du certificat SSL de serveur si et seulement si la connexion utilise le chiffrement SSL.|  
|trustStore|Chaîne|Null|Chemin d'accès (y compris le nom de fichier) au fichier trustStore de certificat. Le fichier trustStore contient la liste des certificats approuvés par le client.<br /><br /> Lorsque cette propriété n'est pas spécifiée ou a la valeur null, le pilote se fie aux règles de recherche de la fabrication du gestionnaire d'approbation pour déterminer le magasin de certificats à utiliser.<br /><br /> **Le TrustManagerFactory SunX509 par défaut tente de localiser les informations approuvées dans l’ordre de recherche suivant :**<br /><br /> Un fichier spécifié par la propriété système de machine virtuelle Java (JVM) « javax.net.ssl.trustStore ».<br /><br /> «\<java-home >/lib/security/jssecacerts » fichier.<br /><br /> «\<java-home >/lib/security/cacerts » fichier.<br /><br /> <br /><br /> Pour plus d’informations, consultez la documentation d’Interface SUNX509 TrustManager sur le site Web de Sun Microsystems.<br /><br /> **Remarque :** cette propriété affecte uniquement la recherche de certificat trustStore si et seulement si la connexion utilise le chiffrement SSL et le **trustServerCertificate** est définie sur « false ».|  
|trustStorePassword|Chaîne|Null|Mot de passe utilisé pour vérifier l'intégrité des données trustStore.<br /><br /> Si la propriété trustStore est définie mais que la propriété trustStorePassword n'est pas définie, l'intégrité du trustStore n'est pas vérifiée.<br /><br /> Lorsque les propriétés trustStore et trustStorePassword ne sont pas spécifiées, le pilote utilise les propriétés système JVM « javax.net.ssl.trustStore » et « javax.net.ssl.trustStorePassword ». Si la propriété système « javax.net.ssl.trustStorePassword » n'est pas spécifiée, l'intégrité du trustStore n'est pas vérifiée.<br /><br /> Si la propriété trustStore n'est pas définie mais que la propriété trustStorePassword est définie, le pilote JDBC utilise le fichier spécifié par la propriété « javax.net.ssl.trustStore » comme magasin d'approbations et l'intégrité du magasin d'approbations est vérifiée à l'aide de la propriété trustStorePassword spécifiée. Cela peut être nécessaire lorsque l'application cliente ne souhaite pas stocker le mot de passe dans la propriété système JVM.<br /><br /> **Remarque :** la propriété trustStorePassword affecte la recherche de certificat trustStore si et seulement si la connexion utilise la connexion SSL et le **trustServerCertificate** est définie sur « false ».|  
|userName, utilisateur|Chaîne<br /><br /> [<=128 char]|Null|L’utilisateur de base de données, en cas de connexion avec l’utilisateur SQL et le mot de passe.<BR/>Pour les connexions Kerberos avec le nom de principal et le mot de passe, cette propriété est définie au nom de Principal Kerberos.|  
|workstationID|Chaîne<br /><br /> [<=128 char]|\<une chaîne vide >|ID de station de travail. Utilisé pour identifier la station de travail spécifique dans différentes [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] profilage et outils de journalisation. Si aucun n’est spécifié, le \<une chaîne vide > est utilisé.|  
|xopenStates|boolean<br /><br /> [« true » &#124; » False] »|false|Définir sur « true » pour spécifier que le pilote retourne les codes d'état compatibles XOPEN dans des exceptions. Par défaut, des codes d'état SQL 99 sont retournés.|  
|gsscredential|org.ietf.jgss.GSSCredential|Null|À partir de Microsoft JDBC Driver 6.2 pour SQL Server, les informations d’identification de l’utilisateur à utiliser pour la délégation contrainte Kerberos peuvent être passées dans cette propriété. <BR/>Cela doit être utilisé avec **integratedSecurity** en tant que **true** et **Java Kerberos** **authenticationscheme**.| 
|jaasConfigurationName|Chaîne|SQLJDBCDriver|À partir de Microsoft JDBC Driver 6.2 pour SQL Server, chaque connexion à SQL Server peut avoir son propre fichier JAAS Login Configuration pour établir les connexions Kerberos. Nom du fichier de Configuration de la connexion peut être transmis via cette propriété. <BR/> Par défaut, le pilote définit propriété `useDefaultCcache = true` pour IBM JVM, et `useTicketCache = true` pour les autres JVM.|
|serverPreparedStatementDiscardThreshold|Entier|10|Contrôle les actions de rejet combien préparées en attente (sp_unprepare) peuvent être en attente par connexion avant l’exécution d’un appel pour nettoyer les handles en attente sur le serveur. Si le paramètre est < = 1 Annuler-préparer les actions seront exécutées immédiatement sur une instruction préparée fermer. Si elle est définie sur > 1, ces appels sont regroupées afin d’éviter le traitement de l’appel sp_unprepare trop souvent.|
|enablePrepareOnFirstPreparedStatementCall|boolean<br /><br /> [« true » &#124; » False] »|false|Si cette configuration est définie sur false, la première exécution d’une instruction préparée appelle sp_executesql et n’a pas préparer une instruction, une fois que la deuxième exécution se produit, elle appelle sp_prepexec et réellement le programme d’installation un descripteur d’instruction préparée.|
|statementPoolingCacheSize|Entier|10|Instructions cachable configurables pour la réutilisation du pool| 
  
> [!NOTE]  
>  Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] prend les valeurs par défaut pour les propriétés de connexion à l’exception de ANSI_DEFAULTS et IMPLICIT_TRANSACTIONS serveur. Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] affecte automatiquement on à ANSI_DEFAULTS et la valeur OFF à IMPLICIT_TRANSACTIONS.  

> [!Note]
> Important : Si l’authentification est définie sur ActiveDirectoryPassword, la bibliothèque suivante sera doivent être incluses dans l’instruction classpath : [azure bibliothèque Active Directory pour java](https://github.com/AzureAD/azure-activedirectory-library-for-java). Il se trouve sur [Maven référentiel](https://mvnrepository.com/artifact/com.microsoft.azure/adal4j). La façon la plus simple pour télécharger la bibliothèque et ses dépendances est à l’aide de Maven : 
 >1. Pour commencer, installez Maven sur votre système. 
 >2. Accédez à la [page GitHub](https://github.com/Microsoft/mssql-jdbc) du pilote
 >3. Téléchargez le fichier pom.xml
 >4. Exécutez la commande Maven suivante pour télécharger la bibliothèque et ses dépendances : dépendance : la copie mvn-dépendances
  
## <a name="see-also"></a>Voir aussi  
 [Connexion à SQL Server avec le pilote JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
 [En Mode FIPS](../../connect/jdbc/fips-mode.md)
  
  
