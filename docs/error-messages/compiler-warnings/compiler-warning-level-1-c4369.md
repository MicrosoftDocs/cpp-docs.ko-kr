---
title: 컴파일러 경고(수준 1) C4369
ms.date: 11/04/2016
f1_keywords:
- C4369
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
ms.openlocfilehash: b0d99792e3e0ea372c8629319553dd9a59ad4b47
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187065"
---
# <a name="compiler-warning-level-1-c4369"></a>컴파일러 경고(수준 1) C4369

' enumerator ': ' value ' 열거자 값을 ' type '으로 표시할 수 없습니다. 값은 ' new_value '입니다.

열거자가 지정 된 내부 형식에 대 한 최대 값 보다 크게 계산 되었습니다.  이로 인해 오버플로가 발생 하 고 컴파일러가 열거자 값을 형식에 사용할 수 있는 가장 낮은 값으로 래핑 했습니다.

## <a name="example"></a>예제

다음 샘플에서는 C4369를 생성 합니다.

```cpp
// C4369.cpp
// compile with: /W1
int main() {
   enum Color: char { red = 0x7e, green, blue };   // C4369
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK
}
```
