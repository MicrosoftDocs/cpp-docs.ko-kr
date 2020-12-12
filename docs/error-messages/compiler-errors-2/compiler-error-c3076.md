---
description: '자세한 정보: 컴파일러 오류 C3076'
title: 컴파일러 오류 C3076
ms.date: 11/04/2016
f1_keywords:
- C3076
helpviewer_keywords:
- C3076
ms.assetid: 8a87b3e4-2c17-4b87-9622-ef0962d6a34e
ms.openlocfilehash: 27fbfe27d2e8efb1abee611701fdbde8f0d3d09f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320182"
---
# <a name="compiler-error-c3076"></a>컴파일러 오류 C3076

' instance ': 참조 형식 ' type '의 인스턴스는 네이티브 형식에 포함할 수 없습니다.

네이티브 형식은 CLR 형식의 인스턴스를 포함할 수 없습니다.

자세한 내용은 [참조 형식에 대 한 c + + 스택 의미 체계](../../dotnet/cpp-stack-semantics-for-reference-types.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3076를 생성 합니다.

```cpp
// C3076.cpp
// compile with: /clr /c
ref struct U {};

struct V {
   U y;   // C3076
};

ref struct W {
   U y;   // OK
};
```
