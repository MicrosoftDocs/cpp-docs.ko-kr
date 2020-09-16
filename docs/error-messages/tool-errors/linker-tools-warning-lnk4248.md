---
title: 링커 도구 경고 LNK4248
ms.date: 11/04/2016
f1_keywords:
- LNK4248
helpviewer_keywords:
- LNK4248
ms.assetid: e40523ff-e3cb-4ba6-ab79-23f0f339f6cf
ms.openlocfilehash: 81f3c2abc41673e6e4c9e3f59ff1dd515e1cf365
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685427"
---
# <a name="linker-tools-warning-lnk4248"></a>링커 도구 경고 LNK4248

' type ';에 대 한 확인 되지 않은 typeref 토큰 (토큰) 이미지가 실행 되지 않을 수 있습니다.

형식에 MSIL 메타 데이터에 대 한 정의가 없습니다.

Msil 모듈에서 형식이 참조 되 고 msil 모듈이 형식에 대 한 정의가 있는 네이티브 모듈과 연결 된 msil **/clr**모듈에 형식에 대 한 전방 선언만 있는 경우 LNK4248이 발생할 수 있습니다.

이 경우 링커에서는 MSIL 메타 데이터에 네이티브 형식 정의를 제공 하 고이를 통해 올바른 동작을 제공할 수 있습니다.

그러나 전방 형식 선언이 CLR 형식이 면 링커의 네이티브 형식 정의가 올바르지 않을 수 있습니다.

자세한 내용은 [/clr (공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md)를 참조 하세요.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. MSIL 모듈의 형식 정의를 제공 합니다.

## <a name="examples"></a>예제

다음 샘플에서는 LNK4248를 생성 합니다. 확인할 구조체 A를 정의 합니다.

```cpp
// LNK4248.cpp
// compile with: /clr /W1
// LNK4248 expected
struct A;
void Test(A*){}

int main() {
   Test(0);
}
```

다음 샘플에는 형식의 전방 정의가 있습니다.

```cpp
// LNK4248_2.cpp
// compile with: /clr /c
class A;   // provide a definition for A here to resolve
A * newA();
int valueA(A * a);

int main() {
   A * a = newA();
   return valueA(a);
}
```

다음 샘플에서는 LNK4248를 생성 합니다.

```cpp
// LNK4248_3.cpp
// compile with: /c
// post-build command: link LNK4248_2.obj LNK4248_3.obj
class A {
public:
   int b;
};

A* newA() {
   return new A;
}

int valueA(A * a) {
   return (int)a;
}
```
