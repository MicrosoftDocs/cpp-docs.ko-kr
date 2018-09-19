---
title: 컴파일러 오류 C3352 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3352
dev_langs:
- C++
helpviewer_keywords:
- C3352
ms.assetid: f233bed7-474e-425f-aad2-7801578169d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c045df51271c761ab61a3d5ec7d97634858909a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093849"
---
# <a name="compiler-error-c3352"></a>컴파일러 오류 C3352

'function': 'type' 대리자 형식이 지정된 된 함수에 맞지

에 대 한 매개 변수 목록이 `function` / 대리자 일치 하지 않습니다.

자세한 내용은 [delegate (c + + 구성 요소 확장)](../../windows/delegate-cpp-component-extensions.md)합니다.

다음 샘플에서는 C3352 오류가 생성 됩니다.

```
// C3352.cpp
// compile with: /clr
delegate int D( int, int );
ref class C {
public:
   int mf( int ) {
      return 1;
   }

   // Uncomment the following line to resolve.
   // int mf(int, int) { return 1; }
};

int main() {
   C^ pC = gcnew C;
   System::Delegate^ pD = gcnew D( pC, &C::mf );   // C3352
}
```
