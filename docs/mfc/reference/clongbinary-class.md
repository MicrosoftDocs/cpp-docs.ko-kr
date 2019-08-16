---
title: CLongBinary 클래스
ms.date: 11/04/2016
f1_keywords:
- CLongBinary
- AFXDB_/CLongBinary
- AFXDB_/CLongBinary::CLongBinary
- AFXDB_/CLongBinary::m_dwDataLength
- AFXDB_/CLongBinary::m_hData
helpviewer_keywords:
- CLongBinary class [MFC]
ms.assetid: f4320059-aeb4-4ee5-bc2b-25f19d898ef5
ms.openlocfilehash: 94666c0d15898e05ae78663a15d86b7d00d5c9c6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505682"
---
# <a name="clongbinary-class"></a>CLongBinary 클래스

데이터베이스에서 매우 큰 이진 데이터 개체(BLOB 또는 "이진 대형 개체"라고도 함) 사용 작업을 간소화합니다.

## <a name="syntax"></a>구문

```
class CLongBinary : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|Description|
|----------|-----------------|
|[CLongBinary::CLongBinary](#clongbinary)|`CLongBinary` 개체를 생성합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|이름|Description|
|----------|-----------------|
|[CLongBinary::m_dwDataLength](#m_dwdatalength)|핸들이 저장 `m_hData`된 데이터 개체의 실제 크기 (바이트)를 포함 합니다.|
|[CLongBinary::m_hData](#m_hdata)|실제 이미지 개체에 대 한 Windows HGLOBAL 핸들을 포함 합니다.|

## <a name="remarks"></a>설명

예를 들어 SQL 테이블의 레코드 필드에는 그림을 나타내는 비트맵이 포함 될 수 있습니다. 개체 `CLongBinary` 는 이러한 개체를 저장 하 고 크기를 추적 합니다.

> [!NOTE]
>  일반적으로 [DFX_Binary](record-field-exchange-functions.md#dfx_binary) 함수와 함께 [CByteArray](../../mfc/reference/cbytearray-class.md) 를 사용 하는 것이 더 좋습니다. 을 계속 사용할 `CLongBinary`수 있지만 일반적 `CByteArray` 으로는 16 비트 `CByteArray`에서 발생 하는 크기 제한이 더 이상 없으므로 Win32에서 더 많은 기능을 제공 합니다. 이 권장 사항은 ODBC (Open Database Connectivity) 뿐만 아니라 DAO (Data Access Objects)를 사용한 프로그래밍에 적용 됩니다.

`CLongBinary` 개체를 사용 하려면 레코드 집합 클래스에서 형식의 `CLongBinary` 필드 데이터 멤버를 선언 합니다. 이 멤버는 레코드 집합 클래스의 포함 된 멤버가 되며 레코드 집합을 생성할 때 생성 됩니다. `CLongBinary` 개체를 생성 한 후에는 RFX (레코드 필드 교환) 메커니즘이 데이터 원본에 있는 현재 레코드의 필드에서 데이터 개체를 로드 하 고 레코드가 업데이트 될 때 레코드에 다시 저장 합니다. RFX는 이진 큰 개체의 크기에 대 한 데이터 소스 `CLongBinary` 를 쿼리하고, 개체의 `m_hData` 데이터 멤버를 통해 저장소를 할당 하 고,에 `m_hData`데이터에 `HGLOBAL` 대 한 핸들을 저장 합니다. 또한 RFX는 데이터 개체의 실제 크기를 `m_dwDataLength` 데이터 멤버에 저장 합니다. 일반적으로 Windows `HGLOBAL` 핸들에 저장 된 데이터 `m_hData`를 조작 하는 데 사용 하는 것과 동일한 기술을 사용 하 여 개체의 데이터를 사용 하 여 작업 합니다.

레코드 집합을 삭제 하면 포함 `CLongBinary` 된 개체도 소멸 되며 해당 소멸자는 데이터 핸들의 `HGLOBAL` 할당을 취소 합니다.

대량 개체 및 사용 `CLongBinary`에 대 한 자세한 내용은 [레코드 집합 (ODBC)](../../data/odbc/recordset-odbc.md) 및 [레코드 집합을 참조 하세요. 대량 데이터 항목 작업 (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)

## <a name="inheritance-hierarchy"></a>상속 계층

[CObject](../../mfc/reference/cobject-class.md)

`CLongBinary`

## <a name="requirements"></a>요구 사항

**헤더:** afxdb_

##  <a name="clongbinary"></a>  CLongBinary::CLongBinary

`CLongBinary` 개체를 생성합니다.

```
CLongBinary();
```

##  <a name="m_dwdatalength"></a>  CLongBinary::m_dwDataLength

의 `m_hData`HGLOBAL 핸들에 저장 된 데이터의 실제 크기 (바이트)를 저장 합니다.

```
SQLULEN m_dwDataLength;
```

### <a name="remarks"></a>설명

이 크기는 데이터에 할당 된 메모리 블록의 크기 보다 작을 수 있습니다. Win32 [globalsize](/windows/win32/api/winbase/nf-winbase-globalsize) 함수를 호출 하 여 할당 된 크기를 가져옵니다.

##  <a name="m_hdata"></a>  CLongBinary::m_hData

실제 blob (binary large object) 데이터에 Windows HGLOBAL 핸들을 저장 합니다.

```
HGLOBAL m_hData;
```

## <a name="see-also"></a>참고자료

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 클래스](../../mfc/reference/crecordset-class.md)
