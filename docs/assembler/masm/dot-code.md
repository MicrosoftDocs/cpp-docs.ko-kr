---
title: .CODE
ms.date: 08/30/2018
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: a5b6608ca71a2b406c54a06cd44ac2865211a8ac
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398573"
---
# <a name="code"></a>.CODE

When used with [.MODEL](../../assembler/masm/dot-model.md), indicates the start of a code segment.

## <a name="syntax"></a>구문

> **.CODE** ⟦*name*⟧

### <a name="parameters"></a>매개 변수

*name*\
Optional parameter that specifies the name of the code segment. The default name is **_TEXT** for tiny, small, compact, and flat [models](../../assembler/masm/dot-model.md). The default name is *modulename*_TEXT for other models.

## <a name="see-also"></a>참조

[Directives Reference](../../assembler/masm/directives-reference.md)\
[.DATA](../../assembler/masm/dot-data.md)
