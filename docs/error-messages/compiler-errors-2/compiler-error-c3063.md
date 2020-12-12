---
description: '자세한 정보: 컴파일러 오류 C3063'
title: 컴파일러 오류 C3063
ms.date: 11/04/2016
f1_keywords:
- C3063
helpviewer_keywords:
- C3063
ms.assetid: 0ecf6f1f-e4a7-487a-9fd5-79d8ac470001
ms.openlocfilehash: 304359e34b6cbae07d2f901db02c6e5ed04e373c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281706"
---
# <a name="compiler-error-c3063"></a>컴파일러 오류 C3063

연산자 ' operator ': 모든 피연산자의 열거형 형식이 동일 해야 합니다.

열거자에서 연산자를 사용 하는 경우 두 피연산자가 모두 열거형 형식 이어야 합니다. 자세한 내용은 [방법: c + +/cli에서 열거형 정의 및 사용](../../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3063를 생성 하 고 수정 하는 방법을 보여 줍니다.

```cpp
// C3063.cpp
// compile with: /clr
enum class E { a, b } e, mask;
int main() {
   if ( ( e & mask ) != 0 ) ;   // C3063 no operator!= (E, int)

   if ( ( e & mask ) != E() )   // OK
      ;
}
```
