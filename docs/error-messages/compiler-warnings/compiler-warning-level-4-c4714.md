---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4714'
title: 컴파일러 경고(수준 4) C4714
ms.date: 11/04/2016
f1_keywords:
- C4714
helpviewer_keywords:
- C4714
ms.assetid: 22c7fd0c-899d-4e9b-95f3-725b2c49fb46
ms.openlocfilehash: aca186ba6d81c0d769837e26023538e7e980fbc6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330578"
---
# <a name="compiler-warning-level-4-c4714"></a>컴파일러 경고(수준 4) C4714

> ' function ' 함수가 인라이닝 되지 __forceinline로 표시 되었습니다.

지정 된 함수가 인라인 확장을 위해 선택 되었지만 컴파일러가 인라이닝을 수행 하지 않았습니다.

**`__forceinline`** 는 컴파일러에 대 한 보다 강력한 표시 이지만 **`__inline`** 인라인은 여전히 컴파일러의 판단에 따라 수행 되지만 추론을 사용 하 여이 함수를 인라인 하는 이점을 확인 하지는 않습니다.

경우에 따라 컴파일러는 기계적 이유로 특정 함수를 인라인 하지 않습니다. 예를 들어 컴파일러는 인라인 되지 않습니다.

- SEH와 c + + EH를 혼합 하 여 발생 하는 함수입니다.

- -EHs/EHa/가 on 일 때 복사 생성 된 개체가 값으로 전달 되는 일부 함수

- -Unwindable/EHs/EHa가 on 인 경우 값으로 개체를 반환 하는 함수입니다.

- -Og/황소/O1/O2 없이 컴파일하는 경우 인라인 어셈블리를 사용 하는 함수입니다.

- 가변 인수 목록을 사용 하는 함수입니다.

- **`try`**(C + + 예외 처리) 문을 사용 하는 함수입니다.

다음 샘플에서는 C4714를 생성 합니다.

```cpp
// C4714.cpp
// compile with: /Ob1 /GX /W4
__forceinline void func1()
{
   try
   {
   }
   catch (...)
   {
   }
}

void func2()
{
   func1();   // C4714
}

int main()
{
}
```
