---
description: '자세한 정보: 공급자에서 자유 스레딩 지원'
title: 공급자에서 자유 스레딩 지원
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, multithreaded
- threading [C++], providers
ms.assetid: a91270dc-cdf9-4855-88e7-88a54be7cbe8
ms.openlocfilehash: 4f6785dd85ae043ce0ee74c1dda4fa365c566729
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286477"
---
# <a name="supporting-free-threading-in-your-provider"></a>공급자에서 자유 스레딩 지원

모든 OLE DB 공급자 클래스는 스레드로부터 안전 하 고 레지스트리 항목을 적절 하 게 설정 합니다. 다중 사용자 상황에서 높은 수준의 성능을 제공 하는 데 도움이 되는 무료 스레딩을 지 원하는 것이 좋습니다. 공급자를 스레드로부터 안전 하 게 유지 하기 위해 코드가 제대로 차단 되었는지 확인 해야 합니다. 데이터를 작성 하거나 저장할 때마다 임계 영역으로 액세스를 차단 해야 합니다.

각 OLE DB 공급자 템플릿 개체에는 고유한 임계 섹션이 있습니다. 차단을 더 쉽게 만들기 위해 만드는 각 새 클래스는 부모 클래스 이름을 인수로 사용 하는 템플릿 클래스 여야 합니다.

다음 예제에서는 코드를 차단 하는 방법을 보여 줍니다.

```cpp
template <class T>
class CMyObject<T> : public...

HRESULT MyObject::MyMethod(void)
{
   T* pT = (T*)this;      // this gets the parent class

// You don't need to do anything if you are only reading information

// If you want to write information, do the following:
   pT->Lock();         // engages critical section in the object
   ...;                // write whatever information you wish
   pT->Unlock();       // disengages the critical section
}
```

및를 사용 하 여 중요 한 섹션을 보호 하는 방법에 대 한 자세한 내용은 `Lock` `Unlock` [다중 스레딩: 동기화 클래스 사용 방법](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)을 참조 하세요.

재정의 하는 메서드 (예: `Execute` )가 스레드로부터 안전 하 게 보호 되는지 확인 합니다.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿 사용](../../data/oledb/working-with-ole-db-provider-templates.md)
