---
title: 컴파일러 경고(수준 4) C4242
ms.date: 11/04/2016
f1_keywords:
- C4242
helpviewer_keywords:
- C4242
ms.assetid: 8df742e1-fbf1-42f3-8e93-c0e1c222dc7e
ms.openlocfilehash: ed145444d6eec583c448a3a49167ca1f82644f0b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510002"
---
# <a name="compiler-warning-level-4-c4242"></a>컴파일러 경고(수준 4) C4242

' identifier ': ' type1 '에서 ' type2 ' (으)로 변환 하 여 데이터가 손실 될 수 있습니다.

형식이 다릅니다. 형식 변환으로 인해 데이터가 손실 될 수 있습니다. 컴파일러는 형식 변환을 수행 합니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

C4242에 대 한 자세한 내용은 [일반적인 컴파일러 오류](/windows/win32/WinProg64/common-compiler-errors)를 참조 하세요.

다음 샘플에서는 C4242를 생성 합니다.

```
// C4242.cpp
// compile with: /W4
#pragma warning(4:4242)
int func() {
   return 0;
}

int main() {
   char a;
   a = func();   // C4242, return type and variable type do not match
}
```