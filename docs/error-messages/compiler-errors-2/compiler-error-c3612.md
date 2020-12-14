---
description: '자세한 정보: 컴파일러 오류 C3612'
title: 컴파일러 오류 C3612
ms.date: 11/04/2016
f1_keywords:
- C3612
helpviewer_keywords:
- C3612
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
ms.openlocfilehash: 332d4bae940a0c98b148fd6ba951a4f51d1bee27
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97223102"
---
# <a name="compiler-error-c3612"></a>컴파일러 오류 C3612

' type ': sealed 클래스는 abstract 일 수 없습니다.

를 사용 하 여 정의 된 형식은 `value` 기본적으로 sealed 이며 클래스는 기본의 모든 메서드를 구현 하지 않는 한 추상 클래스입니다. 봉인 된 추상 클래스는 기본 클래스 이거나 인스턴스화될 수 없습니다.

자세한 내용은 [클래스 및 구조체](../../extensions/classes-and-structs-cpp-component-extensions.md)를 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3612를 생성 합니다.

```cpp
// C3612.cpp
// compile with: /clr /c
value struct V: public System::ICloneable {};   // C3612

// OK
value struct V2: public System::ICloneable {
   Object^ Clone();
};
```
