---
description: '자세히 알아보기: CDaoTableDefInfo Structure'
title: CDaoTableDefInfo 구조체
ms.date: 11/04/2016
f1_keywords:
- CDaoTableDefInfo
helpviewer_keywords:
- CDaoTableDefInfo structure [MFC]
- DAO (Data Access Objects), TableDefs collection
ms.assetid: c01ccebb-5615-434e-883c-4f60eac943dd
ms.openlocfilehash: 953a255b35860dcce0ac8d3ef5081951dd15c344
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247971"
---
# <a name="cdaotabledefinfo-structure"></a>CDaoTableDefInfo 구조체

구조에는 `CDaoTableDefInfo` DAO (data access objects)에 대해 정의 된 테이블 정의 개체에 대 한 정보가 포함 되어 있습니다.

## <a name="syntax"></a>구문

```
struct CDaoTableDefInfo
{
    CString m_strName;               // Primary
    BOOL m_bUpdatable;               // Primary
    long m_lAttributes;              // Primary
    COleDateTime m_dateCreated;      // Secondary
    COleDateTime m_dateLastUpdated;  // Secondary
    CString m_strSrcTableName;       // Secondary
    CString m_strConnect;            // Secondary
    CString m_strValidationRule;     // All
    CString m_strValidationText;     // All
    long m_lRecordCount;             // All
};
```

#### <a name="parameters"></a>매개 변수

*m_strName*<br/>
테이블 정의 개체의 이름을 고유 하 게 정의 합니다. 이 속성의 값을 직접 검색 하려면 tabledef 개체의 [GetName](../../mfc/reference/cdaotabledef-class.md#getname) 멤버 함수를 호출 합니다. 자세한 내용은 DAO 도움말의 "이름 속성" 항목을 참조 하십시오.

*m_bUpdatable*<br/>
테이블에 대 한 변경 내용을 적용할 수 있는지 여부를 나타냅니다. 테이블을 업데이트할 수 있는지 여부를 확인 하는 빠른 방법은 테이블의 `CDaoTableDef` 개체를 열고 개체의 [CanUpdate](../../mfc/reference/cdaotabledef-class.md#canupdate) 멤버 함수를 호출 하는 것입니다. `CanUpdate` 는 새로 만든 테이블 정의 개체에 대해 0이 아닌 값 (TRUE)을 반환 하 고 연결 된 테이블 정의 개체에 대해 0 (FALSE)을 반환 합니다. 새 테이블 정의 개체는 현재 사용자에 게 쓰기 권한이 있는 데이터베이스에만 추가할 수 있습니다. 테이블에 nonupdatable 필드만 포함 되어 있으면는 `CanUpdate` 0을 반환 합니다. 하나 이상의 필드를 업데이트할 수 있는 경우는 `CanUpdate` 0이 아닌 값을 반환 합니다. 업데이트 가능한 필드만 편집할 수 있습니다. 자세한 내용은 DAO 도움말의 "업데이트할 수 있는 속성" 항목을 참조 하십시오.

*m_lAttributes*<br/>
테이블 정의 개체로 표시 되는 테이블의 특성을 지정 합니다. 테이블 형식의 현재 특성을 검색 하려면 해당 [getattributes](../../mfc/reference/cdaotabledef-class.md#getattributes) 멤버 함수를 호출 합니다. 반환 되는 값은 이러한 긴 상수 (비트 or (**&#124;**) 연산자 사용)의 조합일 수 있습니다.

- `dbAttachExclusive` Microsoft Jet 데이터베이스 엔진을 사용 하는 데이터베이스의 경우 테이블은 단독으로 사용 하기 위해 열린 연결 된 테이블 임을 나타냅니다.

- `dbAttachSavePWD` Microsoft Jet 데이터베이스 엔진을 사용 하는 데이터베이스의 경우 연결 된 테이블의 사용자 ID와 암호가 연결 정보로 저장 됨을 나타냅니다.

- `dbSystemObject` 테이블이 Microsoft Jet 데이터베이스 엔진에서 제공 하는 시스템 테이블 임을 나타냅니다. 읽기 전용입니다.

- `dbHiddenObject` 테이블이 Microsoft Jet 데이터베이스 엔진에서 임시 사용을 위해 제공 하는 숨겨진 테이블 임을 나타냅니다. 읽기 전용입니다.

- `dbAttachedTable` 테이블은 Paradox 데이터베이스와 같은 비 ODBC 데이터베이스에서 연결 된 테이블 임을 나타냅니다.

- `dbAttachedODBC` 테이블이 ODBC 데이터베이스에서 연결 된 테이블 임을 나타냅니다 (예: Microsoft SQL Server).

*m_dateCreated*<br/>
테이블을 만든 날짜와 시간입니다. 테이블이 생성 된 날짜를 직접 검색 하려면 해당 테이블과 연결 된 개체의 [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated) 멤버 함수를 호출 합니다 `CDaoTableDef` . 자세한 내용은 아래 주석을 참조 하세요. 관련 내용은 DAO 도움말에서 "DateCreated, LastUpdated 속성" 항목을 참조 하십시오.

*m_dateLastUpdated*<br/>
테이블 디자인에 대해 가장 최근에 변경한 날짜와 시간입니다. 테이블이 마지막으로 업데이트 된 날짜를 직접 검색 하려면 해당 테이블과 연결 된 개체의 [GetDateLastUpdated](../../mfc/reference/cdaotabledef-class.md#getdatelastupdated) 멤버 함수를 호출 합니다 `CDaoTableDef` . 자세한 내용은 아래 주석을 참조 하세요. 관련 내용은 DAO 도움말에서 "DateCreated, LastUpdated 속성" 항목을 참조 하십시오.

*m_strSrcTableName*<br/>
연결 된 테이블의 이름을 지정 합니다 (있는 경우). 원본 테이블 이름을 직접 검색 하려면 테이블에 연결 된 개체의 [Getsourcetablename](../../mfc/reference/cdaotabledef-class.md#getsourcetablename) 멤버 함수를 호출 합니다 `CDaoTableDef` .

*m_strConnect*<br/>
열려 있는 데이터베이스의 원본에 대 한 정보를 제공 합니다. 개체의 [Getconnect](../../mfc/reference/cdaotabledef-class.md#getconnect) 멤버 함수를 호출 하 여이 속성을 확인할 수 있습니다 `CDaoTableDef` . 연결 문자열에 대 한 자세한 내용은을 참조 하십시오 `GetConnect` .

*m_strValidationRule*<br/>
테이블에 변경 되거나 추가 될 때 테이블 정의 필드에서 데이터의 유효성을 검사 하는 값입니다. 유효성 검사는 Microsoft Jet 데이터베이스 엔진을 사용 하는 데이터베이스에 대해서만 지원 됩니다. 유효성 검사 규칙을 직접 검색 하려면 테이블과 연결 된 개체의 [Getvalidationrule](../../mfc/reference/cdaotabledef-class.md#getvalidationrule) 멤버 함수를 호출 합니다 `CDaoTableDef` . 관련 내용은 DAO 도움말의 "ValidationRule 속성" 항목을 참조 하십시오.

*m_strValidationText*<br/>
ValidationRule 속성에 지정 된 유효성 검사 규칙이 충족 되지 않는 경우 응용 프로그램에서 표시 해야 하는 메시지의 텍스트를 지정 하는 값입니다. 관련 내용은 DAO 도움말의 "ValidationText 속성" 항목을 참조 하십시오.

*m_lRecordCount*<br/>
테이블 정의 개체에서 액세스 하는 레코드 수입니다. 이 속성 설정은 읽기 전용입니다. 레코드 수를 직접 검색 하려면 개체의 [Getrecordcount](../../mfc/reference/cdaotabledef-class.md#getrecordcount) 멤버 함수를 호출 합니다 `CDaoTableDef` . 에 대 한 설명서에서는 `GetRecordCount` 레코드 수를 추가로 설명 합니다. 테이블에 여러 레코드가 포함 된 경우이 개수를 검색 하는 작업은 시간이 오래 걸릴 수 있습니다.

## <a name="remarks"></a>설명

테이블 정의는 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)클래스의 개체입니다. 위의 기본, 보조 및 모든에 대 한 참조는 클래스의 [GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo) 멤버 함수에서 정보를 반환 하는 방법을 표시 합니다 `CDaoDatabase` .

[CDaoDatabase:: GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo) 멤버 함수에서 검색 된 정보는 구조체에 저장 됩니다 `CDaoTableDefInfo` . `GetTableDefInfo` `CDaoDatabase` 테이블 정의 개체를 저장 하는 테이블 형식의 개체에 대 한 멤버 함수를 호출 합니다. `CDaoTableDefInfo` 또한 `Dump` 디버그 빌드에서 멤버 함수를 정의 합니다. `Dump`를 사용 하 여 개체의 콘텐츠를 덤프할 수 있습니다 `CDaoTableDefInfo` .

날짜 및 시간 설정은 기본 테이블이 만들어지거나 마지막으로 업데이트 된 컴퓨터에서 파생 됩니다. 다중 사용자 환경에서는 DateCreated 및 LastUpdated 속성 설정의 불일치를 방지 하기 위해 사용자가 파일 서버에서 이러한 설정을 직접 가져와야 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="see-also"></a>참고 항목

[구조체, 스타일, 콜백 및 메시지 맵](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef 클래스](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoDatabase 클래스](../../mfc/reference/cdaodatabase-class.md)
