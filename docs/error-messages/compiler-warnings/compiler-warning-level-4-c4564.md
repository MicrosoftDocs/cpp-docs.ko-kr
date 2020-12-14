---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4564'
title: 컴파일러 경고(수준 4) C4564
ms.date: 11/04/2016
f1_keywords:
- C4564
helpviewer_keywords:
- C4564
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
ms.openlocfilehash: 112d1d20d34619d7a39d20c7fcd5f21584730cef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255173"
---
# <a name="compiler-warning-level-4-c4564"></a>컴파일러 경고(수준 4) C4564

' class ' 클래스의 ' method ' 메서드는 지원 되지 않는 기본 매개 변수 ' parameter '를 정의 합니다.

컴파일러가 기본값이 있는 하나 이상의 매개 변수가 있는 메서드를 검색 했습니다. 매개 변수의 기본값은 메서드가 호출 될 때 무시 됩니다. 이러한 매개 변수에 대 한 값을 명시적으로 지정 합니다. 이러한 매개 변수에 대 한 값을 명시적으로 지정 하지 않으면 c + + 컴파일러에서 오류를 생성 합니다.

메서드 인수에 대 한 기본 매개 변수를 허용 하는 다음 .dll을 Visual Basic 사용 하 여를 만들 수 있습니다.

```vb
' C4564.vb
' compile with: vbc /t:library C4564.vb
Public class TestClass
   Public Sub MyMethod (a as Integer, _
                        Optional c as Integer=1)
   End Sub
End class
```

Visual Basic로 만든 .dll을 사용 하는 다음 c + + 샘플

```cpp
// C4564.cpp
// compile with: /clr /W4 /WX
#using <C4564.dll>

int main() {
   TestClass ^ myx = gcnew TestClass();   // C4564
   myx->MyMethod(9);
   // try the following line instead, to avoid an error
   // myx->MyMethod(9, 1);
}
```
