---
title: 'Leçon 1 : Créer le projet Visual Studio du schéma RDL | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f420509c-51aa-4170-8c25-64c2954f4bb9
caps.latest.revision: 17
author: craigg-msft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fc69b4bbcc40fa669ca9cf5f889944cb302e4b14
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37319809"
---
# <a name="lesson-1-create-the-rdl-schema-visual-studio-project"></a>Leçon 1 : Création du projet Visual Studio du schéma RDL
  Dans ce didacticiel, vous allez créer une application console simple. Ce didacticiel suppose que vous développez dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].  
  
> [!NOTE]  
>  Lorsque vous accédez au service Web Report Server qui s'exécute sur [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services, vous devez ajouter "_SQLExpress" au chemin d'accès "ReportServer". Exemple :  
>   
>  `http://myserver/reportserver_sqlexpress/reportservice2010.asmx"`  
  
### <a name="to-create-the-web-service-proxy"></a>Pour créer le proxy de service Web  
  
1.  Dans le menu **Démarrer** , sélectionnez **Tous les programmes**, Microsoft Visual Studio, **Visual Studio Tools**, puis **Invite de commandes de Visual Studio 2010**.  
  
2.  Dans la fenêtre d'invite de commandes, exécutez la commande suivante si vous utilisez C# :  
  
    ```  
    wsdl /language:CS /n:"ReportService2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     Si vous utilisez Visual Basic, exécutez la commande suivante :  
  
    ```  
    wsdl /language:VB /n:"ReportService2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     Cette commande génère un fichier .cs ou .vb. Vous ajouterez ce fichier à votre application.  
  
### <a name="to-create-a-console-application"></a>Pour créer une application console  
  
1.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet** pour ouvrir la boîte de dialogue **Nouveau projet** .  
  
2.  Dans le volet gauche, sous **Modèles installés**, cliquez sur le nœud **Visual Basic** ou **Visual C#** , puis sélectionnez une catégorie de types de projets dans la liste développée.  
  
3.  Choisissez le type de projet **Application console** .  
  
4.  Dans la zone **Nom** , tapez le nom de votre projet. Tapez le nom `SampleRDLSchema`.  
  
5.  Dans la zone **Emplacement** , entrez le chemin d'accès de l'emplacement où vous voulez enregistrer le projet, ou cliquez sur **Parcourir** pour rechercher le dossier.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)] Une vue réduite de votre projet apparaît dans l’Explorateur de solutions.  
  
7.  Dans le menu **Projet** , cliquez sur **Ajouter un élément existant**.  
  
8.  Naviguez jusqu'à l'emplacement où vous avez généré le fichier .cs ou .vb, sélectionnez le fichier, puis cliquez sur **Ajouter**.  
  
     Vous devrez également ajouter une référence à l'espace de noms <xref:System.Web.Services> pour que votre référence Web fonctionne.  
  
9. Dans le menu Projet, cliquez sur **Ajouter une référence**.  
  
     Dans la boîte de dialogue **Ajouter une référence** , dans l'onglet **.NET** , sélectionnez **System.Web.Services**, puis cliquez sur **OK**.  
  
     Pour plus d’informations sur la connexion au service Web Report Server, consultez [création d’Applications à l’aide du Service Web et le .NET Framework](../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md).  
  
10. Dans l'Explorateur de solutions, développez le nœud du projet. Vous verrez un fichier de code avec le nom par défaut du fichier Program.cs (Module1.vb pour [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) a été ajouté à votre projet.  
  
11. Ouvrez le fichier Program.cs (Module1.vb pour [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) et remplacez le code par le suivant :  
  
     Le code suivant fournit les stubs de méthode que nous utiliserons pour implémenter les fonctionnalités de chargement, de mise à jour et d'enregistrement.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.IO;  
    using System.Text;  
    using System.Xml;  
    using System.Xml.Serialization;  
    using ReportService2010;  
  
    namespace SampleRDLSchema  
    {  
        class ReportUpdater  
        {  
            ReportingService2010 _reportService;  
  
            static void Main(string[] args)  
            {  
                ReportUpdater reportUpdater = new ReportUpdater();  
                reportUpdater.UpdateReport();  
            }  
  
            private void UpdateReport()  
            {  
                try  
                {  
                    // Set up the Report Service connection  
                    _reportService = new ReportingService2010();  
                    _reportService.Credentials =  
                        System.Net.CredentialCache.DefaultCredentials;  
                    _reportService.Url =  
                       "http://<Server Name>/reportserver/" +  
                                       "reportservice2010.asmx";  
  
                    // Call the methods to update a report definition  
                    LoadReportDefinition();  
                    UpdateReportDefinition();  
                    PublishReportDefinition();  
                }  
                catch (Exception ex)  
                {  
                    System.Console.WriteLine(ex.Message);  
                }  
            }  
  
            private void LoadReportDefinition()  
            {  
                //Lesson 3: Load a report definition from the report   
                //          catalog  
            }  
  
            private void UpdateReportDefinition()  
            {  
                //Lesson 4: Update the report definition using the    
                //          classes generated from the RDL Schema  
            }  
  
            private void PublishReportDefinition()  
            {  
                //Lesson 5: Publish the updated report definition back   
                //          to the report catalog  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.IO  
    Imports System.Text  
    Imports System.Xml  
    Imports System.Xml.Serialization  
    Imports ReportService2010  
  
    Namespace SampleRDLSchema  
  
        Module ReportUpdater  
  
            Private m_reportService As ReportingService2010  
  
            Public Sub Main(ByVal args As String())  
  
                Try  
                    'Set up the Report Service connection  
                    m_reportService = New ReportingService2010  
                    m_reportService.Credentials = _  
                        System.Net.CredentialCache.DefaultCredentials  
                    m_reportService.Url = _  
                        "http:// <Server Name>/reportserver/" & _  
                               "reportservice2010.asmx"  
  
                    'Call the methods to update a report definition  
                    LoadReportDefinition()  
                    UpdateReportDefinition()  
                    PublishReportDefinition()  
                Catch ex As Exception  
                    System.Console.WriteLine(ex.Message)  
                End Try  
  
            End Sub  
  
            Private Sub LoadReportDefinition()  
                'Lesson 3: Load a report definition from the report   
                '          catalog  
            End Sub  
  
            Private Sub UpdateReportDefinition()  
                'Lesson 4: Update the report definition using the   
                '          classes generated from the RDL Schema  
            End Sub  
  
            Private Sub PublishReportDefinition()  
                'Lesson 5: Publish the updated report definition back   
                '          to the report catalog  
            End Sub  
  
        End Module  
  
    End Namespace   
    ```  
  
## <a name="next-lesson"></a>Leçon suivante  
 Dans la prochaine leçon, vous allez utiliser l'outil de définition de schéma XML (Xsd.exe) pour générer des classes à partir du schéma RDL et les inclure dans votre projet. Consultez [leçon 2 : générer des Classes à partir du schéma RDL à l’aide de l’outil xsd](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md).  
  
## <a name="see-also"></a>Voir aussi  
 [La mise à jour des rapports à l’aide des Classes générées à partir du schéma RDL &#40;didacticiel SSRS&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [RDL (Report Definition Language) &#40;SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
