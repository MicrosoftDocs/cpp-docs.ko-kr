---
description: '자세한 정보: 공급자에 대 한 책갈피 지원'
title: 공급자의 책갈피 지원
ms.date: 11/04/2016
helpviewer_keywords:
- IRowsetLocate class, provider support for bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- IRowsetLocate class
- OLE DB providers, bookmark support
ms.assetid: 1b14ccff-4f76-462e-96ab-1aada815c377
ms.openlocfilehash: 0a2225f44d9d094f52e97b88eb58c6942906edf6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286659"
---
# <a name="provider-support-for-bookmarks"></a>공급자의 책갈피 지원

이 항목의 예제에서는 인터페이스를 `IRowsetLocate` 클래스에 추가 합니다 `CCustomRowset` . 거의 모든 경우에 기존 COM 개체에 인터페이스를 추가 하 여 시작 합니다. 그런 다음 소비자 템플릿에서 더 많은 호출을 추가 하 여 테스트할 수 있습니다. 예제에서는 다음을 수행 하는 방법을 보여 줍니다.

- 공급자에 인터페이스를 추가 합니다.

- 소비자에 게 반환할 열을 동적으로 결정 합니다.

- 책갈피 지원을 추가 합니다.

`IRowsetLocate` 인터페이스는 `IRowset` 인터페이스에서 상속됩니다. 인터페이스를 추가 하려면 `IRowsetLocate` `CCustomRowset` [IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)에서 상속 합니다.

인터페이스를 추가 `IRowsetLocate` 하는 것은 대부분의 인터페이스와 약간 다릅니다. VTABLEs를 설정 하기 위해 OLE DB 공급자 템플릿에는 파생 된 인터페이스를 처리 하는 템플릿 매개 변수가 있습니다. 다음 코드에서는 새 상속 목록을 보여 줍니다.

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

// CCustomRowset
class CCustomRowset : public CRowsetImpl< CCustomRowset,
      CTextData, CCustomCommand, CAtlArray<CTextData>,
      CSimpleRow,
          IRowsetLocateImpl<CCustomRowset, IRowsetLocate>>
```

네 번째, 다섯 번째 및 여섯 번째 매개 변수가 모두 추가 됩니다. 이 예에서는 네 번째 및 다섯 번째 매개 변수의 기본값을 사용 하지만를 `IRowsetLocateImpl` 여섯 번째 매개 변수로 지정 합니다. `IRowsetLocateImpl` 는 두 개의 템플릿 매개 변수를 사용 하는 OLE DB 템플릿 클래스입니다 .이 클래스는 `IRowsetLocate` 인터페이스를 클래스에 연결 `CCustomRowset` 합니다. 대부분의 인터페이스를 추가 하려면이 단계를 건너뛰고 다음 단계를 진행할 수 있습니다. `IRowsetLocate`및 `IRowsetScroll` 인터페이스만 이러한 방식으로 처리 해야 합니다.

그런 다음 `CCustomRowset` 인터페이스에 대해를 호출 하도록에 지시 해야 합니다 `QueryInterface` `IRowsetLocate` . 지도에 줄을 추가 합니다 `COM_INTERFACE_ENTRY(IRowsetLocate)` . 의 인터페이스 맵은 `CCustomRowset` 다음 코드와 같이 표시 됩니다.

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

typedef CRowsetImpl< CCustomRowset, CTextData, CCustomCommand, CAtlArray<CTextData>, CSimpleRow, IRowsetLocateImpl<CCustomRowset, IRowsetLocate>> _RowsetBaseClass;

BEGIN_COM_MAP(CCustomRowset)
   COM_INTERFACE_ENTRY(IRowsetLocate)
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)
END_COM_MAP()
```

또한 지도를 클래스에 연결 해야 `CRowsetImpl` 합니다. COM_INTERFACE_ENTRY_CHAIN 매크로에를 추가 하 여 맵에 후크 `CRowsetImpl` 합니다. 또한 `RowsetBaseClass` 상속 정보로 구성 된 typedef를 만듭니다. 이 typedef는 임의 이며 무시 해도 됩니다.

마지막으로 호출을 처리 `IColumnsInfo::GetColumnsInfo` 합니다. 일반적으로 PROVIDER_COLUMN_ENTRY 매크로를 사용 하 여이 작업을 수행 합니다. 그러나 소비자는 책갈피를 사용 하는 것이 좋습니다. 소비자가 책갈피를 요청 하는지 여부에 따라 공급자가 반환 하는 열을 변경할 수 있어야 합니다.

호출을 처리 하려면 `IColumnsInfo::GetColumnsInfo` 클래스에서 PROVIDER_COLUMN map을 삭제 합니다 `CTextData` . PROVIDER_COLUMN_MAP 매크로는 함수를 정의 합니다 `GetColumnInfo` . 사용자 고유의 함수를 정의 `GetColumnInfo` 합니다. 함수 선언은 다음과 같습니다.

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.H

class CTextData
{
   ...
     // NOTE: Be sure you removed the PROVIDER_COLUMN_MAP!
   static ATLCOLUMNINFO* GetColumnInfo(CCustomRowset* pThis,
        ULONG* pcCols);
   static ATLCOLUMNINFO* GetColumnInfo(CCustomCommand* pThis,
        ULONG* pcCols);
...
};
```

그런 다음 `GetColumnInfo` *사용자 지정* RS .cpp 파일에서 다음과 같이 함수를 구현 합니다.

```cpp
////////////////////////////////////////////////////////////////////
// CustomRS.cpp

template <class TInterface>
ATLCOLUMNINFO* CommonGetColInfo(IUnknown* pPropsUnk, ULONG* pcCols)
{
   static ATLCOLUMNINFO _rgColumns[5];
   ULONG ulCols = 0;

   CComQIPtr<TInterface> spProps = pPropsUnk;

   CDBPropIDSet set(DBPROPSET_ROWSET);
   set.AddPropertyID(DBPROP_BOOKMARKS);
   DBPROPSET* pPropSet = NULL;
   ULONG ulPropSet = 0;
   HRESULT hr;

   if (spProps)
      hr = spProps->GetProperties(1, &set, &ulPropSet, &pPropSet);

   // Check the property flag for bookmarks, if it is set, set the
// zero ordinal entry in the column map with the bookmark
// information.

   if (pPropSet)
   {
      CComVariant var = pPropSet->rgProperties[0].vValue;
      CoTaskMemFree(pPropSet->rgProperties);
      CoTaskMemFree(pPropSet);

      if ((SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE)))
      {
         ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0,
                     sizeof(DWORD), DBTYPE_BYTES,
            0, 0, GUID_NULL, CAgentMan, dwBookmark,
                        DBCOLUMNFLAGS_ISBOOKMARK)
         ulCols++;
      }
   }

   // Next set the other columns up.
   ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Field1"), 1, 16, DBTYPE_STR,
          0xFF, 0xFF, GUID_NULL, CTextData, szField1)
   ulCols++;
   ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Field2"), 2, 16, DBTYPE_STR,
       0xFF, 0xFF, GUID_NULL, CTextData, szField2)
   ulCols++;

   if (pcCols != NULL)
      *pcCols = ulCols;

   return _rgColumns;
}

ATLCOLUMNINFO* CTextData::GetColumnInfo(CCustomCommand* pThis,
     ULONG* pcCols)
{
   return CommonGetColInfo<ICommandProperties>(pThis->GetUnknown(),
        pcCols);
}

ATLCOLUMNINFO* CAgentMan::GetColumnInfo(RUpdateRowset* pThis, ULONG* pcCols)
{
   return CommonGetColInfo<IRowsetInfo>(pThis->GetUnknown(), pcCols);
}
```

`GetColumnInfo` 는 먼저 라는 속성이 설정 되었는지 여부를 확인 `DBPROP_IRowsetLocate` 합니다. OLE DB에는 행 집합 개체의 각 선택적 인터페이스에 대 한 속성이 있습니다. 소비자가 이러한 선택적 인터페이스 중 하나를 사용 하려는 경우 속성을 true로 설정 합니다. 그런 다음 공급자는이 속성을 확인 하 고이 속성을 기반으로 특별 한 작업을 수행할 수 있습니다.

구현에서 명령 개체에 대 한 포인터를 사용 하 여 속성을 가져옵니다. `pThis`포인터는 행 집합 또는 명령 클래스를 나타냅니다. 여기에서 템플릿을 사용 하므로이를 **`void`** 포인터로 전달 하거나 코드가 컴파일되지 않습니다.

열 정보를 저장할 정적 배열을 지정 합니다. 소비자가 책갈피 열을 원하지 않는 경우 배열의 항목이 낭비 됩니다. 이 배열을 동적으로 할당할 수 있지만 제대로 소멸 해야 합니다. 이 예제에서는 매크로 ADD_COLUMN_ENTRY 및 ADD_COLUMN_ENTRY_EX를 사용 하 여 배열에 정보를 삽입 합니다. *사용자 지정* RS에 매크로를 추가할 수 있습니다. 다음 코드와 같이 H 파일을 표시 합니다.

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

#define ADD_COLUMN_ENTRY(ulCols, name, ordinal, colSize, type, precision, scale, guid, dataClass, member) \
   _rgColumns[ulCols].pwszName = (LPOLESTR)name; \
   _rgColumns[ulCols].pTypeInfo = (ITypeInfo*)NULL; \
   _rgColumns[ulCols].iOrdinal = (ULONG)ordinal; \
   _rgColumns[ulCols].dwFlags = 0; \
   _rgColumns[ulCols].ulColumnSize = (ULONG)colSize; \
   _rgColumns[ulCols].wType = (DBTYPE)type; \
   _rgColumns[ulCols].bPrecision = (BYTE)precision; \
   _rgColumns[ulCols].bScale = (BYTE)scale; \
   _rgColumns[ulCols].cbOffset = offsetof(dataClass, member);

#define ADD_COLUMN_ENTRY_EX(ulCols, name, ordinal, colSize, type, precision, scale, guid, dataClass, member, flags) \
   _rgColumns[ulCols].pwszName = (LPOLESTR)name; \
   _rgColumns[ulCols].pTypeInfo = (ITypeInfo*)NULL; \
   _rgColumns[ulCols].iOrdinal = (ULONG)ordinal; \
   _rgColumns[ulCols].dwFlags = flags; \
   _rgColumns[ulCols].ulColumnSize = (ULONG)colSize; \
   _rgColumns[ulCols].wType = (DBTYPE)type; \
   _rgColumns[ulCols].bPrecision = (BYTE)precision; \
   _rgColumns[ulCols].bScale = (BYTE)scale; \
   _rgColumns[ulCols].cbOffset = offsetof(dataClass, member); \
   memset(&(_rgColumns[ulCols].columnid), 0, sizeof(DBID)); \
   _rgColumns[ulCols].columnid.uName.pwszName = (LPOLESTR)name;
```

소비자의 코드를 테스트 하려면 처리기를 몇 가지 변경 해야 `OnRun` 합니다. 함수를 처음 변경 하면 속성 집합에 속성을 추가 하는 코드를 추가 하는 것입니다. 이 코드는 속성을 true로 설정 하 여 `DBPROP_IRowsetLocate` 책갈피 열을 제공 하도록 공급자에 게 지시 합니다. 처리기 코드는 다음과 같이 `OnRun` 표시 되어야 합니다.

```cpp
//////////////////////////////////////////////////////////////////////
// TestProv Consumer Application in TestProvDlg.cpp

void CTestProvDlg::OnRun()
{
   CCommand<CAccessor<CProvider>> table;
   CDataSource source;
   CSession   session;

   if (source.Open("Custom.Custom.1", NULL, NULL, NULL,
          NULL) != S_OK)
      return;

   if (session.Open(source) != S_OK)
      return;

   CDBPropSet propset(DBPROPSET_ROWSET);
   propset.AddProperty(DBPROP_IRowsetLocate, true);
   if (table.Open(session, _T("c:\\public\\testprf2\\myData.txt"),
          &propset) != S_OK)
      return;

   CBookmark<4> tempBookmark;
   ULONG ulCount=0;
   while (table.MoveNext() == S_OK)
   {

      DBCOMPARE compare;
      if (ulCount == 2)
         tempBookmark = table.bookmark;

HRESULT hr = table.Compare(table.dwBookmark, table.dwBookmark,
                 &compare);
      if (FAILED(hr))
         ATLTRACE(_T("Compare failed: 0x%X\n"), hr);
      else
         _ASSERTE(compare == DBCOMPARE_EQ);

      m_ctlString1.AddString(table.szField1);
      m_ctlString2.AddString(table.szField2);
      ulCount++;
   }

   table.MoveToBookmark(tempBookmark);
   m_ctlString1.AddString(table.szField1);
   m_ctlString2.AddString(table.szField2);
}
```

루프에는 **`while`** `Compare` 인터페이스에서 메서드를 호출 하는 코드가 포함 되어 있습니다 `IRowsetLocate` . 정확히 동일한 책갈피를 비교 하 고 있으므로 항상 코드를 전달 해야 합니다. 또한 **`while`** 루프가 종료 된 후 소비자 템플릿에서 함수를 호출 하는 데 사용할 수 있도록 임시 변수에 하나의 책갈피를 저장 `MoveToBookmark` 합니다. `MoveToBookmark`함수는에서 메서드를 호출 합니다 `GetRowsAt` `IRowsetLocate` .

또한 소비자의 사용자 레코드를 업데이트 해야 합니다. 클래스에 항목을 추가 하 여 COLUMN_MAP에서 책갈피와 항목을 처리 합니다.

```cpp
///////////////////////////////////////////////////////////////////////
// TestProvDlg.cpp

class CProvider
{
// Attributes
public:
   CBookmark<4>    bookmark;  // Add this line
   char   szCommand[16];
   char   szText[256];

   // Binding Maps
BEGIN_ACCESSOR_MAP(CProvider, 1)
   BEGIN_ACCESSOR(0, true)   // auto accessor
      BOOKMARK_ENTRY(bookmark)  // Add this line
      COLUMN_ENTRY(1, szField1)
      COLUMN_ENTRY(2, szField2)
   END_ACCESSOR()
END_ACCESSOR_MAP()
};
```

코드를 업데이트 한 후에는 인터페이스를 사용 하 여 공급자를 빌드하고 실행할 수 있어야 합니다 `IRowsetLocate` .

## <a name="see-also"></a>참고 항목

[고급 공급자 기술](../../data/oledb/advanced-provider-techniques.md)
