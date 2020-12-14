---
description: '자세한 정보: 컴파일러 오류 C3706'
title: 컴파일러 오류 C3706
ms.date: 11/04/2016
f1_keywords:
- C3706
helpviewer_keywords:
- C3706
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
ms.openlocfilehash: e4dcb65d29e24ae40bc311f1d4229edca173e916
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241861"
---
# <a name="compiler-error-c3706"></a>컴파일러 오류 C3706

' function ': COM 이벤트를 발생 시키려면 COM 인터페이스 여야 합니다.

COM 이벤트를 발생 시키는 데 사용 하는 이벤트 인터페이스는 COM 인터페이스 여야 합니다. 이 경우 인터페이스는 Visual C++ 특성을 사용 하 여 정의 하거나 #import의 embedded_idl 특성이 있는 형식 라이브러리의 [#import](../../preprocessor/hash-import-directive-cpp.md) 를 사용 하 여 가져와야 합니다.

`#include`아래 샘플에 표시 된 ATL 헤더 파일의 줄은 COM 이벤트를 사용 하는 데 필요 합니다. 이 오류를 해결 하려면 `IEvents` 다음 특성 중 하나를 인터페이스 정의에 적용 하 여 (이벤트 인터페이스) COM 인터페이스를 만듭니다 ( [개체](../../windows/attributes/object-cpp.md), [이중](../../windows/attributes/dual.md)또는 인터페이스 정의 [](../../windows/attributes/dispinterface.md)).

인터페이스가 MIDL에 의해 생성 된 헤더 파일에서 가져온 경우 컴파일러는 COM 인터페이스로 인식 하지 못합니다.

다음 샘플에서는 C3706를 생성 합니다.

```cpp
// C3706.cpp
// compile with: /c
// C3706 expected
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[module(dll, name="idid", uuid="12341234-1234-1234-1234-123412341234")];

// Uncomment the following line to resolve.
// [object, uuid="12341234-1234-1234-1234-123412341237"]
__interface IEvents : IUnknown {
   HRESULT event1(/*[in]*/ int i);   // uncomment [in]
};

[dual, uuid="12341234-1234-1234-1234-123412341235"]
__interface IBase {
   HRESULT fireEvents();
};

[coclass, event_source(com), uuid="12341234-1234-1234-1234-123412341236"]
class CEventSrc : public IBase {
   public:
   __event __interface IEvents;

   HRESULT fireEvents() {
      HRESULT hr = IEvents_event1(123);
      return hr;
   }
};
```
