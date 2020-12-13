---
description: '자세한 정보: 컴파일러 오류 C2868'
title: 컴파일러 오류 C2868
ms.date: 11/04/2016
f1_keywords:
- C2868
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
ms.openlocfilehash: c6a6368fbdfe61014a606fadce92322234e438f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333791"
---
# <a name="compiler-error-c2868"></a>컴파일러 오류 C2868

> '*identifier*': using 선언 구문이 잘못 되었습니다. 정규화 된 이름이 필요 합니다.

[Using 선언](../../cpp/using-declaration.md) 에는 식별자 이름으로 끝나는 *정규화 된 이름*, 범위-연산자 ()로 구분 된 `::` 네임 스페이스, 클래스 또는 열거형 이름 시퀀스가 필요 합니다. 단일 범위 확인 연산자를 사용 하 여 전역 네임 스페이스의 이름을 도입할 수 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C2868를 생성 하 고 올바른 사용법도 보여 줍니다.

```cpp
// C2868.cpp
class X {
public:
   int i;
};

class Y : X {
public:
   using X::i;   // OK
};

int main() {
   using X;   // C2868
}
```
