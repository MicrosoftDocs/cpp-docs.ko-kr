---
title: 컴파일러 오류 C3533
ms.date: 11/04/2016
f1_keywords:
- C3533
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
ms.openlocfilehash: 4e3c773d0498a35c7b5d053268bff26f9943103b
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686771"
---
# <a name="compiler-error-c3533"></a>컴파일러 오류 C3533

' type ': 매개 변수에는 ' a u t o '를 포함 하는 형식을 사용할 수 없습니다.

**`auto`** 기본 [/zc: auto](../../build/reference/zc-auto-deduce-variable-type.md) 컴파일러 옵션이 적용 되는 경우에는 키워드를 사용 하 여 메서드 또는 템플릿 매개 변수를 선언할 수 없습니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. **`auto`** 매개 변수 선언에서 키워드를 제거 합니다.

## <a name="examples"></a>예제

다음 예제에서는 키워드를 사용 하 여 함수 매개 변수를 선언 **`auto`** 하 고 **/zc: auto**를 사용 하 여 컴파일되기 때문에 C3533를 생성 합니다.

```cpp
// C3533a.cpp
// Compile with /Zc:auto
void f(auto j) {} // C3533
```

다음 예제에서는 키워드를 사용 하 여 템플릿 매개 변수를 선언 **`auto`** 하 고 **/zc: auto**로 컴파일되기 때문에 c + + 14 모드에서 C3533를 생성 합니다. C + + 17에서는 형식이 추론 된 단일 비 형식 템플릿 매개 변수를 사용 하는 클래스 템플릿의 유효한 정의입니다.

```cpp
// C3533b.cpp
// Compile with /Zc:auto
template<auto T> class C {}; // C3533
```

## <a name="see-also"></a>참조

[auto 키워드](../../cpp/auto-keyword.md)<br/>
[/Zc: auto (변수 형식 추론)](../../build/reference/zc-auto-deduce-variable-type.md)
