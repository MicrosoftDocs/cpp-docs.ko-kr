---
description: '자세히 알아보기: 레코드 필드 교환: RFX 함수 사용'
title: '레코드 필드 교환: RFX 함수 사용'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC [C++], data types
- data types [C++], ODBC record field exchange
- RFX (ODBC) [C++], function syntax and parameters
- DoFieldExchange method, and RFX functions
- ODBC [C++], RFX
- RFX (ODBC) [C++], data types
- function calls, RFX functions
ms.assetid: c594300b-5a29-4119-a68b-e7ca32def696
ms.openlocfilehash: 8b597a6ca8ae43922b6bba57b63ea2fc93fb82d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298762"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>레코드 필드 교환: RFX 함수 사용

이 항목에서는 재정의 본문을 구성 하는 RFX 함수 호출을 사용 하는 방법에 대해 설명 합니다 `DoFieldExchange` .

> [!NOTE]
> 이 항목은 대량 행 페치가 구현 되지 않은 [CRecordset](../../mfc/reference/crecordset-class.md) 에서 파생 된 클래스에 적용 됩니다. 대량 행 페치를 사용하는 경우 대량 레코드 필드 교환(대량 RFX)이 구현됩니다. 대량 RFX는 RFX와 비슷합니다. 차이점을 이해 하려면 [레코드 집합: 대량 레코드 페치 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)를 참조 하세요.

RFX 전역 함수는 데이터 원본의 열과 레코드 집합의 필드 데이터 멤버 간에 데이터를 교환 합니다. 레코드 집합의 [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) 멤버 함수에서 RFX 함수 호출을 작성 합니다. 이 항목에서는 함수에 대해 간략하게 설명 하 고 RFX 함수를 사용할 수 있는 데이터 형식을 보여 줍니다. [기술 참고 43](../../mfc/tn043-rfx-routines.md) 는 추가 데이터 형식에 대 한 고유한 RFX 함수를 작성 하는 방법을 설명 합니다.

## <a name="rfx-function-syntax"></a><a name="_core_rfx_function_syntax"></a> RFX 함수 구문

각 RFX 함수는 세 개의 매개 변수를 사용 하 고 일부는 선택적으로 4 번째 또는 다섯 번째 매개 변수를 사용 합니다.

- [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) 개체에 대 한 포인터입니다. 에 전달 된 포인터를 따라 전달 하기만 하면 `pFX` `DoFieldExchange` 됩니다.

- 데이터 원본에 표시 되는 열의 이름입니다.

- 레코드 집합 클래스의 해당 필드 데이터 멤버 또는 매개 변수 데이터 멤버의 이름입니다.

- 필드 일부 함수에서 전송 되는 문자열 또는 배열의 최대 길이입니다. 기본값은 255 바이트 이지만 변경 하는 것이 좋습니다. 최대 크기는 INT_MAX 개체의 최대 크기 `CString` (2147483647) 바이트를  기준으로 하지만,이 크기 보다 먼저 드라이버 제한이 발생할 수 있습니다.

- 필드 함수에서 `RFX_Text` 다섯 번째 매개 변수를 사용 하 여 열의 데이터 형식을 지정 하는 경우도 있습니다.

자세한 내용은 *클래스 라이브러리 참조* 의 [매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md) 에서 RFX 함수를 참조 하세요. 매개 변수를 특별 하 게 사용할 수 있는 경우의 예는 [레코드 집합: 합계 가져오기 및 기타 집계 결과 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)를 참조 하세요.

## <a name="rfx-data-types"></a><a name="_core_rfx_data_types"></a> RFX 데이터 형식

클래스 라이브러리는 데이터 원본과 레코드 집합 간에 다양 한 데이터 형식을 전송 하기 위한 RFX 함수를 제공 합니다. 다음 목록에서는 데이터 유형별 RFX 함수를 요약 합니다. 고유한 RFX 함수 호출을 작성 해야 하는 경우 데이터 형식에 따라 이러한 함수에서 선택 합니다.

|함수|데이터 형식|
|--------------|---------------|
|`RFX_Bool`|**BOOL**|
|`RFX_Byte`|**BYTE**|
|`RFX_Binary`|`CByteArray`|
|`RFX_Double`|**`double`**|
|`RFX_Single`|**`float`**|
|`RFX_Int`|**`int`**|
|`RFX_Long`|**`long`**|
|`RFX_LongBinary`|`CLongBinary`|
|`RFX_Text`|`CString`|
|`RFX_Date`|`CTime`|

자세한 내용은 *클래스 라이브러리 참조* 의 [매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md) 에서 RFX 함수 설명서를 참조 하세요. C + + 데이터 형식이 SQL 데이터 형식에 매핑되는 방법에 대 한 자세한 내용은 [sql: sql 및 c + + 데이터 형식 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)에서 c + + 데이터 형식에 매핑된 ANSI Sql 데이터 형식 표를 참조 하세요.

## <a name="see-also"></a>참고 항목

[RFX (레코드 필드 교환)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[레코드 필드 교환: RFX 작동 방식](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[레코드 집합: 레코드 집합 매개 변수화 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[레코드 집합: 데이터 열 동적 바인딩 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[CRecordset 클래스](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange 클래스](../../mfc/reference/cfieldexchange-class.md)
