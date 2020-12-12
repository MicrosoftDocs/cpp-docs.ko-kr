---
description: '자세히 알아보기: OLE DB 규칙 테스트 전달'
title: OLE DB 적합성 테스트 통과
ms.date: 11/04/2016
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- conformance testing
- conformance testing [OLE DB]
- OLE DB providers, testing
ms.assetid: d1a4f147-2edd-476c-b452-0e6a0ac09891
ms.openlocfilehash: d2a5b788b3a118293800b02a9383fbde9845cfa5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286725"
---
# <a name="passing-ole-db-conformance-tests"></a>OLE DB 적합성 테스트 통과

공급자의 일관성을 유지 하기 위해 데이터 액세스 SDK는 OLE DB 규칙 테스트 집합을 제공 합니다. 테스트는 공급자의 모든 측면을 확인 하 고 공급자가 예상 대로 작동 하는지 확인 합니다. Microsoft Data Access SDK에서 OLE DB 규칙 테스트를 찾을 수 있습니다. 이 섹션에서는 규칙 테스트를 전달 하기 위해 수행 해야 하는 작업을 중점적으로 설명 합니다. OLE DB 규칙 테스트를 실행 하는 방법에 대 한 자세한 내용은 SDK를 참조 하세요.

## <a name="running-the-conformance-tests"></a>규칙 테스트 실행

Visual C++ 6.0에서 OLE DB 공급자 템플릿은 값 및 속성을 확인할 수 있도록 여러 후크 함수를 추가 했습니다. 이러한 함수는 대부분 규칙 테스트에 대 한 응답으로 추가 되었습니다.

> [!NOTE]
> OLE DB 규칙 테스트를 통과 하는 공급자에 대 한 여러 유효성 검사 함수를 추가 해야 합니다.

이 공급자에는 두 가지 유효성 검사 루틴이 필요 합니다. 첫 번째 루틴은 `CRowsetImpl::ValidateCommandID` 행 집합 클래스의 일부입니다. 공급자 템플릿으로 행 집합을 만드는 동안 호출 됩니다. 이 샘플에서는이 루틴을 사용 하 여 소비자에 게 인덱스를 지원 하지 않는다는 사실을 알립니다. 첫 번째 호출은입니다 `CRowsetImpl::ValidateCommandID` . 공급자는 `_RowsetBaseClass` 책갈피에 `CCustomRowset` [대 한 공급자 지원](../../data/oledb/provider-support-for-bookmarks.md)의에 대 한 인터페이스 맵에 추가 된 typedef를 사용 하므로 템플릿 인수의 긴 줄을 입력할 필요가 없습니다. 그런 다음 인덱스 매개 변수가 NULL이 아닌 경우 DB_E_NOINDEX를 반환 합니다 .이는 소비자가 u의 인덱스를 사용 하려고 함을 나타냅니다. 명령 Id에 대 한 자세한 내용은 OLE DB 사양을 참조 하 고을 찾습니다 `IOpenRowset::OpenRowset` .

다음 코드는 `ValidateCommandID` 유효성 검사 루틴입니다.

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H
// Class: CCustomRowset

HRESULT ValidateCommandID(DBID* pTableID, DBID* pIndexID)
{
   HRESULT hr = _RowsetBaseClass::ValidateCommandID(pTableID, pIndexID);
   if (hr != S_OK)
      return hr;

   if (pIndexID != NULL)
      return DB_E_NOINDEX;    // Doesn't support indexes

   return S_OK;
}
```

공급자 템플릿은 `OnPropertyChanged` 사용자가 DBPROPSET_ROWSET 그룹의 속성을 변경할 때마다 메서드를 호출 합니다. 다른 그룹에 대 한 속성을 처리 하려면 해당 개체를 적절 한 개체에 추가 합니다. 즉, 클래스에서 DBPROPSET_SESSION 검사를 수행 `CCustomSession` 합니다.

이 코드는 먼저 속성이 다른에 연결 되었는지 여부를 확인 합니다. 속성이 연결 되는 경우 DBPROP_BOOKMARKS 속성을로 설정 합니다 `True` . OLE DB 사양의 부록 C에는 속성에 대 한 정보가 포함 되어 있습니다. 또한이 정보는 속성이 다른에 연결 되는지 여부를 알려 줍니다.

코드에 루틴을 추가 해야 할 수도 있습니다 `IsValidValue` . `IsValidValue`속성을 설정 하려고 할 때 템플릿이 호출 됩니다. 속성 값을 설정할 때 추가 처리가 필요한 경우이 메서드를 재정의 합니다. 각 속성 집합에 대해 이러한 메서드 중 하나를 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[고급 공급자 기술](../../data/oledb/advanced-provider-techniques.md)
