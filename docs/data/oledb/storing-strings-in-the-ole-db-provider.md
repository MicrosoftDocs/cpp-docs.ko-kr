---
description: '자세한 정보: OLE DB 공급자에 문자열 저장'
title: OLE DB 공급자에 문자열 저장
ms.date: 05/09/2019
helpviewer_keywords:
- user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
ms.openlocfilehash: d5a0fc7160f09d1a8b385b83481cc6fa9009f582
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316702"
---
# <a name="storing-strings-in-the-ole-db-provider"></a>OLE DB 공급자에 문자열 저장

> [!NOTE]
> Visual Studio 2019 이상에서는 ATL OLE DB 공급자 마법사를 사용할 수 없습니다.

**ATL OLE DB 공급자 마법사** 는 *Custom* RS.h에 `CWindowsFile`이라는 기본 사용자 레코드를 만듭니다. 두 문자열을 처리하려면 다음 코드와 같이 `CWindowsFile`을 수정합니다.

```cpp
////////////////////////////////////////////////////////////////////////
class CCustomWindowsFile:
   public WIN32_FIND_DATA
{
public:
DWORD dwBookmark;
static const int iSize = 256;    // Add this
TCHAR szCommand[iSize];          // Add this
TCHAR szText[iSize];             // Add this
TCHAR szCommand2[iSize];         // Add this
TCHAR szText2[iSize];            // Add this

BEGIN_PROVIDER_COLUMN_MAP(CCustomWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)

   PROVIDER_COLUMN_ENTRY_STR("Command", 6, szCommand)    // Add this
   PROVIDER_COLUMN_ENTRY_STR("Text", 7, szText)          // Add this
   PROVIDER_COLUMN_ENTRY_STR("Command2", 8, szCommand2)  // Add this
   PROVIDER_COLUMN_ENTRY_STR("Text2", 9, szText2)        // Add this
END_PROVIDER_COLUMN_MAP()

   bool operator==(const CCustomWindowsFile& am) // This is optional
   {
      return (lstrcmpi(cFileName, am.cFileName) == 0);
   }
};
```

데이터 멤버 `szCommand` 및 `szText`는 `szCommand2` 및 `szText2`와 필요한 경우 추가 열을 사용하여 두 문자열을 나타냅니다. 데이터 멤버 `dwBookmark`는 이 단순한 읽기 전용 공급자에는 필요하지 않지만, 나중에 `IRowsetLocate` 인터페이스를 추가하는 데 사용됩니다. [단순한 읽기 전용 공급자의 기능 향상](../../data/oledb/enhancing-the-simple-read-only-provider.md)을 참조하세요. `==` 연산자는 인스턴스를 비교합니다(이 연산자 구현은 선택 사항임).

이 작업이 완료되면, [OLE DB 공급자로 문자열 읽어들이기](../../data/oledb/reading-strings-into-the-ole-db-provider.md)의 기능을 추가할 수 있습니다.

## <a name="see-also"></a>참고 항목

[간단한 Read-Only 공급자 구현](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
