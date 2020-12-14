---
description: 'TN045: Long Varchar/Varbinary에 대 한 MFC/데이터베이스 지원에 대해 자세히 알아보세요.'
title: 'TN045: Long Varchar-Varbinary에 대 한 MFC-Database 지원'
ms.date: 11/04/2016
helpviewer_keywords:
- TN045
- Varbinary data type
- Varchar data type
ms.assetid: cf572c35-5275-45b5-83df-5f0e36114f40
ms.openlocfilehash: 4e19147ab5ca392307f331b12d3cf24eb5fcc06f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215185"
---
# <a name="tn045-mfcdatabase-support-for-long-varcharvarbinary"></a>TN045: Long Varchar/Varbinary에 대한 MFC/데이터베이스 지원

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

이 참고에서는 MFC 데이터베이스 클래스를 사용 하 여 ODBC **SQL_LONGVARCHAR** 및 **SQL_LONGVARBINARY** 데이터 형식을 검색 하 고 보내는 방법에 대해 설명 합니다.

## <a name="overview-of-long-varcharvarbinary-support"></a>Long Varchar/Varbinary 지원 개요

ODBC **SQL_LONG_VARCHAR** 및 **SQL_LONGBINARY** 데이터 형식 (여기서는 LONG 데이터 열 이라고 함)은 엄청난 양의 데이터를 보유할 수 있습니다. 이 데이터를 처리 하는 방법에는 3 가지가 있습니다.

- 에 바인딩합니다 `CString` / `CByteArray` .

- 에 바인딩합니다 `CLongBinary` .

- 데이터베이스 클래스에 관계 없이 long 데이터 값을 검색 하 여 수동으로 전송 하지 마십시오.

세 가지 방법 각각의 장점과 단점이 있습니다.

쿼리의 매개 변수에는 Long 데이터 열을 사용할 수 없습니다. OutputColumns에 대해서만 지원 됩니다.

## <a name="binding-a-long-data-column-to-a-cstringcbytearray"></a>Long 데이터 열을 CString/CByteArray에 바인딩

장점

이 방법은 이해 하기 쉽고 친숙 한 클래스를 사용 하 여 작업 합니다. 프레임 워크는 `CFormView` 에 대 한 지원을 제공 합니다 `CString` `DDX_Text` . 및 클래스를 사용 하는 일반적인 문자열 또는 컬렉션 기능이 `CString` 많고 `CByteArray` 데이터 값을 보유 하기 위해 로컬로 할당 되는 메모리의 양을 제어할 수 있습니다. 프레임 워크는 또는 함수 호출 중에 필드 데이터의 이전 복사본 `Edit` `AddNew` 을 유지 하 고 프레임 워크는 데이터 변경 내용을 자동으로 검색할 수 있습니다.

> [!NOTE]
> `CString`는 문자 데이터를 사용 하도록 설계 되었으며 이진 데이터에서 작업 하는 경우에는 `CByteArray` 문자 데이터 (**SQL_LONGVARCHAR**)를에 배치 하 `CString` 고 이진 데이터 (**SQL_LONGVARBINARY**)를에 배치 하는 것이 좋습니다 `CByteArray` .

및에 대 한 RFX 함수에는 `CString` `CByteArray` 할당 된 메모리의 기본 크기를 재정의 하 여 데이터 열에 대해 검색 된 값을 저장할 수 있는 추가 인수가 있습니다. 다음 함수 선언에서 nMaxLength 인수를 확인 합니다.

```cpp
void AFXAPI RFX_Text(CFieldExchange* pFX,
    const char *szName,
    CString& value,
    int nMaxLength = 255,
    int nColumnType =
    SQL_VARCHAR);

void AFXAPI RFX_Binary(CFieldExchange* pFX,
    const char *szName,
    CByteArray& value,
    int nMaxLength = 255);
```

Long 데이터 열을 또는로 검색 하는 경우 반환 되는 `CString` `CByteArray` 데이터의 최대 크기는 기본적으로 255 바이트입니다. 이 이외의 모든 항목은 무시 됩니다. 이 경우 프레임 워크는 **AFX_SQL_ERROR_DATA_TRUNCATED** 예외를 throw 합니다. 다행히 nMaxLength를 보다 큰 값으로 최대 **MAXINT** 까지 명시적으로 늘릴 수 있습니다.

> [!NOTE]
> NMaxLength 값은 MFC에서 함수의 로컬 버퍼를 설정 하는 데 사용 됩니다 `SQLBindColumn` . 이는 데이터 저장소에 대 한 로컬 버퍼 이며 실제로는 ODBC 드라이버에서 반환 되는 데이터의 양에 영향을 주지 않습니다. `RFX_Text` 및 `RFX_Binary` 는를 사용 하 여 `SQLFetch` 백 엔드 데이터베이스에서 데이터를 검색 하는 한 번만 호출 합니다. 각 ODBC 드라이버에는 단일 인출에서 반환할 수 있는 데이터 양에 대 한 제한이 다릅니다. 이 제한은 nMaxLength에 설정 된 값 보다 훨씬 작을 수 있으며,이 경우 예외 **AFX_SQL_ERROR_DATA_TRUNCATED** throw 됩니다. 이러한 경우에는 대신를 사용 하 여 `RFX_LongBinary` `RFX_Text` `RFX_Binary` 모든 데이터를 검색할 수 있도록 전환 합니다.

클래스 마법사는 **SQL_LONGVARCHAR** `CString` 또는 **SQL_LONGVARBINARY** 에 바인딩합니다 `CByteArray` . Long 데이터 열을 검색 하는 데 255 바이트를 초과 하는 값을 할당 하려는 경우 nMaxLength에 대해 명시적 값을 제공할 수 있습니다.

Long 데이터 열이 또는에 바인딩되어 있는 경우 `CString` `CByteArray` 필드를 업데이트 하면 SQL_ **VARCHAR** 또는 SQL_ **VARBINARY** 에 바인딩될 때와 동일 하 게 작동 합니다. 동안 데이터 값 `Edit` 은 `Update` 데이터 값의 변경 내용을 감지 하 고 해당 열에 대 한 더티 및 Null 값을 적절 하 게 설정 하기 위해가 호출 될 때 이후에 비교 됩니다.

## <a name="binding-a-long-data-column-to-a-clongbinary"></a>Long 데이터 열을 CLongBinary에 바인딩

Long 데이터 열에 더 많은 **MAXINT** 바이트의 데이터가 포함 될 수 있는 경우로 검색 하는 것이 좋습니다 `CLongBinary` .

장점

이렇게 하면 사용 가능한 메모리까지 전체 long 데이터 열이 검색 됩니다.

단점

데이터는 메모리에 저장 됩니다. 이 접근 방식은 매우 많은 양의 데이터에 비해 비용이 많이 듭니다. `SetFieldDirty`필드가 작업에 포함 되도록 하려면 바인딩된 데이터 멤버에 대해를 호출 해야 합니다 `Update` .

Long 데이터 열을로 검색 하는 경우 `CLongBinary` 데이터베이스 클래스는 long 데이터 열의 전체 크기를 확인 한 다음 `HGLOBAL` 전체 데이터 값을 저장할 수 있을 만큼 큰 메모리 세그먼트를 할당 합니다. 그런 다음 데이터베이스 클래스는 전체 데이터 값을 할당 된로 검색 합니다 `HGLOBAL` .

데이터 소스가 long 데이터 열의 예상 크기를 반환할 수 없는 경우 프레임 워크는 **AFX_SQL_ERROR_SQL_NO_TOTAL** 예외를 throw 합니다. 를 할당 하려는 시도가 실패 하면 `HGLOBAL` 표준 메모리 예외가 throw 됩니다.

클래스 마법사는 **SQL_LONGVARCHAR** 또는 **SQL_LONGVARBINARY** 를에 바인딩합니다 `CLongBinary` . `CLongBinary`멤버 변수 추가 대화 상자에서 변수 형식으로를 선택 합니다. 그러면 클래스 마법사는 `RFX_LongBinary` 호출에 대 한 호출을 추가 `DoFieldExchange` 하 고 바인딩된 필드의 총 수를 늘립니다.

Long 데이터 열 값을 업데이트 하려면 먼저 `HGLOBAL` 의 *m_hData* 멤버에서 **:: globalsize** 를 호출 하 여 새 데이터를 저장할 수 있도록 할당 된이 큰지 확인 합니다 `CLongBinary` . 너무 작은 경우를 해제 `HGLOBAL` 하 고 적절 한 크기를 할당 합니다. 그런 다음 새 크기를 반영 하도록 *m_dwDataLength* 를 설정 합니다.

그렇지 않고 *m_dwDataLength* 을 바꾸려는 데이터의 크기 보다 큰 경우에는를 해제 하거나 다시 `HGLOBAL` 할당 하거나 할당 된 상태로 둘 수 있습니다. *M_dwDataLength* 에 실제로 사용 되는 바이트 수를 표시 해야 합니다.

## <a name="how-updating-a-clongbinary-works"></a>CLongBinary를 업데이트 하는 방법

의 업데이트 방식을 이해할 필요는 `CLongBinary` 없지만 아래에 설명 된이 세 번째 방법을 선택 하는 경우 데이터 원본에 긴 데이터 값을 전송 하는 방법에 대 한 예제로 유용할 수 있습니다.

> [!NOTE]
> `CLongBinary`업데이트에 필드를 포함 하려면 필드에 대해를 명시적으로 호출 해야 합니다 `SetFieldDirty` . Null 설정을 포함 하 여 필드를 변경 하는 경우를 호출 해야 `SetFieldDirty` 합니다. 또한 `SetFieldNull` 두 번째 매개 변수를 사용 하 여 필드 에 값이 있는 것으로 표시 하려면를 호출 해야 합니다.

필드를 업데이트할 때 `CLongBinary` 데이터베이스 클래스는 odbc의 **DATA_AT_EXEC** 메커니즘을 사용 합니다 (Odbc 설명서의 `SQLSetPos` rgbValue 인수 참조). 프레임 워크가 삽입 또는 업데이트 문을 준비 하는 경우 데이터를 포함 하는을 가리키지 않고의 `HGLOBAL` *주소가* `CLongBinary` 대신 열의 *값* 으로 설정 되 고 길이 표시기가 **SQL_DATA_AT_EXEC** 로 설정 됩니다. 나중에 update 문이 데이터 원본으로 전송 될 때는 SQL_NEED_DATA을 `SQLExecDirect` 반환 합니다 . 이 열에 대 한 매개 변수 값이 실제로의 주소 임을 프레임 워크에 알립니다 `CLongBinary` . 프레임 워크는 `SQLGetData` 작은 버퍼를 사용 하 여 한 번 호출 하며 드라이버에서 데이터의 실제 길이를 반환 합니다. 드라이버가 blob (binary large object)의 실제 길이를 반환 하는 경우 MFC는 BLOB를 인출 하는 데 필요한 만큼 공간을 다시 할당 합니다. 데이터 소스가 **SQL_NO_TOTAL** 를 반환 하는 경우 BLOB의 크기를 확인할 수 없다는 것을 나타내는 MFC는 더 작은 블록을 만듭니다. 기본 초기 크기는 64K이 고 후속 블록은 크기의 두 배가 됩니다. 예를 들어 두 번째는 128K, 세 번째는 256K 등이 됩니다. 초기 크기는 구성 가능 합니다.

## <a name="not-binding-retrievingsending-data-directly-from-odbc-with-sqlgetdata"></a>바인딩하지 않음: SQLGetData를 사용 하 여 ODBC에서 직접 데이터 검색/송신

이 방법을 사용 하 여 데이터베이스 클래스를 완전히 우회 하 고 long 데이터 열을 직접 처리 합니다.

장점

필요한 경우 디스크에 데이터를 캐시 하거나 검색할 데이터의 양을 동적으로 결정할 수 있습니다.

단점

프레임 워크의 `Edit` 또는 `AddNew` 지원을 받지 않으며 기본 기능을 수행 하는 코드를 직접 작성 해야 합니다 ( `Delete` 열 수준 작업이 아니기 때문에 작동 함).

이 경우 long 데이터 열은 레코드 집합의 select 목록에 있어야 하지만 프레임 워크에서 바인딩되지 않아야 합니다. 이 작업을 수행 하는 한 가지 방법은 `GetDefaultSQL` 또는를의 함수에 대 한 lpszSQL 인수로 제공 `CRecordset` 하 `Open` 고 RFX_ 함수 호출을 사용 하 여 추가 열을 바인딩하지 않는 것입니다. 바인딩되지 않은 필드는 바인딩된 필드의 오른쪽에 표시 되므로 바인딩되지 않은 열을 선택 목록의 끝에 추가 해야 합니다.

> [!NOTE]
> Long 데이터 열은 프레임 워크에서 바인딩되지 않으므로 해당 열에 대 한 변경 내용은 호출로 처리 되지 않습니다 `CRecordset::Update` . 필요한 SQL **INSERT** 및 **UPDATE** 문을 직접 만들고 보내야 합니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
