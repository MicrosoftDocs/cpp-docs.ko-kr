---
title: CODBCFieldInfo 구조체 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CODBCFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- ODBC [MFC], data source information
- CODBCFieldInfo structure [MFC]
ms.assetid: 92598b4f-facc-4108-b282-63a179ff79ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 797a229007be58ff3da3bb529c9e8f4a062c12b3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434312"
---
# <a name="codbcfieldinfo-structure"></a>CODBCFieldInfo 구조체

`CODBCFieldInfo` 구조 ODBC 데이터 소스에서 필드에 대 한 정보가 들어 있습니다.

## <a name="syntax"></a>구문

```
struct CODBCFieldInfo
{
    CString m_strName;
    SWORD m_nSQLType;
    UDWORD m_nPrecision;
    SWORD m_nScale;
    SWORD m_nNullability;
};
```

#### <a name="parameters"></a>매개 변수

*m_strName*<br/>
@FSHO2@필드의 이름입니다.

*m_nSQLType*<br/>
필드의 SQL 데이터 형식입니다. 이 ODBC SQL 데이터 형식 또는 드라이버별 SQL 데이터 형식 수 있습니다. 유효한 ODBC SQL 데이터 형식의 목록, Windows SDK의 "SQL 데이터 형식"을 참조 하세요. 드라이버별 SQL 데이터 형식에 대 한 내용은 드라이버의 설명서를 참조 하십시오.

*m_nPrecision*<br/>
필드의 최대 전체 자릿수입니다. 자세한 내용은 Windows SDK의 "정밀도, 배율, 길이 및 표시 크기"를 참조 합니다.

*m_nScale*<br/>
필드의 소수 자릿수입니다. 자세한 내용은 Windows SDK의 "정밀도, 배율, 길이 및 표시 크기"를 참조 합니다.

*m_nNullability*<br/>
여부를 필드에 Null 값을 허용 합니다. 두 값 중 하나일 수 있습니다: SQL_NULLABLE SQL_NO_NULLS 필드를 허용 하지 않는 경우 Null 값 또는 필드에 Null 값을 허용 하는 경우.

## <a name="remarks"></a>설명

이 정보를 검색 하려면 호출 [CRecordset::GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo)합니다.

## <a name="requirements"></a>요구 사항

**헤더:** afxdb.h

## <a name="see-also"></a>참고 항목

[구조체, 스타일, 콜백 및 메시지 맵](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CRecordset::GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo)<br/>
[CRecordset::GetFieldValue](../../mfc/reference/crecordset-class.md#getfieldvalue)


