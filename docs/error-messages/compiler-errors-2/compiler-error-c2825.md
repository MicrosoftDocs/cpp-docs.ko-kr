---
description: '자세한 정보: 컴파일러 오류 C2825'
title: 컴파일러 오류 C2825
ms.date: 11/04/2016
f1_keywords:
- C2825
helpviewer_keywords:
- C2825
ms.assetid: c832f1c1-5184-4fc2-9356-12b21daa7af3
ms.openlocfilehash: fa72f915a77ec26e6da402ae8ff87ee380f1838c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194581"
---
# <a name="compiler-error-c2825"></a>컴파일러 오류 C2825

var: 뒤에 ':: '이 올 때 클래스 또는 네임 스페이스 여야 합니다.

정규화 된 이름을 형성 하지 못했습니다.

예를 들어, 함수 이름이::로 시작 하는 함수 선언이 코드에 포함 되어 있지 않은지 확인 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C2825를 생성 합니다.

```cpp
// C2825.cpp
typedef int i;
int main() {
   int* p = new int;
   p->i::i();   // C2825
   // try the following line instead
   // p->i::~i();
}
```
