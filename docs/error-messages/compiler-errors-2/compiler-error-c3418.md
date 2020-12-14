---
description: '자세한 정보: 컴파일러 오류 C3418'
title: 컴파일러 오류 C3418
ms.date: 11/04/2016
f1_keywords:
- C3418
helpviewer_keywords:
- C3418
ms.assetid: 54042c04-3c45-41c1-bad7-90f9ee05a21b
ms.openlocfilehash: 38082b7fe9ffa0ebcc7b4857e77395664a9f0c42
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316234"
---
# <a name="compiler-error-c3418"></a>컴파일러 오류 C3418

액세스 지정자 'specifier'는 지원되지 않습니다.

CLR 액세스 지정자를 잘못 지정했습니다.  자세한 내용은 [방법: 클래스 및 구조체 정의 및 사용 (c + +/cli)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)의 형식 표시 유형 및 멤버 표시 유형을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3418을 생성합니다.

```cpp
// C3418.cpp
// compile with: /clr /c
ref struct m {
internal public:   // C3418
   void test(){}
};

ref struct n {
internal:   // OK
   void test(){}
};
```
