---
description: '자세한 정보: 컴파일러 오류 C3101'
title: 컴파일러 오류 C3101
ms.date: 11/04/2016
f1_keywords:
- C3101
helpviewer_keywords:
- C3101
ms.assetid: 4f673766-d4f7-4632-94a5-d36a83f7f4b5
ms.openlocfilehash: e0c52eadd2af4b090b34f851d561535f360a7e59
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116173"
---
# <a name="compiler-error-c3101"></a>컴파일러 오류 C3101

명명 된 특성 인수 ' field '의 식이 잘못 되었습니다.

명명 된 특성 인수를 초기화 하는 경우 값은 컴파일 타임 상수 여야 합니다.

특성에 대 한 자세한 내용은 [사용자 정의 특성](../../extensions/user-defined-attributes-cpp-component-extensions.md)을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3101를 생성 합니다.

```cpp
// C3101.cpp
// compile with: /clr /c
ref class AAttribute : System::Attribute {
public:
   int Field;
};

extern int i;

[assembly:A(Field = i)];   // C3101
[assembly:A(Field = 0)];   // OK
```
