---
description: '자세한 정보: 컴파일러 오류 C2492'
title: 컴파일러 오류 C2492
ms.date: 11/04/2016
f1_keywords:
- C2492
helpviewer_keywords:
- C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
ms.openlocfilehash: ef31b2136a2cfc0422832899dba14ffb3108d965
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283678"
---
# <a name="compiler-error-c2492"></a>컴파일러 오류 C2492

'*variable*': 스레드 저장 기간이 있는 데이터에는 dll 인터페이스를 사용할 수 없습니다.

변수는 [thread](../../cpp/thread.md) 특성과 DLL 인터페이스를 사용 하 여 선언 됩니다. 변수의 주소는 `thread` 런타임까지 알려지지 않으므로 DLL 가져오기 또는 내보내기에 연결할 수 없습니다.

다음 샘플에서는 C2492를 생성 합니다.

```cpp
// C2492.cpp
// compile with: /c
class C {
public:
   char   ch;
};

__declspec(dllexport) __declspec(thread) C c_1;   // C2492
__declspec(thread) C c_1;   // OK
```
