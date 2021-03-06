---
title: Planification des tâches administratives automatiques dans SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- scheduling administrative tasks [SMO]
- SQL Server Agent [SMO]
- automatic administrative SMO tasks
ms.assetid: 900242ad-d6a2-48e9-8a1b-f0eea4413c16
caps.latest.revision: 40
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ad4b0fa53b7a15d9ff8118336d0ec0b9d31a4b56
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37256051"
---
# <a name="scheduling-automatic-administrative-tasks-in-sql-server-agent"></a>Planification des tâches administratives automatiques dans l'Agent SQL Server
  Dans SMO, l'Agent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est représenté par les objets suivants :  
  
-   L'objet <xref:Microsoft.SqlServer.Management.Smo.Agent.JobServer> possède trois collections de travaux, d'alertes et d'opérateurs.  
  
-   L'objet <xref:Microsoft.SqlServer.Management.Smo.Agent.OperatorCollection> représente une liste de radiomessagerie, d'adresses de messagerie et d'opérateurs net send qui peuvent être notifiés automatiquement de la survenue d'événements par l'Agent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Microsoft.  
  
-   L'objet <xref:Microsoft.SqlServer.Management.Smo.Agent.AlertCollection> représente une liste de circonstances, par exemple des événements système ou des conditions de performance surveillées par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   L'objet <xref:Microsoft.SqlServer.Management.Smo.Agent.JobCollection> est légèrement plus complexe. Il représente une liste de tâches multi-étapes qui s'exécutent en fonctions de planifications spécifiées. Les informations sur les étapes et la planification sont stockées dans les objets <xref:Microsoft.SqlServer.Management.Smo.Agent.JobStep> et <xref:Microsoft.SqlServer.Management.Smo.Agent.JobSchedule>.  
  
 Les objets de l'Agent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] se trouvent dans l'espace de noms <xref:Microsoft.SqlServer.Management.Smo.Agent>.  
  
## <a name="examples"></a>Exemples  
 Pour utiliser un exemple de code qui est fourni, vous devrez choisir l'environnement de programmation, le modèle de programmation et le langage de programmation dans lequel créer votre application. Pour plus d’informations, consultez [créer un projet SMO Visual Basic dans Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) ou [créer un Visual C&#35; projet SMO dans Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
1.  Pour les programmes qui utilisent l'Agent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vous devez inclure l'instruction `Imports` pour qualifier l'espace de noms de l'Agent. Insérez l'instruction après les autres instructions `Imports`, avant toute autre déclaration dans l'application, par exemple :  
  
 `Imports Microsoft.SqlServer.Management.Smo`  
  
 `Imports Microsoft.SqlServer.Management.Common`  
  
 `Imports Microsoft.SqlServer.Management.Smo.Agent`  
  
## <a name="creating-a-job-with-steps-and-a-schedule-in-visual-basic"></a>Création d'un travail avec des étapes et une planification en Visual Basic  
 Cet exemple de code crée un travail avec des étapes et une planification, puis informe un opérateur.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBAgent1](SMO How to#SMO_VBAgent1)]  -->  
  
## <a name="creating-a-job-with-steps-and-a-schedule-in-visual-c"></a>Création d'un travail avec des étapes et une planification en Visual C#  
 Cet exemple de code crée un travail avec des étapes et une planification, puis informe un opérateur.  
  
```  
{  
            //Connect to the local, default instance of SQL Server.  
            Server srv = new Server();  
  
            //Define an Operator object variable by supplying the Agent (parent JobServer object) and the name in the constructor.   
            Operator op = new Operator(srv.JobServer, "Test_Operator");  
  
            //Set the Net send address.   
            op.NetSendAddress = "Network1_PC";  
  
            //Create the operator on the instance of SQL Server Agent.   
            op.Create();  
  
            //Define a Job object variable by supplying the Agent and the name arguments in the constructor and setting properties.   
            Job jb = new Job(srv.JobServer, "Test_Job");  
  
            //Specify which operator to inform and the completion action.   
            jb.OperatorToNetSend = "Test_Operator";  
            jb.NetSendLevel = CompletionAction.Always;  
  
            //Create the job on the instance of SQL Server Agent.   
            jb.Create();  
  
            //Define a JobStep object variable by supplying the parent job and name arguments in the constructor.   
            JobStep jbstp = new JobStep(jb, "Test_Job_Step");  
            jbstp.Command = "Test_StoredProc";  
            jbstp.OnSuccessAction = StepCompletionAction.QuitWithSuccess;  
            jbstp.OnFailAction = StepCompletionAction.QuitWithFailure;  
  
            //Create the job step on the instance of SQL Agent.   
            jbstp.Create();  
  
            //Define a JobSchedule object variable by supplying the parent job and name arguments in the constructor.   
  
            JobSchedule jbsch = new JobSchedule(jb, "Test_Job_Schedule");  
  
            //Set properties to define the schedule frequency, and duration.   
            jbsch.FrequencyTypes = FrequencyTypes.Daily;  
            jbsch.FrequencySubDayTypes = FrequencySubDayTypes.Minute;  
            jbsch.FrequencySubDayInterval = 30;  
            TimeSpan ts1 = new TimeSpan(9, 0, 0);  
            jbsch.ActiveStartTimeOfDay = ts1;  
  
            TimeSpan ts2 = new TimeSpan(17, 0, 0);  
            jbsch.ActiveEndTimeOfDay = ts2;  
            jbsch.FrequencyInterval = 1;  
  
            System.DateTime d = new System.DateTime(2003, 1, 1);  
            jbsch.ActiveStartDate = d;  
  
            //Create the job schedule on the instance of SQL Agent.   
            jbsch.Create();  
        }  
```  
  
## <a name="creating-a-job-with-steps-and-a-schedule-in-powershell"></a>Création d'un travail avec des étapes et une planification dans PowerShell  
 Cet exemple de code crée un travail avec des étapes et une planification, puis informe un opérateur.  
  
```  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Define an Operator object variable by supplying the Agent (parent JobServer object) and the name in the constructor.  
$op = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Operator -argumentlist $srv.JobServer, "Test_Operator"  
  
#Set the Net send address.  
$op.NetSendAddress = "Network1_PC"  
  
#Create the operator on the instance of SQL Agent.  
$op.Create()  
  
#Define a Job object variable by supplying the Agent and the name arguments in the constructor and setting properties.   
$jb = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Job -argumentlist $srv.JobServer, "Test_Job"   
  
#Specify which operator to inform and the completion action.   
$jb.OperatorToNetSend = "Test_Operator";   
$jb.NetSendLevel = [Microsoft.SqlServer.Management.SMO.Agent.CompletionAction]::Always  
  
#Create the job on the instance of SQL Server Agent.   
$jb.Create()  
  
#Define a JobStep object variable by supplying the parent job and name arguments in the constructor.   
$jbstp = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.JobStep -argumentlist $jb, "Test_Job_Step"   
$jbstp.Command = "Test_StoredProc";   
$jbstp.OnSuccessAction = [Microsoft.SqlServer.Management.SMO.Agent.StepCompletionAction]::QuitWithSuccess;   
$jbstp.OnFailAction =[Microsoft.SqlServer.Management.SMO.Agent.StepCompletionAction]::QuitWithFailure;   
  
#Create the job step on the instance of SQL Agent.   
$jbstp.Create();   
  
#Define a JobSchedule object variable by supplying the parent job and name arguments in the constructor.   
$jbsch =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.JobSchedule -argumentlist $jb, "Test_Job_Schedule"   
  
#Set properties to define the schedule frequency, and duration.   
$jbsch.FrequencyTypes =  [Microsoft.SqlServer.Management.SMO.Agent.FrequencyTypes]::Daily  
  
$jbsch.FrequencySubDayTypes = [Microsoft.SqlServer.Management.SMO.Agent.FrequencySubDayTypes]::Minute  
$jbsch.FrequencySubDayInterval = 30  
$ts1 =  New-Object -TypeName TimeSpan -argumentlist 9, 0, 0  
$jbsch.ActiveStartTimeOfDay = $ts1  
$ts2 = New-Object -TypeName TimeSpan -argumentlist 17, 0, 0  
$jbsch.ActiveEndTimeOfDay = $ts2  
$jbsch.FrequencyInterval = 1  
$jbsch.ActiveStartDate = "01/01/2003"  
  
#Create the job schedule on the instance of SQL Agent.   
$jbsch.Create();  
```  
  
## <a name="creating-an-alert-in-visual-basic"></a>Création d'une alerte en Visual Basic  
 Cet exemple de code crée une alerte déclenchée par une condition de performance. La condition doit être fournie selon un format spécifique.  
  
 **ObjectName | CounterName | Instance | ComparisionOp | CompValue**  
  
 Un opérateur est requis pour la notification d'alerte. Le type <xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> doit être placé entre crochets car `operator` est un mot clé Visual Basic.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBAgent3](SMO How to#SMO_VBAgent3)]  -->  
  
## <a name="creating-an-alert-in-visual-c"></a>Création d'une alerte en Visual C#  
 Cet exemple de code crée une alerte déclenchée par une condition de performance. La condition doit être fournie selon un format spécifique.  
  
 **ObjectName | CounterName | Instance | ComparisionOp | CompValue**  
  
 Un opérateur est requis pour la notification d'alerte. Le type <xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> doit être placé entre crochets car `operator` est un mot clé [!INCLUDE[csprcs](../../../includes/csprcs-md.md)].  
  
```  
{  
             //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
  
            //Define an Alert object variable by supplying the SQL Server Agent and the name arguments in the constructor.   
            Alert al = new Alert(srv.JobServer, "Test_Alert");  
  
            //Specify the performance condition string to define the alert.   
            al.PerformanceCondition = "SQLServer:General Statistics|User Connections||>|3";  
  
            //Create the alert on the SQL Agent.   
            al.Create();  
  
            //Define an Operator object variable by supplying the SQL Server Agent and the name arguments in the constructor.   
  
            Operator op = new Operator(srv.JobServer, "Test_Operator");  
            //Set the net send address.   
            op.NetSendAddress = "NetworkPC";  
            //Create the operator on the SQL Agent.   
            op.Create();  
            //Run the AddNotification method to specify the operator is notified when the alert is raised.   
            al.AddNotification("Test_Operator", NotifyMethods.NetSend);  
        }  
```  
  
## <a name="creating-an-alert-in-powershell"></a>Création d'une alerte dans PowerShell  
 Cet exemple de code crée une alerte déclenchée par une condition de performance. La condition doit être fournie selon un format spécifique.  
  
 **ObjectName | CounterName | Instance | ComparisionOp | CompValue**  
  
 Un opérateur est requis pour la notification d'alerte. Le type <xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> doit être placé entre crochets car `operator` est un mot clé [!INCLUDE[csprcs](../../../includes/csprcs-md.md)].  
  
```  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Define an Alert object variable by supplying the SQL Agent and the name arguments in the constructor.  
$al = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Alert -argumentlist $srv.JobServer, "Test_Alert"  
  
#Specify the performance condition string to define the alert.  
$al.PerformanceCondition = "SQLServer:General Statistics|User Connections||>|3"  
  
#Create the alert on the SQL Agent.  
$al.Create()  
  
#Define an Operator object variable by supplying the Agent (parent JobServer object) and the name in the constructor.  
$op = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Operator -argumentlist $srv.JobServer, "Test_Operator"  
  
#Set the Net send address.  
$op.NetSendAddress = "Network1_PC"  
  
#Create the operator on the instance of SQL Agent.  
$op.Create()  
  
#Run the AddNotification method to specify the operator is notified when the alert is raised.  
$ns = [Microsoft.SqlServer.Management.SMO.Agent.NotifyMethods]::NetSend  
$al.AddNotification("Test_Operator", $ns)  
  
#Drop the alert and the operator  
$al.Drop()  
$op.Drop()  
```  
  
## <a name="allowing-user-access-to-subsystem-by-using-a-proxy-account-in-visual-basic"></a>Autorisation de l'accès utilisateur au sous-système à l'aide d'un compte proxy en Visual Basic  
 L'exemple de code suivant montre comment autoriser un utilisateur à accéder à un sous-système spécifié en utilisant la méthode <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount.AddSubSystem%2A> de l'objet <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount>.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBAgent2](SMO How to#SMO_VBAgent2)]  -->  
  
## <a name="allowing-user-access-to-subsystem-by-using-a-proxy-account-in-visual-c"></a>Autorisation de l'accès utilisateur au sous-système à l'aide d'un compte proxy en Visual C#  
 L'exemple de code suivant montre comment autoriser un utilisateur à accéder à un sous-système spécifié en utilisant la méthode <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount.AddSubSystem%2A> de l'objet <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount>.  
  
```  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
//Declare a JobServer object variable and reference the SQL Server Agent.   
JobServer js = default(JobServer);   
js = srv.JobServer;   
//Define a Credential object variable by supplying the parent server and name arguments in the constructor.   
Credential c = default(Credential);   
c = new Credential(srv, "Proxy_accnt");   
//Set the identity to a valid login represented by the vIdentity string variable.   
//The sub system will run under this login.   
c.Identity = vIdentity;   
//Create the credential on the instance of SQL Server.   
c.Create();   
//Define a ProxyAccount object variable by supplying the SQL Server Agent, the name, the credential, the description arguments in the constructor.   
ProxyAccount pa = default(ProxyAccount);   
pa = new ProxyAccount(js, "Test_proxy", "Proxy_accnt", true, "Proxy account for users to run job steps in command shell.");   
//Create the proxy account on the SQL Agent.   
pa.Create();   
//Add the login, represented by the vLogin string variable, to the proxy account.   
pa.AddLogin(vLogin);   
//Add the CmdExec subsytem to the proxy account.   
pa.AddSubSystem(AgentSubSystem.CmdExec);   
}   
//Now users logged on as vLogin can run CmdExec job steps with the specified credentials.   
```  
  
## <a name="see-also"></a>Voir aussi  
 [Agent SQL Server](../../../ssms/agent/sql-server-agent.md)   
 [Implémenter des travaux](../../../ssms/agent/implement-jobs.md)  
  
  
