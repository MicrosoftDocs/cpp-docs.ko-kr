---
description: '다음에 대 한 자세한 정보: CODBCFieldInfo 구조체'
title: CODBCFieldInfo 구조체
ms.date: 11/04/2016
f1_keywords:
- CODBCFieldInfo
helpviewer_keywords:
- ODBC [MFC], data source information
- CODBCFieldInfo structure [MFC]
ms.assetid: 92598b4f-facc-4108-b282-63a179ff79ab
ms.openlocfilehash: 7cd7072719bec46cfbfaeb02c5c86d714c4de13c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331419"
---
# <a name="codbcfieldinfo-structure"></a>CODBCFieldInfo 구조체

구조에는 `CODBCFieldInfo` ODBC 데이터 원본의 필드에 대 한 정보가 포함 되어 있습니다.

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
필드의 이름입니다.

*m_nSQLType*<br/>
필드의 SQL 데이터 형식입니다. ODBC SQL 데이터 형식 또는 드라이버별 SQL 데이터 형식일 수 있습니다. 유효한 ODBC SQL 데이터 형식 목록은 Windows SDK의 "SQL 데이터 형식"을 참조 하십시오. 드라이버별 SQL 데이터 형식에 대 한 자세한 내용은 드라이버 설명서를 참조 하십시오.

*m_nPrecision*<br/>
필드의 최대 전체 자릿수입니다. 자세한 내용은 Windows SDK의 "전체 자릿수, 소수 자릿수, 길이 및 표시 크기"를 참조 하십시오.

*m_nScale*<br/>
필드의 소수 자릿수입니다. 자세한 내용은 Windows SDK의 "전체 자릿수, 소수 자릿수, 길이 및 표시 크기"를 참조 하십시오.

*m_nNullability*<br/>
필드에 Null 값이 허용 되는지 여부를 나타냅니다. 이 값은 두 값 중 하나일 수 있습니다. 필드에 Null 값이 허용 되는 경우 SQL_NULLABLE이 고, 필드에 Null 값이 허용 되지 않는 경우 SQL_NO_NULLS입니다.

## <a name="remarks"></a>설명

이 정보를 검색 하려면 [CRecordset:: GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo)를 호출 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="see-also"></a>참고 항목

[구조체, 스타일, 콜백 및 메시지 맵](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CRecordset:: GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo)<br/>
[CRecordset:: GetFieldValue](../../mfc/reference/crecordset-class.md#getfieldvalue)
