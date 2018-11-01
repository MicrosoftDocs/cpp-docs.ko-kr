---
title: 소비자에게 반환되는 열을 동적으로 결정
ms.date: 10/26/2018
helpviewer_keywords:
- bookmarks [C++], dynamically determining columns
- dynamically determining columns [C++]
ms.assetid: 58522b7a-894e-4b7d-a605-f80e900a7f5f
ms.openlocfilehash: 0d01fdac1a64bee62bd7227f4efac8650ff635b8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428382"
---
# <a name="dynamically-determining-columns-returned-to-the-consumer"></a>소비자에게 반환되는 열을 동적으로 결정

PROVIDER_COLUMN_ENTRY 매크로 정상적으로 처리 된 `IColumnsInfo::GetColumnsInfo` 호출 합니다. 그러나 소비자는 책갈피를 사용 하도록 선택할 수, 있으므로 공급자 소비자는 책갈피를 요청 하는 여부에 따라 반환 되는 열을 변경할 수 여야 합니다.

처리 하는 `IColumnsInfo::GetColumnsInfo` 함수를 정의 하는 PROVIDER_COLUMN_MAP, 삭제를 호출할 `GetColumnInfo`에서 `CAgentMan` 사용자 CustomRS.h에서 기록 하 고 고유한 정의로 바꿉니다 `GetColumnInfo` 함수:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.H
class CAgentMan
{
public:
   DWORD dwBookmark;
   TCHAR szCommand[256];
   TCHAR szText[256];
   TCHAR szCommand2[256];
   TCHAR szText2[256];
  
   static ATLCOLUMNINFO* GetColumnInfo(void* pThis, ULONG* pcCols);
   bool operator==(const CAgentMan& am)
   {
      return (lstrcmpi(szCommand, am.szCommand) == 0);
   }
};
```

다음으로 구현 된 `GetColumnInfo` 함수 *사용자 지정*RS.cpp, 다음 코드에 표시 된 대로 합니다.

`GetColumnInfo` 먼저 확인 하는 경우 OLE DB 속성인 `DBPROP_BOOKMARKS` 설정 됩니다. 속성을 가져올 `GetColumnInfo` 대 한 포인터를 사용 하 여 (`pRowset`) 행 집합 개체입니다. `pThis` 포인터 클래스인 속성 맵에 저장 된 행 집합을 생성 하는 클래스를 나타냅니다. `GetColumnInfo` 포인터로 변환 합니다 `pThis` 에 대 한 포인터는 `RCustomRowset` 포인터입니다.

확인 하는 `DBPROP_BOOKMARKS` 속성인 `GetColumnInfo` 사용 하 여를 `IRowsetInfo` 인터페이스를 호출 하 여 얻을 수 있습니다 `QueryInterface` 에 `pRowset` 인터페이스. 또는 ATL을 사용할 수 있습니다 [CComQIPtr](../../atl/reference/ccomqiptr-class.md) 메서드 대신 합니다.

```cpp
////////////////////////////////////////////////////////////////////
// CustomRS.cpp
ATLCOLUMNINFO* CAgentMan::GetColumnInfo(void* pThis, ULONG* pcCols)
{
   static ATLCOLUMNINFO _rgColumns[5];
   ULONG ulCols = 0;
  
   // Check the property flag for bookmarks; if it is set, set the zero 
   // ordinal entry in the column map with the bookmark information.
   CAgentRowset* pRowset = (CAgentRowset*) pThis;
   CComQIPtr<IRowsetInfo, &IID_IRowsetInfo> spRowsetProps = pRowset;
  
   CDBPropIDSet set(DBPROPSET_ROWSET);
   set.AddPropertyID(DBPROP_BOOKMARKS);
   DBPROPSET* pPropSet = NULL;
   ULONG ulPropSet = 0;
   HRESULT hr;
  
   if (spRowsetProps)
      hr = spRowsetProps->GetProperties(1, &set, &ulPropSet, &pPropSet);
  
   if (pPropSet)
   {
      CComVariant var = pPropSet->rgProperties[0].vValue;
      CoTaskMemFree(pPropSet->rgProperties);
      CoTaskMemFree(pPropSet);
  
      if (SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE))
      {
         ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD), 
         DBTYPE_BYTES, 0, 0, GUID_NULL, CAgentMan, dwBookmark, 
         DBCOLUMNFLAGS_ISBOOKMARK)
         ulCols++;
      }
   }
  
   // Next, set the other columns up.
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Command"), 1, 256, DBTYPE_STR, 0xFF, 0xFF, 
      GUID_NULL, CAgentMan, szCommand)
   ulCols++;
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Text"), 2, 256, DBTYPE_STR, 0xFF, 0xFF, 
      GUID_NULL, CAgentMan, szText)
   ulCols++;
  
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Command2"), 3, 256, DBTYPE_STR, 0xFF, 0xFF, 
      GUID_NULL, CAgentMan, szCommand2)
   ulCols++;
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Text2"), 4, 256, DBTYPE_STR, 0xFF, 0xFF, 
      GUID_NULL, CAgentMan, szText2)
   ulCols++;
  
   if (pcCols != NULL)
      *pcCols = ulCols;
  
   return _rgColumns;
}
```

이 예제에서는 정적 배열 열 정보를 저장 합니다. 소비자는 책갈피 열을 표시 하려고 하지 않습니다, 경우 배열에 있는 하나의 항목을 사용 하지 않습니다. 정보를 처리 하려면 두 배열 매크로 만듭니다: ADD_COLUMN_ENTRY 및 ADD_COLUMN_ENTRY_EX 합니다. ADD_COLUMN_ENTRY_EX는 추가 매개 변수로 *플래그*되는 책갈피 열을 지정 하는 경우 필요 합니다.

```cpp
ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD),
   DBTYPE_BYTES, 0, 0, GUID_NULL, CAgentMan, dwBookmark,
   DBCOLUMNFLAGS_ISBOOKMARK)
```

이제 컴파일 및 향상 된 공급자를 실행할 수 있습니다. 에 설명 된 대로 공급자를 테스트 하려면 테스트 소비자를 수정 [단순 소비자 구현](../../data/oledb/implementing-a-simple-consumer.md)합니다. 공급자를 사용 하 여 테스트 소비자를 실행 합니다. 확인을 클릭 하면 테스트 소비자의 공급자에서 적절 한 문자열을 검색 하는 **실행할** 단추를 **소비자 테스트** 대화 상자.

## <a name="see-also"></a>참고 항목

[단순한 읽기 전용 공급자의 기능 향상](../../data/oledb/enhancing-the-simple-read-only-provider.md)<br/>
