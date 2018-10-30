---
title: OLE DB 공급자로 문자열 읽어들이기 | Microsoft Docs
ms.custom: ''
ms.date: 10/13/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, reading strings into
ms.assetid: 517f322c-f37e-4eed-bf5e-dd9a412c2f98
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b1730c839ab2eb87511a241c28409646a999cfd6
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216255"
---
# <a name="reading-strings-into-the-ole-db-provider"></a>OLE DB 공급자로 문자열 읽어들이기

`RCustomRowset::Execute` 함수 파일을 열고 문자열을 읽습니다. 소비자를 호출 하 여 공급자에 게 파일 이름을 전달 [icommandtext:: Setcommandtext](/previous-versions/windows/desktop/ms709757)합니다. 공급자 파일 이름을 받고 멤버 변수에 저장 `m_szCommandText`합니다. `Execute` 파일 이름을 읽고 `m_szCommandText`합니다. 파일 이름이 잘못 되었거나 파일을 사용할 수 없는 경우 `Execute` 오류를 반환 합니다. 을 열고 파일 및 호출 `fgets` 문자열을 검색 합니다. 각 설정 문자열의 읽기에 대 한 `Execute` 사용자 레코드의 인스턴스를 만듭니다 (`CAgentMan`) 배열에 넣습니다.

파일을 열 수 없는 경우 `Execute` DB_E_NOTABLE 반환 해야 합니다. E_FAIL을 대신 반환 하는 경우 공급자를 많은 소비자와 함께 작동 하지 않습니다 하 고 OLE DB를 전달 하지 않습니다 [적합성 테스트](../../data/oledb/testing-your-provider.md)합니다.

## <a name="example"></a>예제

```cpp
/////////////////////////////////////////////////////////////////////////
// CustomRS.h
class RCustomRowset : public CRowsetImpl< RCustomRowset, CAgentMan, CRCustomCommand>
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
        size_t nLength;        errcodeerr;

        ObjectLock lock(this);

        // From a filename, passed in as a command text, scan the file
        // placing data in the data array.
        if (!m_szCommandText)
        {
            ATLTRACE("No filename specified");
            return E_FAIL;
        }

        // Open the file
        _tcscpy_s(szFile, sizeOfFile, m_szCommandText);
        if (szFile[0] == _T('\0') ||
            ((err = fopen_s(&pFile, &szFile[0], "r")) == 0))
        {
            ATLTRACE("Could not open file");
            return DB_E_NOTABLE;
        }

        // Scan and parse the file.
        // The file should contain two strings per record
        LONG cFiles = 0;
        while (fgets(szString, sizeOfBuffer, pFile) != NULL)
        {
            nLength = strnlen(szString, sizeOfBuffer);
            szString[nLength-1] = '\0';   // Strip off trailing CR/LF
            CAgentMan am;
            _tcscpy_s(am.szCommand, am.sizeOfCommand, szString);
            _tcscpy_s(am.szCommand2, am.sizeOfCommand2, szString);

            if (fgets(szString, sizeOfBuffer, pFile) != NULL)
            {
                nLength = strnlen(szString, sizeOfBuffer);
                szString[nLength-1] = '\0'; // Strip off trailing CR/LF
                _tcscpy_s(am.szText, am.sizeOfText, szString);
                _tcscpy_s(am.szText2, am.sizeOfText2, szString);
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
}
```

## <a name="see-also"></a>참고 항목

[단순한 읽기 전용 공급자 구현](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
