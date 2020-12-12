---
description: '자세한 정보: 컴파일러 경고 C4368'
title: 컴파일러 경고 C4368
ms.date: 11/04/2016
f1_keywords:
- C4368
helpviewer_keywords:
- C4368
ms.assetid: cb85bcee-fd3d-4aa5-b626-2324f07a4f1b
ms.openlocfilehash: 106d8b0bb0dc70f03017892e8597c0cf059016cd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180788"
---
# <a name="compiler-warning-c4368"></a>컴파일러 경고 C4368

' member '를 관리 되는 ' type '의 멤버로 정의할 수 없습니다. 혼합 형식은 지원 되지 않습니다.

네이티브 데이터 멤버를 CLR 형식에 포함할 수 없습니다.

하지만 네이티브 형식에 대한 포인터를 선언하고, 관리 클래스의 생성자 및 소멸자와 종료자에서 해당 수명을 제어할 수 있습니다. 자세한 내용은 [소멸자 및 종료자](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)를 참조 하세요.

이 경고는 항상 오류로 실행 됩니다. C4368를 사용 하지 않도록 설정 하려면 [warning](../../preprocessor/warning.md) pragma를 사용 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C4368를 생성 합니다.

```cpp
// C4368.cpp
// compile with: /clr /c
struct N {};
ref struct O {};
ref struct R {
    R() : m_p( new N ) {}
    ~R() { delete m_p; }

   property N prop;   // C4368
   int i[10];   // C4368

   property O ^ prop2;   // OK
   N * m_p;   // OK
};
```
