---
description: '자세히 알아보기: CDaoFieldInfo Structure'
title: CDaoFieldInfo 구조체
ms.date: 09/17/2019
f1_keywords:
- CDaoFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure [MFC]
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
ms.openlocfilehash: 8cb297e767fed023ff7b6c2fe7efe5dd41a1621a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250870"
---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo 구조체

구조에는 `CDaoFieldInfo` DAO (data access objects)에 대해 정의 된 필드 개체에 대 한 정보가 포함 되어 있습니다.

DAO는 Office 2013을 통해 지원 됩니다. DAO 3.6은 최종 버전이 며 사용 되지 않는 것으로 간주 됩니다.

## <a name="syntax"></a>구문

```
struct CDaoFieldInfo
{
    CString m_strName;           // Primary
    short m_nType;               // Primary
    long m_lSize;                // Primary
    long m_lAttributes;          // Primary
    short m_nOrdinalPosition;    // Secondary
    BOOL m_bRequired;            // Secondary
    BOOL m_bAllowZeroLength;     // Secondary
    long m_lCollatingOrder;      // Secondary
    CString m_strForeignName;    // Secondary
    CString m_strSourceField;    // Secondary
    CString m_strSourceTable;    // Secondary
    CString m_strValidationRule; // All
    CString m_strValidationText; // All
    CString m_strDefaultValue;   // All
};
```

#### <a name="parameters"></a>매개 변수

*m_strName*<br/>
필드 개체의 이름을 고유 하 게 합니다. 자세한 내용은 DAO 도움말의 "이름 속성" 항목을 참조 하십시오.

*m_nType*<br/>
필드의 데이터 형식을 나타내는 값입니다. 자세한 내용은 DAO 도움말의 "형식 속성" 항목을 참조 하십시오. 이 속성의 값은 다음 중 하나일 수 있습니다.

- `dbBoolean` 예/아니요, TRUE/FALSE와 동일 합니다.

- `dbByte` 바이트만

- `dbInteger` 간략히

- `dbLong` 시간과

- `dbCurrency`최신 MFC 클래스 [COleCurrency](../../mfc/reference/colecurrency-class.md) 를 참조 하세요.

- `dbSingle` 단

- `dbDouble` 차례로

- `dbDate`날짜/시간; MFC 클래스 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 를 참조 하세요.

- `dbText`본문 MFC 클래스 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 참조

- `dbLongBinary` Long Binary (OLE 개체); `CByteArray`보다 풍부하고 사용하기 쉬운 `CLongBinary`클래스 대신 MFC 클래스 [CByteArray](../../mfc/reference/cbytearray-class.md)를 사용하는 것이 좋습니다.

- `dbMemo` Memo MFC 클래스 참조 `CString`

- `dbGUID` 원격 프로시저 호출에 사용 되는 전역적으로 고유한 식별자/범용 고유 식별자입니다. 자세한 내용은 DAO 도움말의 "형식 속성" 항목을 참조 하십시오.

> [!NOTE]
> 이진 데이터에는 문자열 데이터 형식을 사용 하지 마십시오. 이렇게 하면 데이터가 유니코드/ANSI 변환 계층을 통과 하 여 오버 헤드가 증가 하 고 예기치 않은 번역이 발생할 수 있습니다.

*m_lSize*<br/>
텍스트 또는 숫자 값을 포함 하는 필드 개체의 고정 크기를 포함 하는 DAO field 개체의 최대 크기 (바이트)를 나타내는 값입니다. 자세한 내용은 DAO 도움말의 "크기 속성" 항목을 참조 하십시오. 크기는 다음 값 중 하나일 수 있습니다.

|형식|크기(바이트)|설명|
|----------|--------------------|-----------------|
|`dbBoolean`|1바이트|예/아니요 (True/False와 동일)|
|`dbByte`|1|Byte|
|`dbInteger`|2|정수|
|`dbLong`|4|long|
|`dbCurrency`|8|통화 ([COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|Single|
|`dbDouble`|8|Double|
|`dbDate`|8|날짜/시간 ([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|텍스트 ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Long Binary (OLE 개체; [CByteArray](../../mfc/reference/cbytearray-class.md); 대신 사용 `CLongBinary` )|
|`dbMemo`|0|메모 ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbGUID`|16|원격 프로시저 호출에 사용 되는 전역적으로 고유한 식별자/범용 고유 식별자입니다.|

*m_lAttributes*<br/>
테이블 정의, 레코드 집합, 쿼리 정의 또는 인덱스 개체에 포함 된 field 개체의 특성을 지정 합니다. 반환 되는 값은 c + + 비트 or (**&#124;**) 연산자를 사용 하 여 만든 이러한 상수의 합계 일 수 있습니다.

- `dbFixedField` 필드 크기가 고정 되어 있습니다 (숫자 필드의 경우 기본값).

- `dbVariableField` 필드 크기가 variable (텍스트 필드에만 해당)입니다.

- `dbAutoIncrField` 새 레코드에 대 한 필드 값이 자동으로 변경 될 수 없는 고유한 정수 (long)로 증가 합니다. Microsoft Jet 데이터베이스 테이블에만 지원 됩니다.

- `dbUpdatableField` 필드 값을 변경할 수 있습니다.

- `dbDescending` 필드는 내림차순 (Z-A 또는 100-0) 순서로 정렬 됩니다. index 개체의 Fields 컬렉션에 있는 field 개체에만 적용 됩니다. MFC에서는 인덱스 개체가 테이블 정의 개체에 포함 됩니다. 이 상수를 생략 하면 필드가 오름차순 (a-z 또는 0-100) 순서 (기본값)로 정렬 됩니다.

이 속성의 설정을 확인 하는 경우 c + + 비트 AND 연산자 ()를 사용 **&** 하 여 특정 특성을 테스트할 수 있습니다. 여러 특성을 설정할 때는 적절 한 상수를 비트 or (**&#124;**) 연산자와 결합 하 여 결합할 수 있습니다. 자세한 내용은 DAO 도움말의 "Attributes 속성" 항목을 참조 하십시오.

*m_nOrdinalPosition*<br/>
다른 필드를 기준으로 DAO 필드 개체가 나타내는 필드가 표시 되는 순서를 지정 하는 값입니다. [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)를 사용 하 여이 속성을 설정할 수 있습니다. 자세한 내용은 DAO 도움말의 "OrdinalPosition 속성" 항목을 참조 하십시오.

*m_bRequired*<br/>
DAO 필드 개체에 Null이 아닌 값이 필요한 지 여부를 나타냅니다. 이 속성이 TRUE 이면 필드에서 Null 값을 허용 하지 않습니다. Required가 FALSE로 설정 된 경우이 필드에는 AllowZeroLength 및 ValidationRule 속성 설정에 지정 된 조건에 맞는 값 뿐만 아니라 Null 값도 포함 될 수 있습니다. 자세한 내용은 DAO 도움말의 "필수 속성" 항목을 참조 하십시오. [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)를 사용 하 여 테이블 정의에 대해이 속성을 설정할 수 있습니다.

*m_bAllowZeroLength*<br/>
빈 문자열 ("")이 Text 또는 Memo 데이터 형식의 DAO field 개체의 유효한 값 인지 여부를 나타냅니다. 이 속성이 TRUE 이면 빈 문자열이 올바른 값입니다. 이 속성을 FALSE로 설정 하 여 빈 문자열을 사용 하 여 필드의 값을 설정할 수 없도록 할 수 있습니다. 자세한 내용은 DAO 도움말의 "AllowZeroLength 속성" 항목을 참조 하십시오. [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)를 사용 하 여 테이블 정의에 대해이 속성을 설정할 수 있습니다.

*m_lCollatingOrder*<br/>
텍스트에서 문자열 비교 또는 정렬 순서를 지정 합니다. 자세한 내용은 DAO 도움말의 "데이터 액세스에 대 한 Windows 레지스트리 설정 사용자 지정" 항목을 참조 하십시오. 반환 가능한 값의 목록은 `m_lCollatingOrder` [CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md) 구조체의 멤버를 참조 하십시오. [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)를 사용 하 여 테이블 정의에 대해이 속성을 설정할 수 있습니다.

*m_strForeignName*<br/>
관계에서 기본 테이블의 필드에 해당 하는 외래 테이블의 DAO 필드 개체 이름을 지정 하는 값입니다. 자세한 내용은 DAO 도움말의 "ForeignName 속성" 항목을 참조 하십시오.

*m_strSourceField*<br/>
테이블 정의, 레코드 집합 또는 querydef 개체에 포함 된 DAO field 개체에 대 한 데이터 원본의 원본 필드 이름을 나타냅니다. 이 속성은 field 개체와 연결 된 원래 필드 이름을 나타냅니다. 예를 들어이 속성을 사용 하 여 기본 테이블의 필드 이름과 관련이 없는 쿼리 필드에 있는 데이터의 원본 원본을 확인할 수 있습니다. 자세한 내용은 DAO 도움말의 "SourceField, SourceTable Properties" 항목을 참조 하십시오. [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)를 사용 하 여 테이블 정의에 대해이 속성을 설정할 수 있습니다.

*m_strSourceTable*<br/>
테이블 정의, 레코드 집합 또는 querydef 개체에 포함 된 DAO field 개체에 대 한 데이터의 원래 원본인 테이블의 이름을 나타냅니다. 이 속성은 field 개체와 연결 된 원래 테이블 이름을 나타냅니다. 예를 들어이 속성을 사용 하 여 기본 테이블의 필드 이름과 관련이 없는 쿼리 필드에 있는 데이터의 원본 원본을 확인할 수 있습니다. 자세한 내용은 DAO 도움말의 "SourceField, SourceTable Properties" 항목을 참조 하십시오. [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)를 사용 하 여 테이블 정의에 대해이 속성을 설정할 수 있습니다.

*m_strValidationRule*<br/>
테이블에 변경 되거나 추가 될 때 필드의 데이터에 대 한 유효성을 검사 하는 값입니다. 자세한 내용은 DAO 도움말의 "ValidationRule 속성" 항목을 참조 하십시오. [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)를 사용 하 여 테이블 정의에 대해이 속성을 설정할 수 있습니다.

테이블 형식의 관련 정보는 `m_strValidationRule` [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) 구조체의 멤버를 참조 하십시오.

*m_strValidationText*<br/>
응용 프로그램에 표시 되는 메시지의 텍스트를 지정 하는 값입니다 .이 값은 DAO 필드 개체의 값이 ValidationRule 속성 설정에 지정 된 유효성 검사 규칙을 충족 하지 않는 경우에 표시 됩니다. 자세한 내용은 DAO 도움말의 "ValidationText 속성" 항목을 참조 하십시오. [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)를 사용 하 여 테이블 정의에 대해이 속성을 설정할 수 있습니다.

*m_strDefaultValue*<br/>
DAO field 개체의 기본값입니다. 새 레코드가 생성 되 면 DefaultValue 속성 설정이 자동으로 필드 값으로 입력 됩니다. 자세한 내용은 DAO 도움말의 "DefaultValue 속성" 항목을 참조 하십시오. [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)를 사용 하 여 테이블 정의에 대해이 속성을 설정할 수 있습니다.

## <a name="remarks"></a>설명

위의 기본, 보조 및 모든에 대 한 참조는 `GetFieldInfo` [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo), [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)및 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)클래스의 멤버 함수에서 정보를 반환 하는 방법을 표시 합니다.

Field 개체는 MFC 클래스로 표현 되지 않습니다. 대신, 다음 클래스의 기본 MFC 개체에 포함 된 DAO 개체는 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)및 [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)필드 개체의 컬렉션을 포함 합니다. 이러한 클래스는 필드 정보의 일부 개별 항목에 액세스 하는 멤버 함수를 제공 하거나, 포함 하는 `CDaoFieldInfo` `GetFieldInfo` 개체의 멤버 함수를 호출 하 여 개체를 사용 하 여 한 번에 모두 액세스할 수 있습니다.

개체 속성을 검사 하는 데 사용 하는 것 외에도를 사용 `CDaoFieldInfo` 하 여 테이블 정의에 새 필드를 만들기 위한 입력 매개 변수를 생성할 수 있습니다. 이 작업에는 보다 간단한 옵션을 사용할 수 있지만 보다 세부적인 제어를 원하는 경우 매개 변수를 사용 하는 [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield) 버전을 사용할 수 있습니다 `CDaoFieldInfo` .

`GetFieldInfo`멤버 함수 (필드를 포함 하는 클래스)에 의해 검색 된 정보는 구조체에 저장 됩니다 `CDaoFieldInfo` . 필드 `GetFieldInfo` 개체가 저장 된 필드 컬렉션을 포함 하는 개체의 멤버 함수를 호출 합니다. `CDaoFieldInfo` 또한 `Dump` 디버그 빌드에서 멤버 함수를 정의 합니다. `Dump`를 사용 하 여 개체의 콘텐츠를 덤프할 수 있습니다 `CDaoFieldInfo` .

## <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="see-also"></a>참고 항목

[구조체, 스타일, 콜백 및 메시지 맵](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetFieldInfo](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)<br/>
[CDaoRecordset::GetFieldInfo](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)<br/>
[CDaoQueryDef::GetFieldInfo](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)
