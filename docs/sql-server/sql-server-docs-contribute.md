---
title: Guide pratique pour contribuer à la documentation SQL Server | Microsoft Docs
ms.date: 08/13/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || >= sql-server-linux-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 57b35b9edbfb257d327f310d526729b7a60215e2
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42773942"
---
# <a name="how-to-contribute-to-sql-server-documentation"></a>Guide pratique pour contribuer à la documentation SQL Server

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md.md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Tout le monde peut apporter sa contribution à la documentation SQL Server. C’est-à-dire corriger des fautes de frappe, suggérer de meilleures explications et améliorer la précision technique. Cet article explique comment commencer à contribuer à du contenu et comment fonctionne la procédure.

Il existe deux flux de travail principaux que vous pouvez utiliser pour apporter votre contribution :

|||
|---|---|
| [Modifier dans votre navigateur](#githubui) | Recommandé pour les modifications mineures et rapides d’un article. |
| [Modifier localement avec des outils](#tools) | Recommandé pour les modifications plus complexes, les modifications impliquant plusieurs articles et les contributions fréquentes à docs.microsoft.com. |

## <a id="githubui"></a> Modifier dans votre navigateur

Vous pouvez apporter des modifications de base au contenu SQL Server dans votre navigateur, puis les envoyer à Microsoft. Le processus complet est décrit dans l’article, [Vue d’ensemble du guide de contributeur Microsoft Docs](https://docs.microsoft.com/contribute/#quick-edits-to-existing-documents). La vidéo suivante montre le processus de bout en bout pour soumettre des changements dans votre navigateur :

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE23pxh]

> [!TIP]
> Notez que l’emplacement du bouton **Modifier** est légèrement différent de celui montré dans la vidéo, mais le processus est le même.
>
> ![Bouton Modifier](./media/sql-server-docs-contribute/edit-sql-server-docs.png)

## <a id="tools"></a> Modifier localement avec des outils

Une autre option de modification consiste à dupliquer le dépôt **sql-docs** ou **azure-docs**, puis à le cloner localement sur votre ordinateur. Vous pouvez ensuite utiliser un éditeur Markdown et un client Git pour soumettre les modifications. Ce flux de travail est approprié pour les modifications plus complexes ou qui impliquent plusieurs fichiers. Il est également adapté pour les contributeurs réguliers de docs.microsoft.com.

Pour apporter votre contribution à l’aide de cette méthode, consultez les articles suivants :

- [Créer un compte GitHub](https://docs.microsoft.com/contribute/get-started-setup-github)
- [Installer des outils de création de contenu](https://docs.microsoft.com/contribute/get-started-setup-tools)
- [Configurer localement un dépôt Git](https://docs.microsoft.com/contribute/get-started-setup-local)
- [Apporter sa contribution à l’aide d’outils](https://docs.microsoft.com/contribute/how-to-write-workflows-major)

Si vous envoyez une demande de tirage avec d’importants changements à apporter à la documentation, un commentaire s’affiche dans GitHub vous demandant d’envoyer un **contrat de licence de contribution** (CLA, Contribution License Agreement) en ligne. Pour que votre demande de tirage soit acceptée, vous devez au préalable compléter le formulaire en ligne.

## <a name="recognition"></a>Reconnaissance

Si vos changements sont acceptés, vous êtes reconnu comme contributeur en haut de l’article.

![Reconnaissance de la contribution au contenu](./media/sql-server-docs-contribute/contribution-recognition.png)

## <a name="sql-docs-overview"></a>Vue d’ensemble de sql-docs

Cette section fournit des conseils supplémentaires sur l’utilisation du dépôt **sql-docs**.

> [!IMPORTANT]
> Les informations de cette section sont spécifiques à **sql-docs**. Si vous modifiez un article SQL dans la documentation Azure, consultez [le fichier Lisez-moi du dépôt azure-docs sur GitHub](https://github.com/MicrosoftDocs/azure-docs/blob/master/README.md).

Le dépôt [sql-docs](https://github.com/MicrosoftDocs/sql-docs) utilise plusieurs dossiers standard pour organiser le contenu.

| Dossier | Description |
|---|---|
| [docs](https://github.com/MicrosoftDocs/sql-docs/tree/live/docs) | Contient tout le contenu SQL Server publié. Les sous-dossiers organisent de manière logique les différents domaines du contenu. |
| [docs/includes](https://github.com/MicrosoftDocs/sql-docs/tree/live/docs/includes) | Contient les fichiers include. Ces fichiers sont des blocs de contenu qui peuvent être inclus dans une ou plusieurs autres rubriques. |
| **./media** | Chaque dossier peut avoir un sous-dossier **media** pour les images des articles. Le dossier **media** comprend à son tour des sous-dossiers portant le même nom que les rubriques dans lesquelles l’image apparaît. Les images doivent être des fichiers .png avec toutes les lettres en minuscules et sans espaces. |
| **TOC.MD** | Fichier de table des matières. Chaque sous-dossier a la possibilité d’utiliser un fichier TOC.MD. |

#### <a name="applies-to-includes"></a>Fichiers include Applies-to

Chaque article SQL Server contient un fichier include **applies-to** après le titre. Cela indique les domaines ou les versions de SQL Server auxquels l’article s’applique.

Prenons l’exemple Markdown suivant qui extrait le fichier include **appliesto-ss-asdb-asdw-pdw-md.md**.

```Markdown
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
```

Cette opération ajoute le texte suivant en haut de l’article :

![Texte « S’applique à »](./media/sql-server-docs-contribute/applies-to.png)

Pour trouver le fichier include applies-to approprié à votre article, utilisez les conseils suivants :

- Pour une liste de fichiers include couramment utilisés, consultez [Version SQL Server et fichiers include applies-to](applies-to-includes.md).
- Consultez d’autres articles qui traitent de la même fonction ou d’une tâche associée. Si vous modifiez cet article, vous pouvez copier le texte Markdown du lien du fichier include applies-to (vous pouvez annuler la modification sans la soumettre).
- Recherchez les fichiers contenant le texte « applies-to » dans le répertoire [docs/includes](https://github.com/MicrosoftDocs/sql-docs/tree/live/docs/includes). Vous pouvez utiliser le bouton **Find** (Trouver) dans GitHub pour appliquer rapidement un filtre. Cliquez sur le fichier pour voir comment il est restitué.
- Faites attention à la convention de nommage. Si le nom contient des x, ce sont généralement des espaces réservés indiquant l’absence de prise en charge d’un service. Par exemple, **appliesto-xx-xxxx-asdw-xxx-md.md** indique la prise en charge d’Azure SQL Data Warehouse uniquement, car seul **asdw** est indiqué clairement, tandis que les autres champs contiennent des x.
- Certains fichiers include spécifient un numéro de version, comme **tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md**. Utilisez ces fichiers include seulement si vous savez que la fonctionnalité a été introduite avec une version spécifique de SQL Server.

## <a name="contributor-resources"></a>Ressources pour les contributeurs

- [Guide des contributeurs pour docs.microsoft.com](https://docs.microsoft.com/en-us/contribute/)
- [Guide de style de Microsoft](https://docs.microsoft.com/en-us/teamblog/style-guide)
- [Principes de base de Markdown](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)

> [!TIP]
> Si vous avez des commentaires sur le produit plutôt que sur la documentation, [fournissez vos commentaires sur le produit SQL Server ici](https://feedback.azure.com/forums/908035-sql-server).

## <a name="next-steps"></a>Étapes suivantes

Explorez le [dépôt sql-docs](https://github.com/MicrosoftDocs/sql-docs) sur GitHub.

Recherchez un article, envoyez une modification et aidez la Communauté SQL Server. 

Merci !