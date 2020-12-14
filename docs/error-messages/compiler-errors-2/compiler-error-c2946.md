---
description: '자세한 정보: 컴파일러 오류 C2946'
title: 컴파일러 오류 C2946
ms.date: 11/04/2016
f1_keywords:
- C2946
helpviewer_keywords:
- C2946
ms.assetid: c86dfbfc-7702-4f09-8a53-d205710e99c2
ms.openlocfilehash: 7a74b17c10acd55a254c0d7fba5c8269689e3094
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249505"
---
# <a name="compiler-error-c2946"></a>컴파일러 오류 C2946

명시적 인스턴스화. 'class'는 템플릿-클래스 특수화가 아닙니다.

템플릿이 아닌 클래스를 명시적으로 인스턴스화할 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C2946을 생성합니다.

```cpp
// C2946.cpp
class C {};
template C;  // C2946
int main() {}
```
