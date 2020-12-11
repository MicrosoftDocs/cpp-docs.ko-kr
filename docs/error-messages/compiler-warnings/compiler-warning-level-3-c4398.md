---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4398'
title: 컴파일러 경고(수준 3) C4398
ms.date: 11/04/2016
f1_keywords:
- C4398
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
ms.openlocfilehash: ea88f81e44fe0520cd096e1904c49a306863496a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160430"
---
# <a name="compiler-warning-level-3-c4398"></a>컴파일러 경고(수준 3) C4398

> '*variable*': 여러 appdomain에서 프로세스별 전역 개체가 제대로 작동 하지 않을 수 있습니다. __declspec (appdomain) 사용 고려

## <a name="remarks"></a>설명

네이티브 형식에서 [__clrcall](../../cpp/clrcall.md) 호출 규칙을 사용 하는 가상 함수를 사용 하면 응용 프로그램 도메인 vtable 마다 생성 됩니다. 이러한 변수는 여러 응용 프로그램 도메인에서 사용 되는 경우 올바르게 수정 되지 않을 수 있습니다.

변수를 명시적으로 표시 하 여이 경고를 해결할 수 있습니다 `__declspec(appdomain)` . Visual studio 2017 이전의 Visual Studio 버전에서는 **/clr: pure** 를 사용 하 여 컴파일하여이 경고를 해결할 수 있습니다. 이렇게 하면 기본적으로 appdomain 당 전역 변수가 만들어집니다. **/Clr: pure** 컴파일러 옵션은 visual studio 2015에서는 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

자세한 내용은 [appdomain](../../cpp/appdomain.md) 및 [응용 프로그램 도메인 및 Visual C++](../../dotnet/application-domains-and-visual-cpp.md)을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C4398를 생성 합니다.

```cpp
// C4398.cpp
// compile with: /clr /W3 /c
struct S {
   virtual void f( System::String ^ );   // String^ parameter makes function __clrcall
};

S glob_s;   // C4398
__declspec(appdomain) S glob_s2;   // OK
```
