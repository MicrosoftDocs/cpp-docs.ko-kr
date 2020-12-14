---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4062'
title: 컴파일러 경고(수준 4) C4062
ms.date: 04/05/2019
f1_keywords:
- C4062
helpviewer_keywords:
- C4062
ms.assetid: 36d1c6ae-c917-4b08-bf30-2eb49ee94169
ms.openlocfilehash: 3aee4286fb8d06d98617ea6fa71929768cbd23c0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262050"
---
# <a name="compiler-warning-level-4-c4062"></a>컴파일러 경고(수준 4) C4062

> '*enumeration*' 열거형의 switch에 있는 '*identifier*' 열거자가 처리 되지 않습니다.

열거자 *식별자* 는 문에 연결 된 `case` 처리기가 없으며 **`switch`** **`default`** catch 할 수 있는 레이블이 없습니다. 누락 된 케이스는 감독 일 수 있으며 코드에서 오류가 발생할 수 있습니다. 사례가 있는 문에서 사용 하지 않는 열거자에 대 한 관련 경고는 **`switch`** **`default`** [C4061](compiler-warning-level-4-c4061.md)를 참조 하세요.

기본적으로 이 경고는 해제되어 있습니다. 기본적으로 해제 되어 있는 경고를 사용 하도록 설정 하는 방법에 대 한 자세한 내용은 [기본적으로 해제 되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C4062를 생성 하 고 수정 하는 방법을 보여 줍니다.

```cpp
// C4062.cpp
// compile with: /EHsc /W4
#pragma warning(default : 4062)
enum E { a, b, c };
void func ( E e ) {
   switch(e) {
      case a:
      case b:
   // case c:  // to fix, uncomment this line
      break;   // no default label
   }   // C4062, enumerator 'c' not handled
}

int main() {
}
```

## <a name="see-also"></a>참고 항목

[컴파일러 경고 (수준 4) C4061](compiler-warning-level-4-c4061.md)
