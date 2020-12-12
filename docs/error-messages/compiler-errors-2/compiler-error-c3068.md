---
description: '자세한 정보: 컴파일러 오류 C3068'
title: 컴파일러 오류 C3068
ms.date: 11/04/2016
f1_keywords:
- C3068
helpviewer_keywords:
- C3068
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
ms.openlocfilehash: a73c525f017a3d571600e31d4c9ea875d0b25662
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281675"
---
# <a name="compiler-error-c3068"></a>컴파일러 오류 C3068

' function ': ' naked ' 함수는 c + + 예외가 발생 했을 때 해제가 필요한 개체를 포함할 수 없습니다.

컴파일러는 함수에서 임시 개체가 생성 되었고,[/ehsc](../../build/reference/eh-exception-handling-model.md)(c + + 예외 처리)가 지정 되었기 때문에 예외를 throw 한 [naked](../../cpp/naked-cpp.md) 함수에서 스택 해제를 수행할 수 없습니다.

이 오류를 해결 하려면 다음 중 하나 이상을 수행 합니다.

- /Ehsc로 컴파일하지 않음

- 함수를로 표시 하지 마십시오 `naked` .

- 함수에서 임시 개체를 만들지 마십시오.

함수가 스택에 임시 개체를 만드는 경우, 함수가 예외를 throw 하 고 c + + 예외 처리를 사용 하는 경우 예외가 throw 되 면 컴파일러는 스택을 정리 합니다.

예외가 throw 되 면 프롤로그 및 에필로그 라고 하 고 naked 함수에 없는 컴파일러 생성 코드는 함수에 대해 실행 됩니다.

## <a name="example"></a>예제

다음 샘플에서는 C3068를 생성 합니다.

```cpp
// C3068.cpp
// compile with: /EHsc
// processor: x86
class A {
public:
   A(){}
   ~A(){}
};

void b(A){}

__declspec(naked) void c() {
   b(A());   // C3068
};
```
