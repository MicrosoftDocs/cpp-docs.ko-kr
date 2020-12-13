---
description: '자세한 정보: 심각한 오류 C1308'
title: 심각한 오류 C1308
ms.date: 11/04/2016
f1_keywords:
- C1308
helpviewer_keywords:
- C1308
ms.assetid: 46177997-069e-433a-8e20-93c846d78ffd
ms.openlocfilehash: 9d9b8cee128b9ed830c4ba3651ee609d91d42eac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177876"
---
# <a name="fatal-error-c1308"></a>심각한 오류 C1308

어셈블리 연결은 지원 되지 않습니다.

.netmodule을 링커에 대한 입력 파일로 사용할 수 있지만 어셈블리는 사용할 수 없습니다. 이 오류는로 컴파일된 어셈블리를 연결 하려고 할 때 발생할 수 있습니다 `/clr:safe` .

자세한 내용은 [링커 입력 파일로 사용하는 .netmodule 파일](../../build/reference/netmodule-files-as-linker-input.md)을 참조하세요.

다음 샘플에서는 C1308를 생성 합니다.

```cpp
// C1308.cpp
// compile with: /clr:safe /LD
public ref class MyClass {
public:
   int i;
};
```

그런 다음

```cpp
// C1308b.cpp
// compile with: /clr /link C1308b.obj C1308.dll
// C1308 expected
#using "C1308.dll"
int main() {
   MyClass ^ my = gcnew MyClass();
}
```
