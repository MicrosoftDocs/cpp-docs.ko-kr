---
description: '자세한 정보: 컴파일러 경고 C4959'
title: 컴파일러 경고 C4959
ms.date: 11/04/2016
f1_keywords:
- C4959
helpviewer_keywords:
- C4959
ms.assetid: 3a128f3e-4d8a-4565-ba1a-5d32fdeb5982
ms.openlocfilehash: 3a4fae04ee654caf23776a7bf4d6b073853bd03a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336086"
---
# <a name="compiler-warning-c4959"></a>컴파일러 경고 C4959

> 해당 멤버에 액세스 하면 비안정형 코드가 생성 되므로/clr: safe에서 관리 되지 않는 '*type*' 구조체를 정의할 수 없습니다.

## <a name="remarks"></a>설명

관리되지 않는 형식의 멤버에 액세스하면 확인할 수 없는 (peverify.exe) 이미지가 생성됩니다.

자세한 내용은 [순수형 및 안정형 코드 (c + +/cli)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)를 참조 하세요.

**/Clr: safe** 컴파일러 옵션은 visual studio 2015에서 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

이 경고는 오류로 발생하며 [warning](../../preprocessor/warning.md) pragma 또는 [/wd](../../build/reference/compiler-option-warning-level.md) 컴파일러 옵션과 함께 사용하지 않도록 설정할 수 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C4959를 생성합니다.

```cpp
// C4959.cpp
// compile with: /clr:safe

// Uncomment the following line to resolve.
// #pragma warning( disable : 4959 )
struct X {
   int data;
};

int main() {
   X x;
   x.data = 10;   // C4959
}
```
