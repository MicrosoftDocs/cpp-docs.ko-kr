---
description: '자세히 알아보기: &lt; 새로 만들기&gt;'
title: '&lt;신규&gt;'
ms.date: 11/04/2016
f1_keywords:
- <new>
helpviewer_keywords:
- new header
ms.assetid: 218e2a15-34e8-4ef3-9122-1e90eccf8559
ms.openlocfilehash: c99c036a7b4065e207bfe9ad71eb86e6d5f01d0f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338150"
---
# <a name="ltnewgt"></a>&lt;신규&gt;

프로그램이 제어하는 스토리지의 할당 및 해제를 제어하는 여러 형식 및 함수를 정의합니다. 또한 스토리지 관리 오류에 대한 보고를 위해 구성 요소를 정의합니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<new>

**네임스페이스:** std

## <a name="remarks"></a>설명

이 헤더에 선언된 함수 중 일부는 교체할 수 있습니다. 구현은 이 문서에서 해당 동작을 설명하는 기본 버전을 제공합니다. 그러나 프로그램에서 동일한 서명으로 함수를 정의하여 링크 타임에 기본 버전을 바꿀 수 있습니다. 대체 버전은 이 문서에 설명된 요구 사항을 충족해야 합니다.

## <a name="members"></a>멤버

### <a name="objects"></a>개체

|Name|설명|
|-|-|
|[nothrow](../standard-library/new-functions.md#nothrow)|및 버전의 인수로 사용할 개체를 제공 합니다 **`nothrow`** **`new`** **`delete`** .|

### <a name="typedefs"></a>Typedefs

|Name|설명|
|-|-|
|[new_handler](../standard-library/new-typedefs.md#new_handler)|새 처리기로 사용하기에 적합한 함수를 가리키는 형식입니다.|
|[hardware_constructive_interference_size](../standard-library/new-typedefs.md#hardware_destructive_interference_size)||
|[hardware_destructive_interference_size](../standard-library/new-typedefs.md#hardware_destructive_interference_size)||

### <a name="functions"></a>함수

|Name|설명|
|-|-|
|[get_new_handler](../standard-library/new-functions.md#get_new_handler)||
|[launder](../standard-library/new-functions.md#launder)||
|[set_new_handler](../standard-library/new-functions.md#set_new_handler)|new가 메모리 할당 시도에 실패할 때 호출되는 사용자 함수를 설치합니다.|

### <a name="operators"></a>연산자

|Name|설명|
|-|-|
|[operator delete](../standard-library/new-operators.md#op_delete)|개별 개체에 대해 스토리지를 할당 해제하기 위해 delete 식에서 호출되는 함수입니다.|
|[operator delete&#91;&#93;](../standard-library/new-operators.md#op_delete_arr)|개체 배열에 대해 스토리지를 할당 해제하기 위해 delete 식에서 호출되는 함수입니다.|
|[operator new](../standard-library/new-operators.md#op_new)|개별 개체에 대해 스토리지를 할당하기 위해 new 식에서 호출되는 함수입니다.|
|[operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)|개체 배열에 대해 스토리지를 할당하기 위해 new 식에서 호출되는 함수입니다.|

### <a name="enums"></a>열거형

|Name|설명|
|-|-|
|[align_val_t](../standard-library/new-operators.md#op_align_val_t)||

### <a name="classes"></a>클래스

|이름|설명|
|-|-|
|[bad_alloc 클래스](../standard-library/bad-alloc-class.md)|이 클래스는 할당 요청이 성공하지 못했음을 나타내기 위해 발생하는 예외를 설명합니다.|
|[bad_array_new_length 클래스](../standard-library/bad-array-new-length.md)||
|[nothrow_t 클래스](../standard-library/nothrow-t-structure.md)|이 클래스는 함수가 예외를 발생시키는 대신 null 포인터를 반환하여 할당 오류를 보고해야 함을 나타내기 위해 new 연산자에 대한 함수 매개 변수로 사용됩니다.|

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
