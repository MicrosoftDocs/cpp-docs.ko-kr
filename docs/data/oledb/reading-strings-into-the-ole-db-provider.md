---
description: '자세한 정보: 문자열을 OLE DB 공급자로 읽기'
title: OLE DB 공급자로 문자열 읽어들이기
ms.date: 10/13/2018
helpviewer_keywords:
- OLE DB providers, reading strings into
ms.assetid: 517f322c-f37e-4eed-bf5e-dd9a412c2f98
ms.openlocfilehash: 5df8812d5589dd457684bf5e36a8a49f798f99aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286633"
---
# <a name="reading-strings-into-the-ole-db-provider"></a>OLE DB 공급자로 문자열 읽어들이기

`CCustomRowset::Execute`함수는 파일을 열고 문자열을 읽습니다. 소비자는 [ICommandText:: SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85))를 호출 하 여 파일 이름을 공급자에 게 전달 합니다. 공급자는 파일 이름을 받아서 멤버 변수에 저장 합니다 `m_strCommandText` . `Execute` 에서 파일 이름을 읽습니다 `m_strCommandText` . 파일 이름이 잘못 되었거나 파일을 사용할 수 없는 경우에서 `Execute` 오류를 반환 합니다. 그렇지 않으면 파일을 열고 `fgets` 를 호출 하 여 문자열을 검색 합니다. 는 읽을 각 문자열 집합에 대해 `Execute` 사용자 레코드의 인스턴스를 만들고 ( `CCustomWindowsFile` [OLE DB 공급자의 문자열 저장](../../data/oledb/storing-strings-in-the-ole-db-provider.md)에서 수정) 배열에 배치 합니다.

파일을 열 수 없는 경우는 `Execute` DB_E_NOTABLE을 반환 해야 합니다. 대신 E_FAIL을 반환 하는 경우 공급자는 많은 소비자와 작동 하지 않으며 OLE DB [규칙 테스트](../../data/oledb/testing-your-provider.md)를 통과 하지 못합니다.

## <a name="example"></a>예제

```cpp
/////////////////////////////////////////////////////////////////////////
// CustomRS.h
class CCustomRowset : public CRowsetImpl< CCustomRowset, CCustomWindowsFile, CCustomCommand>
{
public:
    HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)
    {
        enum {
            sizeOfBuffer = 256,
            sizeOfFile = MAX_PATH
        };
        USES_CONVERSION;
        FILE* pFile = NULL;
        TCHAR szString[sizeOfBuffer];
        TCHAR szFile[sizeOfFile];
        size_t nLength;

        ObjectLock lock(this);

        // From a filename, passed in as a command text, scan the file
        // placing data in the data array.
        if (!m_strCommandText)
        {
            ATLTRACE("No filename specified");
            return E_FAIL;
        }

        // Open the file
        _tcscpy_s(szFile, sizeOfFile, m_strCommandText);
        if (szFile[0] == _T('\0') ||
            (fopen_s(&pFile, (char*)&szFile[0], "r") == 0))
        {
            ATLTRACE("Could not open file");
            return DB_E_NOTABLE;
        }

        // Scan and parse the file.
        // The file should contain two strings per record
        LONG cFiles = 0;
        while (fgets((char*)szString, sizeOfBuffer, pFile) != NULL)
        {
            nLength = strnlen((char*)szString, sizeOfBuffer);
            szString[nLength-1] = '\0';   // Strip off trailing CR/LF
            CCustomWindowsFile am;
            _tcscpy_s(am.szCommand, am.iSize, szString);
            _tcscpy_s(am.szCommand2, am.iSize, szString);

            if (fgets((char*)szString, sizeOfBuffer, pFile) != NULL)
            {
                nLength = strnlen((char*)szString, sizeOfBuffer);
                szString[nLength-1] = '\0'; // Strip off trailing CR/LF
                _tcscpy_s(am.szText, am.iSize, szString);
                _tcscpy_s(am.szText2, am.iSize, szString);
            }

            am.dwBookmark = ++cFiles;
            if (!m_rgRowData.Add(am))
            {
                ATLTRACE("Couldn't add data to array");
                fclose(pFile);
                return E_FAIL;
            }
        }

        if (pcRowsAffected != NULL)
            *pcRowsAffected = cFiles;
        return S_OK;
    }
};
```

이 작업이 완료 되 면 공급자를 컴파일하고 실행할 준비가 된 것입니다. 공급자를 테스트 하려면 일치 하는 기능이 있는 소비자가 필요 합니다. [간단한 소비자를 구현](../../data/oledb/implementing-a-simple-consumer.md) 하면 이러한 테스트 소비자를 만드는 방법을 보여 줍니다. 공급자를 사용 하 여 테스트 소비자를 실행 하 고 테스트 소비자가 공급자에서 적절 한 문자열을 검색 하는지 확인 합니다.

공급자를 성공적으로 테스트 한 경우 추가 인터페이스를 구현 하 여 기능을 향상 시킬 수 있습니다. 예제는 [간단한 Read-Only 공급자를 향상 시키는](../../data/oledb/enhancing-the-simple-read-only-provider.md)방법을 보여 줍니다.

## <a name="see-also"></a>참고 항목

[간단한 Read-Only 공급자 구현](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
