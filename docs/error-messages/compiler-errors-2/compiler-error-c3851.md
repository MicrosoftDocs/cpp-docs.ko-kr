---
title: 컴파일러 오류 C3851
ms.date: 09/05/2018
f1_keywords:
- C3851
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
ms.openlocfilehash: 97d9ef1eeeffa0e5a63d2c8ae2428a3fad0ff238
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165588"
---
# <a name="compiler-error-c3851"></a>컴파일러 오류 C3851

> '*char*': 유니버설 문자 이름에는 기본 문자 집합의 문자를 지정할 수 없습니다.

## <a name="remarks"></a>주의

C++로 컴파일된 코드에서는 문자열 또는 문자 리터럴 외부에서 기본 소스 문자 집합의 문자를 나타내는 유니버설 문자 이름을 사용할 수 없습니다. 자세한 내용은 [Character Sets](../../cpp/character-sets.md)을 참조하세요. C로 컴파일된 코드에서는 0x24 (' $ '), 0x40 ('\@') 또는 0x60 ('\`')을 제외 하 고 0x20-0x7f (포함) 범위의 문자에 유니버설 문자 이름을 사용할 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3851을 생성하고 해결 방법을 보여 줍니다.

```cpp
// C3851.cpp
int main()
{
   int test1_\u0041 = 0;   // C3851, \u0041 = 'A' in basic character set
   int test2_A = 0;        // OK
}
```
