---
description: '자세한 정보: 컴파일러 오류 C2388'
title: 컴파일러 오류 C2388
ms.date: 11/04/2016
f1_keywords:
- C2388
helpviewer_keywords:
- C2388
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
ms.openlocfilehash: 63a2758b4e214b38c7d999bdc2a33d328709ea67
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123983"
---
# <a name="compiler-error-c2388"></a>컴파일러 오류 C2388

' symbol ': 기호는 __declspec (appdomain)와 \_ _declspec (process)를 사용 하 여 선언할 수 없습니다.

`appdomain`및 `process` **`__declspec`** 한정자는 동일한 기호에 사용할 수 없습니다. 변수에 대한 스토리지는 프로세스별 또는 애플리케이션 도메인별로 존재합니다.

자세한 내용은 [appdomain](../../cpp/appdomain.md) 및 [process](../../cpp/process.md)를 참조하세요.

다음 샘플에서는 C2388을 생성합니다.

```cpp
// C2388.cpp
// compile with: /clr /c
__declspec(process) __declspec(appdomain) int i;   // C2388
__declspec(appdomain) int i;   // OK
```
