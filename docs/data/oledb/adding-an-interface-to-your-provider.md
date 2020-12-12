---
description: '자세한 정보: 공급자에 인터페이스 추가'
title: 공급자에 인터페이스 추가
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB provider templates, object interfaces
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
ms.openlocfilehash: 0514f57489fd0a5d97f659fc5695cc7e0f8e03e3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97246073"
---
# <a name="adding-an-interface-to-your-provider"></a>공급자에 인터페이스 추가

> [!NOTE]
> Visual Studio 2019 이상에서는 ATL OLE DB 공급자 마법사를 사용할 수 없습니다.

인터페이스를 추가하려는 개체를 결정합니다(일반적으로 데이터 소스, 행 집합, 명령 또는 **OLE DB 공급자 마법사** 에서 생성된 세션 개체). 인터페이스를 추가해야 하는 개체가 공급자에서 현재 지원하지 않는 개체일 수 있습니다. 이 경우, **ATL OLE DB 공급자 마법사** 를 실행하여 개체를 만듭니다. **클래스 뷰** 에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 메뉴에서 **추가** > **새 항목** 을 클릭한 다음, **설치됨** > **Visual C++** > **ATL** 을 선택하고 **ATL OLEDB 공급자** 를 클릭합니다. 인터페이스 코드를 별도의 디렉터리에 배치한 다음, 공급자 프로젝트에 파일을 복사하는 것이 좋습니다.

인터페이스를 지원하는 새 클래스를 만든 경우 개체가 해당 클래스에서 상속받도록 합니다. 예를 들어 행 집합 개체에 `IRowsetIndexImpl` 클래스를 추가할 수 있습니다.

```cpp
template <class Creator>
class CCustomRowset :
    public CRowsetImpl< CCustomRowset<Creator>, CCustomWindowsFile, Creator>,
    public IRowsetIndexImpl< ... >
```

COM_INTERFACE_ENTRY 매크로를 사용하여 개체의 COM_MAP에 인터페이스를 추가합니다. 맵이 없으면 새로 만듭니다. 예를 들어:

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
END_COM_MAP()
```

행 집합 개체의 경우 개체가 부모 클래스에 위임할 수 있도록 부모 개체의 맵을 연결합니다. 이 예제에서는 COM_INTERFACE_ENTRY_CHAIN 매크로를 맵에 추가합니다.

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)
END_COM_MAP()
```

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿 사용](../../data/oledb/working-with-ole-db-provider-templates.md)
