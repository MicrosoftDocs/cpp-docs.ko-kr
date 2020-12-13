---
description: '자세한 정보: 컴파일러 오류 C3665'
title: 컴파일러 오류 C3665
ms.date: 11/04/2016
f1_keywords:
- C3665
helpviewer_keywords:
- C3665
ms.assetid: 893bb47e-8de1-43aa-af7d-fa47ad149ee9
ms.openlocfilehash: 3a4585361fa2ffab4835fafd47778a5c591bb001
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134279"
---
# <a name="compiler-error-c3665"></a>컴파일러 오류 C3665

' 소멸자 ': 재정의 지정자 ' keyword '는 소멸자/종료자에서 사용할 수 없습니다.

소멸자 또는 종료자에서 허용 되지 않는 키워드가 사용 되었습니다.

예를 들어 새 슬롯은 소멸자 또는 종료자에서 요청할 수 없습니다.  자세한 내용은 [명시적 재정의](../../extensions/explicit-overrides-cpp-component-extensions.md) 및 [소멸자 및 종료자](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)를 참조 하세요.

다음 샘플에서는 C3665를 생성 합니다.

```cpp
// C3665.cpp
// compile with: /clr
public ref struct R {
   virtual ~R() { }
   virtual void a() { }
};

public ref struct S : R {
   virtual ~S() new {}   // C3665
   virtual void a() new {}   // OK
};
```
