---
description: '자세한 정보: CCustomWindowsFile'
title: CCustomWindowsFile
ms.date: 10/22/2018
f1_keywords:
- cmyproviderwindowsfile
- ccustomwindowsfile
helpviewer_keywords:
- CMyProviderWindowsFile class
- OLE DB providers, wizard-generated files
- CCustomWindowsFile class
ms.assetid: 0e9e72ac-1e1e-445f-a7ac-690c20031f9d
ms.openlocfilehash: c0df2840b68a350f9d65102fdf0a962681edefd9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170401"
---
# <a name="ccustomwindowsfile"></a>CCustomWindowsFile

마법사는 데이터 행이 하나 있는 클래스를 만듭니다. 이 경우 호출 `CCustomWindowsFile` 됩니다. 에 대 한 다음 코드는 `CCustomWindowsFile` 마법사에서 생성 되며 구조를 사용 하 여 디렉터리의 모든 파일을 나열 합니다 `WIN32_FIND_DATA` . `CCustomWindowsFile` 구조체에서 상속 됩니다 `WIN32_FIND_DATA` .

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H

class CCustomWindowsFile:
   public WIN32_FIND_DATA
{
public:
BEGIN_PROVIDER_COLUMN_MAP(CCustomWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)
END_PROVIDER_COLUMN_MAP()
};
```

`CCustomWindowsFile` 는 공급자의 행 집합에 있는 열을 설명 하는 맵도 있으므로 [사용자 레코드 클래스](../../data/oledb/user-record.md) 라고 합니다. 공급자 열 맵은 PROVIDER_COLUMN_ENTRY 매크로를 사용 하 여 행 집합의 각 필드에 대 한 하나의 항목을 포함 합니다. 매크로는 열 이름, 서 수 및 구조체 항목에 대 한 오프셋을 지정 합니다. 위의 코드에서 공급자 열 항목에는 구조체로의 오프셋이 포함 `WIN32_FIND_DATA` 됩니다. 소비자가를 호출 하면 `IRowset::GetData` 하나의 연속 된 버퍼로 데이터가 전송 됩니다. 지도를 사용 하 여 포인터 산술 연산을 수행 하는 대신 데이터 멤버를 지정할 수 있습니다.

`CCustomRowset`클래스에도 메서드가 포함 되어 있습니다 `Execute` . `Execute` 는 실제로 네이티브 소스에서 데이터를 읽는 것입니다. 다음 코드는 마법사에서 생성 된 메서드를 보여 줍니다 `Execute` . 함수는 Win32 `FindFirstFile` 및 `FindNextFile` api를 사용 하 여 디렉터리에 있는 파일에 대 한 정보를 검색 하 고 클래스의 인스턴스에 넣습니다 `CCustomWindowsFile` .

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H

HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)
{
   USES_CONVERSION;
   BOOL bFound = FALSE;
   HANDLE hFile;
   LPTSTR  szDir = (m_strCommandText == _T("")) ? _T("*.*") :
       OLE2T(m_strCommandText);
   CCustomWindowsFile wf;
   hFile = FindFirstFile(szDir, &wf);
   if (hFile == INVALID_HANDLE_VALUE)
      return DB_E_ERRORSINCOMMAND;
   LONG cFiles = 1;
   BOOL bMoreFiles = TRUE;
   while (bMoreFiles)
   {
      if (!m_rgRowData.Add(wf))
         return E_OUTOFMEMORY;
      bMoreFiles = FindNextFile(hFile, &wf);
      cFiles++;
   }
   FindClose(hFile);
   if (pcRowsAffected != NULL)
      *pcRowsAffected = cFiles;
   return S_OK;
}
```

검색할 디렉터리는로 표시 됩니다. `m_strCommandText` 여기에는 `ICommandText` command 개체의 인터페이스에서 나타내는 텍스트가 포함 됩니다. 디렉터리가 지정 되지 않은 경우 현재 디렉터리를 사용 합니다.

메서드는 각 파일 (행에 해당)에 대해 하나의 항목을 만들어 데이터 멤버에 배치 `m_rgRowData` 합니다. `CRowsetImpl`클래스는 데이터 멤버를 정의 합니다 `m_rgRowData` . 이 배열의 데이터는 전체 테이블에 표시 되며 템플릿 전체에서 사용 됩니다.

## <a name="see-also"></a>참고 항목

[공급자 Wizard-Generated 파일](../../data/oledb/provider-wizard-generated-files.md)<br/>
