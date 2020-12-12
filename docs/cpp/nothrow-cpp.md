---
description: '자세히 알아보기: nothrow (c + +)'
title: nothrow (C++)
ms.date: 01/03/2018
f1_keywords:
- nothrow_cpp
helpviewer_keywords:
- __declspec keyword [C++], nothrow
- nothrow __declspec keyword
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
ms.openlocfilehash: 7e438541221fe097aefb2e52d190e223fa1cf2fc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146252"
---
# <a name="nothrow-c"></a>nothrow (C++)

**Microsoft 전용**

**`__declspec`** 함수 선언에 사용할 수 있는 확장 특성입니다.

## <a name="syntax"></a>Syntax

> *반환 형식* __declspec (nothrow) [*호출 규칙*] *함수 이름* ([*인수 목록*])

## <a name="remarks"></a>설명

모든 새 코드는 대신 [noexcept](noexcept-cpp.md) 연산자를 사용 하는 것이 좋습니다 `__declspec(nothrow)` .

이 특성은 컴파일러에게 선언한 함수와 이 함수가 요청한 함수들이 예외를 throw하지 않도록 명령합니다. 그러나 지시문을 적용 하지는 않습니다. 즉, std: [: terminate](../standard-library/exception-functions.md#terminate) 는 **`noexcept`** 또는 **std: c + + 17** 모드 (Visual Studio 2017 버전 15.5 이상)에서 호출 되지 `throw()` 않습니다.

이제 기본값인, 동기 예외 처리 모델을 이용하여 컴파일러는 해제할 수 있는 특정 개체의 수명 추적 메커니즘을 제거할 수 있으며, 코드 크기를 크게 줄일 수 있습니다. 다음 전처리기 지시문이 지정 된 경우 아래의 세 함수 선언은 **/std: c + + 14** 모드에서 동일 합니다.

```cpp
#define WINAPI __declspec(nothrow) __stdcall

void WINAPI f1();
void __declspec(nothrow) __stdcall f2();
void __stdcall f3() throw();
```

**/Std: c + + 17** 모드에서 `throw()` 는 `__declspec(nothrow)` `std::terminate` 함수에서 예외가 throw 되는 경우가 호출 되기 때문에를 사용 하는 다른 다른와는 다릅니다.

선언에는 `void __stdcall f3() throw();` c + + 표준에 정의 된 구문이 사용 됩니다. C + + 17에서 `throw()` 키워드는 사용 되지 않습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[__declspec](../cpp/declspec.md)<br/>
[noexcept](noexcept-cpp.md)<br/>
[키워드](../cpp/keywords-cpp.md)
