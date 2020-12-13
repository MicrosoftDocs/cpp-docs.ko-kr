---
description: '자세한 정보: 컴파일러 오류 C2351'
title: 컴파일러 오류 C2351
ms.date: 11/04/2016
f1_keywords:
- C2351
helpviewer_keywords:
- C2351
ms.assetid: 5439ccf6-66f6-4859-964c-c73f5eddfc1b
ms.openlocfilehash: ae8cf10cff4a345ee067519d250210f72e6690f8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145485"
---
# <a name="compiler-error-c2351"></a>컴파일러 오류 C2351

사용 되지 않는 c + + 생성자 초기화 구문

생성자에 대 한 새 스타일 초기화 목록에서 유일한 기본 클래스 이더라도 각 직접 기본 클래스의 이름을 명시적으로 지정할 수 있습니다.

다음 샘플에서는 C2351를 생성 합니다.

```cpp
// C2351.cpp
// compile with: /c
class B {
public:
   B() : () {}   // C2351
   B() {}   // OK
};
```
