---
title: 컴파일러 경고 (수준 4) C4800
ms.date: 03/14/2019
f1_keywords:
- C4800
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
ms.openlocfilehash: bcc98b9bb24f77e39a31332b8fbe2f7dcc5a7638
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924616"
---
# <a name="compiler-warning-level-4-c4800"></a>컴파일러 경고 (수준 4) C4800

::: moniker range=">= msvc-160"
Visual Studio 2019 이상:
> ' *Type* '에서 bool로의 암시적 변환입니다. 가능한 정보 손실
::: moniker-end

C4800는 Visual Studio 2015 이전 버전의 수준 3 경고입니다.
> ' *type* ': 값을 bool ' true ' 또는 ' f a l s e '로 강제 적용 합니다 (성능 경고).

이 경고는 값이 암시적으로 형식으로 변환 될 때 생성 됩니다 **`bool`** . 일반적으로이 메시지는 변수에 변수와 **`int`** **`bool`** **`int`** 만 포함 되어 **`true`** **`false`** 있고 형식으로 다시 선언 될 수 있는 변수에 변수를 할당 하는 경우에 발생 합니다 **`bool`** . 형식을 사용 하도록 식을 다시 작성할 수 없는 경우 식에 ""를 추가 하 여 식 **`bool`** 형식을 지정할 수 있습니다 `!=0` **`bool`** . 식을 형식으로 캐스팅 하면 **`bool`** 경고가 발생 하지 않습니다.

::: moniker range=">= msvc-150"
이 경고는 Visual Studio 2017에서 내보내지 않습니다.
::: moniker-end

::: moniker range=">= msvc-160"
이 경고는 Visual Studio 2019부터 기본적으로 해제 되어 있습니다. __/W__*n*__4800__ 을 사용 하 여 C4800을 수준 *n* 경고로 설정 하거나 [/Wall](../../build/reference/compiler-option-warning-level.md) 를 사용 하 여 기본적으로 해제 되어 있는 모든 경고를 사용 하도록 설정 합니다. 자세한 내용은 [기본적으로 해제 되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md)를 참조 하세요.
::: moniker-end

## <a name="example"></a>예제

다음 샘플에서는 C4800를 생성 하 고 수정 하는 방법을 보여 줍니다.

```cpp
// C4800.cpp
// compile with: /W4 /w44800
int main() {
   int i = 0;

   // To fix, instead try:
   // bool i = 0;

   bool j = i;   // C4800
   j++;
}
```
