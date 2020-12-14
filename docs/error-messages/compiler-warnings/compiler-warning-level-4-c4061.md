---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4061'
title: 컴파일러 경고 (수준 4) C4061
ms.date: 04/05/2019
f1_keywords:
- C4061
helpviewer_keywords:
- C4061
ms.assetid: a99cf88e-7941-4519-8b1b-f6889d914b2f
ms.openlocfilehash: 9e76fd864e57e6d84ed28b1646e8950186945d11
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262063"
---
# <a name="compiler-warning-level-4-c4061"></a>컴파일러 경고 (수준 4) C4061

> '*enumeration*' 열거형의 switch에 있는 '*identifier*' 열거자는 case 레이블에 의해 명시적으로 처리 되지 않습니다.

지정 된 열거자 *식별자* 에 사례가 있는 문에 연결 된 처리기가 없습니다 **`switch`** **`default`** . 누락 된 케이스는 감독 일 수도 있고 문제가 아닐 수도 있습니다. 열거자가 기본 사례로 처리 되는지 여부에 따라 달라질 수 있습니다. 사례가 없는 문에서 사용 하지 않는 열거자에 대 한 관련 경고는 **`switch`** **`default`** [C4062](compiler-warning-level-4-c4062.md)을 참조 하세요.

기본적으로 이 경고는 해제되어 있습니다. 기본적으로 해제 되어 있는 경고를 사용 하도록 설정 하는 방법에 대 한 자세한 내용은 [기본적으로 해제 되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C4061를 생성 합니다. 누락 된 열거자에 대 한 사례를 추가 하 여 수정 합니다.

```cpp
// C4061.cpp
// compile with: /W4
#pragma warning(default : 4061)

enum E { a, b, c };
void func ( E e )
{
   switch(e)
   {
      case a:
      case b:
      default:
         break;
   }   // C4061 c' not handled
}

int main()
{
}
```

## <a name="see-also"></a>참고 항목

[컴파일러 경고 (수준 4) C4062](compiler-warning-level-4-c4062.md)
