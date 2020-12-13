---
description: '자세한 정보: 컴파일러 오류 C3908'
title: 컴파일러 오류 C3908
ms.date: 11/04/2016
f1_keywords:
- C3908
helpviewer_keywords:
- C3908
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
ms.openlocfilehash: 67258f9f5946d180af9a270b931f88f263238856
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144172"
---
# <a name="compiler-error-c3908"></a>컴파일러 오류 C3908

' 구문 ' 보다 액세스 수준이 덜 제한적입니다.

속성 접근자 메서드 (get 또는 set)는 속성 자체에 지정 된 액세스 보다 덜 제한적으로 액세스할 수 없습니다.  마찬가지로 이벤트 접근자 메서드의 경우입니다.

자세한 내용은 [속성](../../extensions/property-cpp-component-extensions.md) 및 [이벤트](../../extensions/event-cpp-component-extensions.md)를 참조 하세요.

다음 샘플에서는 C3908를 생성 합니다.

```cpp
// C3908.cpp
// compile with: /clr
ref class X {
protected:
   property int i {
   public:   // C3908 property i is protected
      int get();
   private:
      void set(int);   // OK more restrictive
   };
};
```
