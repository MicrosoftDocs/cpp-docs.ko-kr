---
description: _Execute_onexit_table, _initialize_onexit_table, _register_onexit_function에 대해 자세히 알아보세요.
title: _execute_onexit_table, _initialize_onexit_table, _register_onexit_function
ms.date: 4/2/2020
api_name:
- _execute_onexit_table
- _initialize_onexit_table
- _register_onexit_function
- _o__execute_onexit_table
- _o__initialize_onexit_table
- _o__register_onexit_function
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _execute_onexit_table
- process/_execute_onexit_table
- _initialize_onexit_table
- process/_initialize_onexit_table
- _register_onexit_function
- process/_register_onexit_function
helpviewer_keywords:
- _execute_onexit_table function
- _initialize_onexit_table function
- _register_onexit_function function
ms.assetid: ad9e4149-d4ad-4fdf-aaaf-cf786fcb4473
ms.openlocfilehash: 5bd0449c4b353c6a417e145f864b07794ae40ca3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300075"
---
# <a name="_execute_onexit_table-_initialize_onexit_table-_register_onexit_function"></a>_execute_onexit_table, _initialize_onexit_table, _register_onexit_function

종료 시 호출할 루틴을 관리합니다.

## <a name="syntax"></a>구문

```
int _initialize_onexit_table(
    _onexit_table_t* table
    );

int _register_onexit_function(
    _onexit_table_t* table,
    _onexit_t        function
    );

int _execute_onexit_table(
    _onexit_table_t* table
    );
```

#### <a name="parameters"></a>매개 변수

*table*<br/>
[in, out] onexit 함수 테이블에 대한 포인터입니다.

*function*<br/>
[in] onexit 함수 테이블에 추가할 함수에 대한 포인터입니다.

## <a name="return-value"></a>반환 값

성공하면 0을 반환합니다. 그렇지 않으면 음수 값을 반환합니다.

## <a name="remarks"></a>설명

이러한 함수는 C 런타임을 지원하는 데 사용된 인프라 구현 세부 정보이고 코드에서 직접 호출하면 안 됩니다. C 런타임은 *onexit 함수 테이블* 을 사용 하 여, 및에 대 한 호출로 등록 된 함수의 시퀀스를 나타냅니다 `atexit` `at_quick_exit` `_onexit` . onexit 함수 테이블 데이터 구조체는 C 런타임의 불투명한 구현 세부 정보이고 해당 데이터 멤버의 순서와 의미는 변경될 수 있습니다. 데이터 멤버는 외부 코드를 통해 검사되지 않아야 합니다.

`_initialize_onexit_table` 함수는 onexit 함수 테이블을 초기 값으로 초기화합니다.  onexit 함수 테이블이 `_register_onexit_function` 또는 `_execute_onexit_table`에 전달되기 전에 이 함수를 호출해야 합니다.

`_register_onexit_function` 함수는 onexit 함수 테이블의 끝에 함수를 추가합니다.

`_execute_onexit_table` 함수는 onexit 함수 테이블의 모든 함수를 실행하고, 테이블을 지우고 나서, 반환됩니다. `_execute_onexit_table`을 호출한 후 테이블은 잘못된 상태가 되므로 다시 사용되기 전에 `_initialize_onexit_table`을 호출하여 다시 초기화해야 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|`_initialize_onexit_table function`, `_register_onexit_function`, `_execute_onexit_table`|C, C + +: \<process.h>|

`_initialize_onexit_table`, `_register_onexit_function` 및 함수는 `_execute_onexit_table` Microsoft 전용입니다. 호환성에 대한 내용은 [호환성](../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[atexit](../c-runtime-library/reference/atexit.md)<br/>
[exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)
