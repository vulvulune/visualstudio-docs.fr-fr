---
title: Validation des points d’arrêt dans un Service de langage hérité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 025f5366938eb00114b035f0b7992d61433cc181
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62908150"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Validation des points d’arrêt dans un service de langage hérité
Un point d’arrêt indique que l’exécution du programme doit s’arrêter à un moment donné pendant qu’il est en cours d’exécution dans un débogueur. Un utilisateur peut placer un point d’arrêt sur n’importe quelle ligne dans le fichier source, dans la mesure où l’éditeur n’a aucune connaissance de ce qui constitue un emplacement valide pour un point d’arrêt. Lorsque le débogueur est lancé, tous les points d’arrêt marquées (appelés en attente de points d’arrêt) sont liés à l’emplacement approprié dans le programme en cours d’exécution. En même temps que les points d’arrêt sont validées pour garantir qu’ils servent à indiquer les emplacements de code valide. Par exemple, un point d’arrêt sur un commentaire n’est pas valide, car il n’existe aucun code à cet emplacement dans le code source. Le débogueur désactive les points d’arrêt non valides.

 Étant donné que le service de langage connaît le code source qui est affiché, il peut valider des points d’arrêt avant de lancer le débogueur. Vous pouvez remplacer le <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> méthode pour retourner une étendue en spécifiant un emplacement valide pour un point d’arrêt. L’emplacement du point d’arrêt est toujours validé lorsque le débogueur est lancé, mais l’utilisateur est informé des points d’arrêt non valides sans attendre que le débogueur charge.

## <a name="implementing-support-for-validating-breakpoints"></a>Implémentation de prise en charge pour la validation des points d’arrêt

- Le <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> la position du point d’arrêt est donnée à la méthode. Votre implémentation doit décider ou non l’emplacement est valide et indiquer ceci en retournant une étendue de texte qui identifie le code associé à la position de ligne du point d’arrêt.

- Retourner <xref:Microsoft.VisualStudio.VSConstants.S_OK> si l’emplacement est valide, ou <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> s’il n’est pas valide.

- Si le point d’arrêt est valide, l’étendue de texte est mis en surbrillance, ainsi que le point d’arrêt.

- Si le point d’arrêt n’est pas valide, un message d’erreur s’affiche dans la barre d’état.

### <a name="example"></a>Exemple
 Cet exemple illustre une implémentation de la <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> méthode qui appelle l’analyseur pour obtenir l’étendue du code (le cas échéant) à l’emplacement spécifié.

 Cet exemple suppose que vous avez ajouté un `GetCodeSpan` méthode à la <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe qui valide l’étendue de texte et le retourne `true` si elle est un emplacement de point d’arrêt valide.

```csharp
using Microsoft VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestLanguageService : LanguageService
    {
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,
                                                       int line,
                                                       int col,
                                                       TextSpan[] pCodeSpan)
        {
            int retval = VSConstants.S_FALSE;
            if (pCodeSpan != null)
            {
                // Initialize span to current line by default.
                pCodeSpan[0].iStartLine = line;
                pCodeSpan[0].iStartIndex = col;
                pCodeSpan[0].iEndLine = line;
                pCodeSpan[0].iEndIndex = col;
            }

            if (buffer != null)
            {
                IVsTextLines textLines = buffer as IVsTextLines;
                if (textLines != null)
                {
                    Source src = this.GetSource(textLines);
                    if (src != null)
                    {
                        TokenInfo tokenInfo = new TokenInfo();
                        string text = src.GetText();
                        ParseRequest req = CreateParseRequest(src,
                                                              line,
                                                              col,
                                                              tokenInfo,
                                                              text,
                                                              src.GetFilePath(),
                                                              ParseReason.CodeSpan,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        TextSpan span = new TextSpan();
                        if (sink.GetCodeSpan(out span))
                        {
                            pCodeSpan[0] = span;
                            retval = VSConstants.S_OK;
                        }
                    }
                }
            }
            return retval;
        }
    }
}
```

## <a name="see-also"></a>Voir aussi
- [Fonctionnalités du service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md)