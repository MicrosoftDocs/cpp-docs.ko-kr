---
description: '자세한 정보: 컴파일러 경고 C4355'
title: 컴파일러 경고 C4355
ms.date: 11/04/2016
f1_keywords:
- C4355
helpviewer_keywords:
- C4355
ms.assetid: b819ecab-8a07-42d7-8fa4-1180d51626c0
ms.openlocfilehash: fd4d38aae7a3728370c89cb2298438dbc0ba616c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180775"
---
# <a name="compiler-warning-c4355"></a>컴파일러 경고 C4355

'this' : 기본 멤버 이니셜라이저 목록에서 사용되었습니다.

**`this`** 포인터는 비정적 멤버 함수 내 에서만 사용할 수 있습니다. 기본 클래스에 대 한 이니셜라이저 목록에서 사용할 수 없습니다.

기본 클래스 생성자 및 클래스 멤버 생성자는 생성자 이전에 호출 됩니다 **`this`** . 실제로 생성 되지 않은 개체에 대 한 포인터를 다른 생성자에 게 전달 했습니다. 다른 생성자가이에서 멤버에 액세스 하거나 멤버 함수를 호출 하는 경우 결과가 정의 되지 않습니다. **`this`** 모든 생성이 완료 될 때까지 포인터를 사용 하면 안 됩니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

다음 샘플에서는 C4355를 생성 합니다.

```cpp
// C4355.cpp
// compile with: /w14355 /c
#include <tchar.h>

class CDerived;
class CBase {
public:
   CBase(CDerived *derived): m_pDerived(derived) {};
   ~CBase();
   virtual void function() = 0;

   CDerived * m_pDerived;
};

class CDerived : public CBase {
public:
   CDerived() : CBase(this) {};   // C4355 "this" used in derived c'tor
   virtual void function() {};
};

CBase::~CBase() {
   m_pDerived -> function();
}

int main() {
   CDerived myDerived;
}
```
