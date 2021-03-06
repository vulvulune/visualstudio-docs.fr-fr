---
title: Créer un projet de test unitaire
ms.date: 01/29/2019
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: ca83689628f02a8c7a2e0166b390d5b277086c1d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965529"
---
# <a name="create-a-unit-test-project"></a>Créer un projet de test unitaire

Les tests unitaires reflètent souvent la structure du code testé. Par exemple, un projet de test unitaire est créé pour chaque projet de code du produit. Le projet de test peut se trouver dans la même solution que le code de production, ou dans une solution distincte. Vous pouvez avoir plusieurs projets de test unitaire dans une solution.

> [!NOTE]
> L’emplacement des tests unitaires du code natif et la structure du projet de test peuvent être différents de la structure décrite dans cet article. Pour plus d’informations, consultez [Écriture de tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>Pour créer un projet de test unitaire

1. Dans le menu **Fichier**, choisissez **Nouveau** > **Projet** ou appuyez sur **Ctrl**+**Maj**+**N**.

::: moniker range="vs-2017"

2. Dans la boîte de dialogue **Nouveau projet**, développez le nœud **Installé**, choisissez le langage que vous voulez utiliser pour votre projet de test, puis sélectionnez **Test**.

3. Pour utiliser l’une des infrastructures de tests unitaires Microsoft, choisissez **Projet de test unitaire** dans la liste des modèles de projet. Sinon, choisissez le modèle de projet de l’infrastructure de tests unitaires que vous souhaitez utiliser. Nommez le projet, puis sélectionnez **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

2. Dans la page **Créer un projet**, tapez **test unitaire** dans la zone de recherche. Sélectionnez le modèle de projet **Projet de test unitaire (.NET Framework)**, puis cliquez sur **Suivant**.

3. Dans la page **Configurer votre nouveau projet**, entrez un nom pour le projet, puis cliquez sur **Créer**.

::: moniker-end

4. Dans votre projet de test unitaire, ajoutez une référence au code testé. Pour ajouter une référence à un projet de code dans la même solution :

   1. Sélectionnez le projet de test dans **l’Explorateur de solutions**.

   2. Dans le menu **Projet** , choisissez **Ajouter une référence**.

   3. Dans **Gestionnaire de références**, sélectionnez le nœud **Solution** sous **Projets**. Sélectionnez le projet de code que vous voulez tester, puis sélectionnez **OK**.

   Si le code que vous voulez tester se trouve à un autre emplacement, consultez [Gestion des références dans un projet](../ide/managing-references-in-a-project.md) pour plus d’informations sur l’ajout d’une référence.

## <a name="next-steps"></a>Étapes suivantes

Consultez l’une des sections suivantes :

**Écriture de tests unitaires**

- [Tests unitaires sur votre code](../test/unit-test-your-code.md)

- [Écriture de tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md)

- [Utiliser le framework MSTest dans les tests unitaires](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Exécution de tests unitaires**

- [Exécuter des tests unitaires avec l’Explorateur de tests](../test/run-unit-tests-with-test-explorer.md)