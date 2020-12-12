---
description: '자세한 정보: 컴파일러 오류 C2129'
title: 컴파일러 오류 C2129
ms.date: 11/04/2016
f1_keywords:
- C2129
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
ms.openlocfilehash: 5efb19aa3f4edd14dd6cfab93c3880745b08e59d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323157"
---
# <a name="compiler-error-c2129"></a>컴파일러 오류 C2129

' function ' 정적 함수가 선언 되었지만 정의 되지 않았습니다.

정의 되지 않은 함수에 대해 전방 참조가 생성 됩니다 **`static`** .

**`static`** 함수는 파일 범위 내에서 정의 되어야 합니다. 함수가 다른 파일에 정의 되어 있는 경우에는 선언 해야 **`extern`** 합니다.
