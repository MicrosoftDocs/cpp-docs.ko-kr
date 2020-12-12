---
description: '자세한 정보: CCustomRowset (CustomRS. H)'
title: CCustomRowset(CustomRS.H)
ms.date: 10/22/2018
f1_keywords:
- cmyproviderrowset
- ccustomrowset
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderRowset class in MyProviderRS.H
- CCustomRowset class in CustomRS.H
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
ms.openlocfilehash: 87025be2a34f8c850bde2be53ab01519968654d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170466"
---
# <a name="ccustomrowset-customrsh"></a>CCustomRowset(CustomRS.H)

이 마법사는 행 집합 개체에 대 한 항목을 생성 합니다. 이 경우 호출 `CCustomRowset` 됩니다. `CCustomRowset`클래스는 `CRowsetImpl` 행 집합 개체에 필요한 모든 인터페이스를 구현 하는 라는 OLE DB 공급자 클래스에서 상속 됩니다. 다음 코드에서는의 상속 체인을 보여 줍니다 `CRowsetImpl` .

```cpp
template <class T, class Storage, class CreatorClass,
   class ArrayType = CAtlArray<Storage>>
class CMyRowsetImpl:
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType,
      CSimpleRow, IRowsetLocateImpl< T >>
```

`CRowsetImpl` 또한는 `IAccessor` 및 인터페이스를 사용 `IColumnsInfo` 합니다. 테이블의 출력 필드에 대해 이러한 인터페이스를 사용 합니다. 또한 클래스는 `IRowsetIdentity` 소비자가 두 행이 동일한 지 여부를 확인할 수 있도록 하는에 대 한 구현을 제공 합니다. `IRowsetInfo`인터페이스는 행 집합 개체에 대 한 속성을 구현 합니다. `IConvertType`인터페이스를 사용 하면 공급자가 소비자가 요청한 데이터 형식과 공급자가 사용 하는 데이터 형식의 차이를 해결할 수 있습니다.

이 `IRowset` 인터페이스는 실제로 데이터 검색을 처리 합니다. 소비자는 먼저 라는 메서드를 호출 `GetNextRows` 하 여 행에 대 한 핸들을 반환 `HROW` 합니다. 그런 다음 소비자는를 사용 하 여를 호출 하 여 `IRowset::GetData` `HROW` 요청 된 데이터를 검색 합니다.

`CRowsetImpl` 는 또한 여러 템플릿 매개 변수를 사용 합니다. 이러한 매개 변수를 사용 하 여 클래스가 데이터를 처리 하는 방법을 결정할 수 있습니다 `CRowsetImpl` . 인수를 사용 하면 `ArrayType` 행 데이터를 저장 하는 데 사용 되는 저장소 메커니즘을 확인할 수 있습니다. *Rowclass* 매개 변수는를 포함 하는 클래스를 지정 합니다 `HROW` .

*RowsetInterface* 매개 변수를 사용 하 여 또는 인터페이스를 사용할 수도 있습니다 `IRowsetLocate` `IRowsetScroll` . `IRowsetLocate`및 `IRowsetScroll` 인터페이스는 모두에서 상속 `IRowset` 됩니다. 따라서 OLE DB 공급자 템플릿은 이러한 인터페이스에 대 한 특별 한 처리를 제공 해야 합니다. 이러한 인터페이스 중 하나를 사용 하려는 경우이 매개 변수를 사용 해야 합니다.

## <a name="see-also"></a>참고 항목

[공급자 Wizard-Generated 파일](../../data/oledb/provider-wizard-generated-files.md)<br/>
