---
description: '자세한 정보: 사용자 레코드'
title: 사용자 레코드
ms.date: 05/09/2019
f1_keywords:
- COLUMN_ENTRY_MAP
helpviewer_keywords:
- rowsets [C++], accessors
- COLUMN_ENTRY macro
- COLUMN_ENTRY_MAP macro
- user records, OLE DB consumer templates
- OLE DB consumer templates, user records
- CAccessor class, example
- BEGIN_ACCESSOR_MAP macro
- accessors [C++], rowsets
- accessors [C++], static
- BEGIN_ACCESSOR macro, example
ms.assetid: 2de9e5eb-53ce-42b1-80fa-57d46600a80c
ms.openlocfilehash: 1d31ef93bb1b06925306c84d436d7a7837a08431
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322327"
---
# <a name="user-records"></a>사용자 레코드

> [!NOTE]
> Visual Studio 2019 이상에서는 ATL OLE DB 소비자 마법사를 사용할 수 없습니다. 수동으로 기능을 추가할 수는 있습니다. 자세한 내용은 [마법사를 사용하지 않고 소비자 만들기](creating-a-consumer-without-using-a-wizard.md)를 참조하세요.

정적 접근자(즉, `CAccessor`에서 파생된 접근자)를 사용하려면 소비자에 사용자 레코드가 있어야 합니다. 사용자 레코드는 입력 또는 출력을 처리할 데이터 요소가 포함된 C++ 클래스입니다. **ATL OLE DB 소비자 마법사** 에서 소비자에 대한 사용자 레코드를 생성합니다. 명령 처리와 같은 선택적 작업을 위한 메서드를 사용자 레코드에 추가할 수 있습니다.

다음 코드에서는 명령을 처리하는 샘플 레코드를 보여 줍니다. 사용자 레코드에서 BEGIN_COLUMN_MAP은 공급자에서 소비자로 전달되는 데이터 행 집합을 나타냅니다. BEGIN_PARAM_MAP는 명령 매개 변수 집합을 나타냅니다. 이 예제에서는 [CCommand](../../data/oledb/ccommand-class.md) 클래스를 사용하여 명령 매개 변수를 처리합니다. 맵 항목의 데이터 멤버는 각 클래스 인스턴스에 대한 연속 메모리 블록의 오프셋을 나타냅니다. COLUMN_ENTRY 매크로는 공급자 쪽의 PROVIDER_COLUMN_ENTRY 매크로에 해당합니다.

COLUMN_MAP 및 PARAM_MAP 매크로에 대한 자세한 내용은 [OLE DB 소비자 템플릿에 대한 매크로](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)를 참조하세요.

```cpp
class CArtists
{
public:
// Data Elements
   CHAR m_szFirstName[20];
   CHAR m_szLastName[30];
   short m_nAge;

// Column binding map
BEGIN_COLUMN_MAP(CArtists)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
   COLUMN_ENTRY(3, m_nAge)
END_COLUMN_MAP()

// Parameter binding map
BEGIN_PARAM_MAP(CArtists)
   COLUMN_ENTRY(1, m_nAge)
END_PARAM_MAP()
};
```

## <a name="wizard-generated-user-records"></a>마법사 생성 사용자 레코드

**ATL OLE DB 소비자 마법사** 를 사용하여 소비자를 생성하는 경우 OLE DB 템플릿 또는 OLE DB 특성을 사용하도록 선택할 수 있습니다. 선택 내용에 따라 생성되는 코드가 다릅니다. 이 코드에 대한 자세한 내용은 [소비자 마법사 생성 클래스](../../data/oledb/consumer-wizard-generated-classes.md)를 참조하세요.

## <a name="user-record-support-for-multiple-accessors"></a>여러 접근자에 대한 사용자 레코드 지원

여러 접근자를 사용해야 하는 시나리오에 대한 자세한 내용은 [행 집합에서 여러 접근자 사용](../../data/oledb/using-multiple-accessors-on-a-rowset.md)을 참조하세요.

다음 예제에서는 행 집합에서 여러 접근자를 지원하도록 수정된 사용자 레코드를 보여 줍니다. BEGIN_COLUMN_MAP 및 END_COLUMN_MAP 대신 [BEGIN_ACCESSOR_MAP](./macros-and-global-functions-for-ole-db-consumer-templates.md#begin_accessor_map) 및 [BEGIN_ACCESSOR](./macros-and-global-functions-for-ole-db-consumer-templates.md#begin_accessor)를 각 접근자에 사용합니다. BEGIN_ACCESSOR 매크로는 접근자 수(0에서의 오프셋) 및 접근자가 자동 접근자인지 여부를 지정합니다. 자동 접근자는 `GetData`를 호출하여 [MoveNext](./crowset-class.md#movenext) 호출에서 자동으로 데이터를 검색합니다. 자동이 아닌 접근자를 사용하는 경우 명시적으로 데이터를 검색해야 합니다. 모든 레코드에 대해 검색하지 않으려는 대규모 데이터 필드(예: 비트맵 이미지)에 바인딩하는 경우 자동이 아닌 접근자를 사용합니다.

```cpp
class CMultiArtists
{
public:
// Data Elements
   CHAR m_szFirstName[20];
   CHAR m_szLastName[30];
   short m_nAge;

// Column binding map
BEGIN_ACCESSOR_MAP(CMultiArtists, 2)
   BEGIN_ACCESSOR(0, true)    // true specifies an auto accessor
    COLUMN_ENTRY(1, m_szFirstName)
    COLUMN_ENTRY(2, m_szLastName)
   END_ACCESSOR()
   BEGIN_ACCESSOR(1, false)   // false specifies a manual accessor
    COLUMN_ENTRY(3, m_nAge)
   END_ACCESSOR()
END_ACCESSOR_MAP()
};
```

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)
