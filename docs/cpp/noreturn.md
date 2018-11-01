---
title: noreturn
ms.date: 11/04/2016
f1_keywords:
- noreturn_cpp
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
ms.openlocfilehash: 1d78e8f5116eabf9073205b938156197bf1001a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611863"
---
# <a name="noreturn"></a>noreturn

## <a name="microsoft-specific"></a>Microsoft 전용

이렇게 **__declspec** 특성 컴파일러가 함수가 반환 하지 않습니다. 결과적으로 컴파일러 한다는 사실을 알고 있으면 호출 하는 코드를 **__declspec (noreturn)** 함수에 연결할 수 없습니다.

컴파일러가 값을 반환하지 않는 제어 경로를 가진 함수를 발견할 경우 경고(C4715) 또는 오류 메시지(C2202)가 생성됩니다. 반환 하지 않는 함수로 인해 제어 경로 연결할 수 없습니다, 하는 경우 사용할 수 있습니다 **__declspec (noreturn)** 이 경고 또는 오류를 방지할 수 있습니다.

> [!NOTE]
>  추가 **__declspec (noreturn)** 반환 해야 하는 함수에 정의 되지 않은 동작이 발생할 수 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 합니다 **다른** 절에 return 문이 없습니다.  선언 `fatal` 으로 **__declspec (noreturn)** 오류 또는 경고 메시지를 방지 합니다.

```cpp
// noreturn2.cpp
__declspec(noreturn) extern void fatal () {}

int main() {
   if(1)
     return 1;
   else if(0)
     return 0;
   else
     fatal();
}
```

## <a name="see-also"></a>참고자료

[__declspec](../cpp/declspec.md)<br/>
[키워드](../cpp/keywords-cpp.md)