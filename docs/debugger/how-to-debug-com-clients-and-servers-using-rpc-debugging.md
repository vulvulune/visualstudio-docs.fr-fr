---
title: Déboguer des clients COM et des serveurs à l’aide du débogage RPC | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- RPC (Remote Procedure Call), debugging COM clients and servers
- COM, debugging
- RPC (Remote Procedure Call)
- RPC (Remote Procedure Call), debugging
- COM clients, debugging
- COM servers, debugging
- out-of-process remote procedure call debugging
- remote debugging, RPC (Remote Procedure Call)
- in-process remote procedure call debugging
ms.assetid: 3e8526c8-43b5-4b87-8e0d-b22c24f0a3ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5c98405b424dd5402a903a236b1c5549a43616d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387518"
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>Procédure : Déboguer des clients et des serveurs COM à l’aide du débogage RPC
Vous pouvez utiliser le débogage RPC pour déboguer des applications client/serveur COM. Vous devez activer le débogage RPC pour l'utiliser. Lorsque le débogage RPC est activé, si vous effectuez un pas à pas détaillé dans l'appel serveur à partir du client, le débogueur est attaché au serveur, ce qui permet de déboguer son code. Une fois que le débogueur est attaché, vous pouvez utiliser toutes ses fonctionnalités avec les processus client et serveur.

### <a name="to-enable-rpc-debugging"></a>Pour activer le débogage RPC

1. Dans le menu **Outils**, cliquez sur **Options**.

2. Dans la boîte de dialogue **Options**, cliquez sur le dossier **Débogage**.

3. Cliquez sur la page **Natif**.

4. Cochez la case **Débogage RPC**.

    > [!NOTE]
    > Pour déboguer des appels RPC, vous devez posséder les privilèges Administrateur ou Utilisateur avec pouvoirs.

    > [!NOTE]
    > Le processus d'exécution pas à pas RPC sur un serveur distant qui exécute Microsoft Windows Vista fonctionne uniquement si un débogueur natif est attaché au serveur distant. Sinon, l'appel RPC échoue sans message d'erreur. Sinon, l'appel RPC s'effectue, mais le processus d'exécution pas à pas dans l'appel RPC ne fonctionne pas.

## <a name="see-also"></a>Voir aussi
- [Débogage de serveurs et de conteneurs COM](../debugger/com-server-and-container-debugging.md)
- [Débogage dans Visual Studio](../debugger/index.md)
- [Présentation du débogueur](../debugger/debugger-feature-tour.md)