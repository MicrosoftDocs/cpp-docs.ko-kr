---
description: '자세한 정보: 컴파일러 오류 C3539'
title: 컴파일러 오류 C3539
ms.date: 11/04/2016
f1_keywords:
- C3539
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
ms.openlocfilehash: a944a2e6af03e030434cf41e2b6009be82ad9239
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315246"
---
# <a name="compiler-error-c3539"></a>컴파일러 오류 C3539

' type ': 템플릿 인수는 ' a u t o '를 포함 하는 형식일 수 없습니다.

표시 된 템플릿 인수 형식은 키워드의 사용을 포함할 수 없습니다 **`auto`** .

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. 키워드를 사용 하 여 템플릿 인수를 지정 하지 마십시오 **`auto`** .

## <a name="example"></a>예제

다음 예에서는 C3539를 생성 합니다.

```cpp
// C3539.cpp
// Compile with /Zc:auto
template<class T> class C{};
int main()
{
   C<auto> c;   // C3539
   return 0;
}
```

## <a name="see-also"></a>참조

[auto 키워드](../../cpp/auto-cpp.md)
