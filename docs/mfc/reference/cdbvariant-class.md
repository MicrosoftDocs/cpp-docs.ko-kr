---
description: '자세히 알아보기: CDBVariant 클래스'
title: CDBVariant 클래스
ms.date: 11/04/2016
f1_keywords:
- CDBVariant
- AFXDB/CDBVariant
- AFXDB/CDBVariant::CDBVariant
- AFXDB/CDBVariant::Clear
- AFXDB/CDBVariant::m_dwType
- AFXDB/CDBVariant::m_boolVal
- AFXDB/CDBVariant::m_chVal
- AFXDB/CDBVariant::m_dblVal
- AFXDB/CDBVariant::m_fltVal
- AFXDB/CDBVariant::m_iVal
- AFXDB/CDBVariant::m_lVal
- AFXDB/CDBVariant::m_pbinary
- AFXDB/CDBVariant::m_pdate
- AFXDB/CDBVariant::m_pstring
- AFXDB/CDBVariant::m_pstringA
- AFXDB/CDBVariant::m_pstringW
helpviewer_keywords:
- CDBVariant [MFC], CDBVariant
- CDBVariant [MFC], Clear
- CDBVariant [MFC], m_dwType
- CDBVariant [MFC], m_boolVal
- CDBVariant [MFC], m_chVal
- CDBVariant [MFC], m_dblVal
- CDBVariant [MFC], m_fltVal
- CDBVariant [MFC], m_iVal
- CDBVariant [MFC], m_lVal
- CDBVariant [MFC], m_pbinary
- CDBVariant [MFC], m_pdate
- CDBVariant [MFC], m_pstring
- CDBVariant [MFC], m_pstringA
- CDBVariant [MFC], m_pstringW
ms.assetid: de23609c-c560-4b24-bd6b-9d8903fd5b49
ms.openlocfilehash: 54fc432998a15d79ab51165b280e4cc4ced94455
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247944"
---
# <a name="cdbvariant-class"></a>CDBVariant 클래스

MFC ODBC 클래스의 variant 데이터 형식을 나타냅니다.

## <a name="syntax"></a>구문

```
class CDBVariant
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDBVariant:: CDBVariant](#cdbvariant)|`CDBVariant` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDBVariant:: Clear](#clear)|개체를 지웁니다 `CDBVariant` .|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CDBVariant:: m_dwType](#m_dwtype)|현재 저장 된 값의 데이터 형식을 포함 합니다. `DWORD`을 입력합니다.|

### <a name="public-union-members"></a>공용 공용 구조체 멤버

|Name|설명|
|----------|-----------------|
|[CDBVariant:: m_boolVal](#m_boolval)|**BOOL** 형식의 값을 포함 합니다.|
|[CDBVariant:: m_chVal](#m_chval)|형식의 값을 포함 **`unsigned char`** 합니다.|
|[CDBVariant:: m_dblVal](#m_dblval)|형식의 값을 포함 **`double`** 합니다.|
|[CDBVariant:: m_fltVal](#m_fltval)|형식의 값을 포함 **`float`** 합니다.|
|[CDBVariant:: m_iVal](#m_ival)|형식의 값을 포함 **`short`** 합니다.|
|[CDBVariant:: m_lVal](#m_lval)|형식의 값을 포함 **`long`** 합니다.|
|[CDBVariant:: m_pbinary](#m_pbinary)|형식의 개체에 대 한 포인터를 포함 `CLongBinary` 합니다.|
|[CDBVariant:: m_pdate](#m_pdate)|**TIMESTAMP_STRUCT** 형식의 개체에 대 한 포인터를 포함 합니다.|
|[CDBVariant:: m_pstring](#m_pstring)|형식의 개체에 대 한 포인터를 포함 `CString` 합니다.|
|[CDBVariant:: m_pstringA](#m_pstringa)|ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md) 개체에 대 한 포인터를 저장 합니다.|
|[CDBVariant:: m_pstringW](#m_pstringw)|와이드 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 개체에 대 한 포인터를 저장 합니다.|

## <a name="remarks"></a>설명

`CDBVariant` 에 기본 클래스가 없습니다.

`CDBVariant`[COleVariant](../../mfc/reference/colevariant-class.md)와 비슷합니다. 그러나 `CDBVariant` 는 OLE를 사용 하지 않습니다. `CDBVariant` 값의 데이터 형식에 대해 걱정 하지 않고 값을 저장할 수 있습니다. `CDBVariant` 공용 구조체에 저장 된 현재 값의 데이터 형식을 추적 합니다.

[CRecordset](../../mfc/reference/crecordset-class.md) 클래스 `CDBVariant` 는 세 개의 멤버 함수, 및에서 개체를 활용 `GetFieldValue` `GetBookmark` `SetBookmark` 합니다. 예를 들어를 사용 하 여 `GetFieldValue` 열의 데이터를 동적으로 가져올 수 있습니다. 열의 데이터 형식은 런타임에 알려지지 않을 수 있기 때문에에서는 개체를 사용 하 여 `GetFieldValue` `CDBVariant` 열의 데이터를 저장 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CDBVariant`

## <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="cdbvariantcdbvariant"></a><a name="cdbvariant"></a> CDBVariant:: CDBVariant

NULL 개체를 만듭니다 `CDBVariant` .

```
CDBVariant();
```

### <a name="remarks"></a>설명

DBVT_NULL [m_dwType](#m_dwtype) 데이터 멤버를 설정 합니다.

## <a name="cdbvariantclear"></a><a name="clear"></a> CDBVariant:: Clear

개체를 지우려면이 멤버 함수를 호출 `CDBVariant` 합니다.

```cpp
void Clear();
```

### <a name="remarks"></a>설명

[M_dwType](#m_dwtype) 데이터 멤버의 값이 DBVT_DATE, DBVT_STRING 또는 DBVT_BINARY 이면 `Clear` union 포인터 멤버와 연결 된 메모리를 해제 합니다. `Clear``m_dwType`DBVT_NULL로 설정 합니다.

소멸자는를 `CDBVariant` 호출 `Clear` 합니다.

## <a name="cdbvariantm_boolval"></a><a name="m_boolval"></a> CDBVariant:: m_boolVal

BOOL 형식의 값을 저장 합니다.

### <a name="remarks"></a>설명

`m_boolVal`데이터 멤버가 공용 구조체에 속합니다. 액세스 하기 전에 `m_boolVal` 먼저 [Cdbvariant:: m_dwType](#m_dwtype)의 값을 확인 합니다. `m_dwType`가 DBVT_BOOL로 설정 된 경우에는 `m_boolVal` 유효한 값이 포함 됩니다. 그렇지 않으면에 액세스 하면 신뢰할 수 없는 `m_boolVal` 결과가 생성 됩니다.

## <a name="cdbvariantm_chval"></a><a name="m_chval"></a> CDBVariant:: m_chVal

형식의 값을 저장 **`unsigned char`** 합니다.

### <a name="remarks"></a>설명

`m_chVal`데이터 멤버가 공용 구조체에 속합니다. 액세스 하기 전에 `m_chVal` 먼저 [Cdbvariant:: m_dwType](#m_dwtype)의 값을 확인 합니다. `m_dwType`가 DBVT_UCHAR로 설정 된 경우에는 `m_chVal` 유효한 값이 포함 되 고, 그렇지 않으면에 액세스 하면 신뢰할 수 없는 `m_chVal` 결과가 생성 됩니다.

## <a name="cdbvariantm_dblval"></a><a name="m_dblval"></a> CDBVariant:: m_dblVal

형식의 값을 저장 **`double`** 합니다.

### <a name="remarks"></a>설명

`m_dblVal`데이터 멤버가 공용 구조체에 속합니다. 액세스 하기 전에 `m_dblVal` 먼저 [Cdbvariant:: m_dwType](#m_dwtype)의 값을 확인 합니다. `m_dwType`가 DBVT_DOUBLE로 설정 된 경우에는 `m_dblVal` 유효한 값이 포함 되 고, 그렇지 않으면에 액세스 하면 신뢰할 수 없는 `m_dblVal` 결과가 생성 됩니다.

## <a name="cdbvariantm_dwtype"></a><a name="m_dwtype"></a> CDBVariant:: m_dwType

이 데이터 멤버는 `CDBVariant` 개체의 union 데이터 멤버에 현재 저장 된 값의 데이터 형식을 포함 합니다.

### <a name="remarks"></a>설명

이 공용 구조체에 액세스 하기 전에 값을 확인 `m_dwType` 하 여 액세스할 공용 구조체 데이터 멤버를 결정 해야 합니다. 다음 표에서는 `m_dwType` 및 해당 union 데이터 멤버에 사용할 수 있는 값을 보여 줍니다.

|m_dwType|Union 데이터 멤버|
|---------------|-----------------------|
|DBVT_NULL|액세스에 사용할 수 있는 union 멤버가 없습니다.|
|DBVT_BOOL|[m_boolVal](#m_boolval)|
|DBVT_UCHAR|[m_chVal](#m_chval)|
|DBVT_SHORT|[m_iVal](#m_ival)|
|DBVT_LONG|[m_lVal](#m_lval)|
|DBVT_SINGLE|[m_fltVal](#m_fltval)|
|DBVT_DOUBLE|[m_dblVal](#m_dblval)|
|DBVT_DATE|[m_pdate](#m_pdate)|
|DBVT_STRING|[m_pstring](#m_pstring)|
|DBVT_BINARY|[m_pbinary](#m_pbinary)|
|DBVT_ASTRING|[m_pstringA](#m_pstringa)|
|DBVT_WSTRING|[m_pstringW](#m_pstringw)|

## <a name="cdbvariantm_fltval"></a><a name="m_fltval"></a> CDBVariant:: m_fltVal

형식의 값을 저장 **`float`** 합니다.

### <a name="remarks"></a>설명

`m_fltVal`데이터 멤버가 공용 구조체에 속합니다. 액세스 하기 전에 `m_fltVal` 먼저 [Cdbvariant:: m_dwType](#m_dwtype)의 값을 확인 합니다. `m_dwType`가 DBVT_SINGLE로 설정 된 경우에는 `m_fltVal` 유효한 값이 포함 되 고, 그렇지 않으면에 액세스 하면 신뢰할 수 없는 `m_fltVal` 결과가 생성 됩니다.

## <a name="cdbvariantm_ival"></a><a name="m_ival"></a> CDBVariant:: m_iVal

형식의 값을 저장 **`short`** 합니다.

### <a name="remarks"></a>설명

`m_iVal`데이터 멤버가 공용 구조체에 속합니다. 액세스 하기 전에 `m_iVal` 먼저 [Cdbvariant:: m_dwType](#m_dwtype)의 값을 확인 합니다. `m_dwType`가 DBVT_SHORT로 설정 된 경우에는 `m_iVal` 유효한 값이 포함 되 고, 그렇지 않으면에 액세스 하면 신뢰할 수 없는 `m_iVal` 결과가 생성 됩니다.

## <a name="cdbvariantm_lval"></a><a name="m_lval"></a> CDBVariant:: m_lVal

형식의 값을 저장 **`long`** 합니다.

### <a name="remarks"></a>설명

`m_lVal`데이터 멤버가 공용 구조체에 속합니다. 액세스 하기 전에 `m_lVal` 먼저 [Cdbvariant:: m_dwType](#m_dwtype)의 값을 확인 합니다. `m_dwType`가 DBVT_LONG로 설정 된 경우에는 `m_lVal` 유효한 값이 포함 되 고, 그렇지 않으면에 액세스 하면 신뢰할 수 없는 `m_lVal` 결과가 생성 됩니다.

## <a name="cdbvariantm_pbinary"></a><a name="m_pbinary"></a> CDBVariant:: m_pbinary

[CLongBinary](../../mfc/reference/clongbinary-class.md)형식의 개체에 대 한 포인터를 저장 합니다.

### <a name="remarks"></a>설명

`m_pbinary`데이터 멤버가 공용 구조체에 속합니다. 액세스 하기 전에 `m_pbinary` 먼저 [Cdbvariant:: m_dwType](#m_dwtype)의 값을 확인 합니다. `m_dwType`가 DBVT_BINARY로 설정 된 경우에는 `m_pbinary` 유효한 포인터가 포함 되 고, 그렇지 않으면에 액세스 하면 신뢰할 수 없는 `m_pbinary` 결과가 생성 됩니다.

## <a name="cdbvariantm_pdate"></a><a name="m_pdate"></a> CDBVariant:: m_pdate

TIMESTAMP_STRUCT 형식의 개체에 대 한 포인터를 저장 합니다.

### <a name="remarks"></a>설명

`m_pdate`데이터 멤버가 공용 구조체에 속합니다. 액세스 하기 전에 `m_pdate` 먼저 [Cdbvariant:: m_dwType](#m_dwtype)의 값을 확인 합니다. `m_dwType`가 DBVT_DATE로 설정 된 경우에는 `m_pdate` 유효한 포인터가 포함 되 고, 그렇지 않으면에 액세스 하면 신뢰할 수 없는 `m_pdate` 결과가 생성 됩니다.

TIMESTAMP_STRUCT 데이터 형식에 대 한 자세한 내용은 Windows SDK의 *ODBC 프로그래머 참조* 에서 부록 D의 [C 데이터 형식](/sql/odbc/reference/appendixes/c-data-types) 항목을 참조 하세요.

## <a name="cdbvariantm_pstring"></a><a name="m_pstring"></a> CDBVariant:: m_pstring

[CString](../../atl-mfc-shared/reference/cstringt-class.md)형식의 개체에 대 한 포인터를 저장 합니다.

### <a name="remarks"></a>설명

`m_pstring`데이터 멤버가 공용 구조체에 속합니다. 액세스 하기 전에 `m_pstring` 먼저 [Cdbvariant:: m_dwType](#m_dwtype)의 값을 확인 합니다. `m_dwType`가 DBVT_STRING로 설정 된 경우에는 `m_pstring` 유효한 포인터가 포함 되 고, 그렇지 않으면에 액세스 하면 신뢰할 수 없는 `m_pstring` 결과가 생성 됩니다.

## <a name="cdbvariantm_pstringa"></a><a name="m_pstringa"></a> CDBVariant:: m_pstringA

ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md) 개체에 대 한 포인터를 저장 합니다.

### <a name="remarks"></a>설명

`m_pstringA`데이터 멤버가 공용 구조체에 속합니다. 액세스 하기 전에 `m_pstringA` 먼저 [Cdbvariant:: m_dwType](#m_dwtype)의 값을 확인 합니다. `m_dwType`가 DBVT_ASTRING로 설정 된 경우에는 `m_pstringA` 유효한 포인터가 포함 되 고, 그렇지 않으면에 액세스 하면 신뢰할 수 없는 `m_pstringA` 결과가 생성 됩니다.

## <a name="cdbvariantm_pstringw"></a><a name="m_pstringw"></a> CDBVariant:: m_pstringW

와이드 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 개체에 대 한 포인터를 저장 합니다.

### <a name="remarks"></a>설명

`m_pstringW`데이터 멤버가 공용 구조체에 속합니다. 액세스 하기 전에 `m_pstringW` 먼저 [Cdbvariant:: m_dwType](#m_dwtype)의 값을 확인 합니다. `m_dwType`가 DBVT_WSTRING로 설정 된 경우에는 `m_pstringW` 유효한 포인터가 포함 되 고, 그렇지 않으면에 액세스 하면 신뢰할 수 없는 `m_pstringW` 결과가 생성 됩니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 클래스](../../mfc/reference/crecordset-class.md)
