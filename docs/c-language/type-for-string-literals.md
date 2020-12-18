---
description: '자세한 정보: 문자열 리터럴의 형식'
title: 문자열 리터럴의 형식
ms.date: 11/04/2016
helpviewer_keywords:
- string literals, type
- types [C], string literals
ms.assetid: f50a28af-20c1-4440-bdc6-564c86a309c8
ms.openlocfilehash: 9b752d79a1f33e43f24fb86902ba91b3d31777c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242823"
---
# <a name="type-for-string-literals"></a>문자열 리터럴의 형식

문자열 리터럴은 **`char`** 배열(즉, **char[ ]** ) 형식입니다. 와이드 문자 문자열은 **`wchar_t`** 배열(즉, **wchar_t[ ]** ) 형식입니다. 즉, 문자열은 **`char`** 형식의 요소가 포함된 배열입니다. 배열에 있는 요소의 수는 문자열의 문자 개수에 null 종결 문자에 해당하는 1을 더한 값입니다.

## <a name="see-also"></a>참조

[C 문자열 리터럴](../c-language/c-string-literals.md)
