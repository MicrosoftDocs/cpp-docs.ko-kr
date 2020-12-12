---
description: '자세히 알아보기: &lt; 미래&gt;'
title: '&lt;future&gt;'
ms.date: 11/04/2016
f1_keywords:
- <future>
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
ms.openlocfilehash: 67c204f636ee9249e9c714df87a02ff6c6ff3149
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324202"
---
# <a name="ltfuturegt"></a>&lt;future&gt;

\<future>별도 스레드에서 함수 실행을 간소화 하 고 결과를 검색 하는 데 사용할 수 있는 클래스 템플릿과 지원 템플릿을 정의 하려면 표준 헤더를 포함 합니다. 결과는 함수에서 반환되는 값 또는 함수에서 발생했지만 함수에 catch되지 않은 예외 중 하나입니다.

이 헤더는 동시성 런타임(ConcRT)을 사용하므로 다른 ConcRT 메커니즘과 함께 사용할 수 있습니다. ConcRT에 대한 자세한 내용은 [동시성 런타임](../parallel/concrt/concurrency-runtime.md)을 참조하세요.

## <a name="syntax"></a>구문

```cpp
#include <future>
```

## <a name="remarks"></a>설명

> [!NOTE]
> **/Clr** 을 사용 하 여 컴파일된 코드에서이 헤더는 차단 됩니다.

*비동기 공급자* 는 함수 호출의 결과를 저장합니다. *비동기 반환 개체* 는 함수 호출 결과를 검색하는 데 사용됩니다. *연결된 비동기 상태* 를 통해 비동기 공급자와 비동기 반환 개체 하나 이상 사이에서 통신할 수 있습니다.

프로그램에서는 연결된 비동기 상태 개체를 직접 만들지 않습니다. 프로그램에서는 필요할 때마다 비동기 공급자를 만들고 이를 기반으로 연결된 비동기 상태를 공급자와 공유하는 비동기 반환 개체를 만듭니다. 비동기 공급자와 비동기 반환 개체는 공유된 연결된 비동기 상태를 포함하는 개체를 관리합니다. 연결된 비동기 상태를 참조하는 마지막 개체가 해당 상태를 해제하면 연결된 비동기 상태를 포함하는 개체가 삭제됩니다.

연결된 비동기 상태가 없는 비동기 공급자 또는 비동기 반환 개체는 *비어 있습니다*.

연결된 비동기 상태는 해당 비동기 공급자가 반환 값을 저장했거나 예외를 저장한 경우에만 *준비* 입니다.

템플릿 함수와 `async` 클래스 템플릿 `promise` 및는 `packaged_task` 비동기 공급자입니다. 클래스 템플릿과 `future` `shared_future` 비동기 반환 개체에 대해 설명 합니다.

각 클래스 템플릿 `promise` , 및에는 `future` `shared_future` 형식에 대 한 특수화 **`void`** 와 참조로 값을 저장 하 고 검색 하는 부분 특수화가 있습니다. 이러한 특수화는 반환된 값을 저장 및 검색하는 함수의 시그니처와 의미 체계에만 있는 기본 템플릿과 다릅니다.

`future` `shared_future` 이전 버전과의 호환성을 위해 유지 되는 한 가지 경우를 제외 하 고, 클래스 템플릿은 소멸자에서 차단 되지 않습니다. 다른 모든 미래와 달리 `future` `shared_future` 로 시작 되는 작업에 연결 된 경우 소멸자가 `std::async` 차단 됩니다. 즉,이 스레드가 또는를 아직 호출 하지 않은 경우에는 차단 되 `.get()` `.wait()` 고 작업은 계속 실행 됩니다. 다음 유용성 메모는 초안 표준에서 `std::async`에 대한 설명에 추가되었습니다. "[참고: std::async에서 가져온 future가 로컬 범위 외부로 이동되면 해당 future를 사용하는 다른 코드는 공유된 상태가 준비가 되도록 future의 소멸자가 차단될 수 있다는 것을 인식해야 합니다. - 메모 종료]" 다른 모든 경우에는 `future` 및 `shared_future` 소멸자가 필요하고 절대 차단되지 않도록 보장됩니다.

## <a name="members"></a>멤버

### <a name="classes"></a>클래스

|이름|설명|
|----------|-----------------|
|[future 클래스](../standard-library/future-class.md)|비동기 반환 개체를 설명합니다.|
|[future_error 클래스](../standard-library/future-error-class.md)|`future` 개체를 관리하는 형식의 메서드에서 throw될 수 있는 예외 개체를 설명합니다.|
|[packaged_task 클래스](../standard-library/packaged-task-class.md)|호출 시그니처 `Ty(ArgTypes...)`가 포함된 호출 래퍼인 비동기 공급자를 설명합니다. 비동기 공급자의 연결된 비동기 상태에는 잠재적 결과와 함께 호출 가능 개체의 복사본이 포함됩니다.|
|[약속 클래스](../standard-library/promise-class.md)|비동기 공급자를 설명합니다.|
|[shared_future 클래스](../standard-library/shared-future-class.md)|비동기 반환 개체를 설명합니다. `future` 개체와는 달리 `shared_future` 개체의 경우 원하는 수만큼 비동기 공급자에 연결할 수 있습니다.|

### <a name="structures"></a>구조체

|Name|설명|
|----------|-----------------|
|[is_error_code_enum 구조체](../standard-library/is-error-code-enum-structure.md)|`future_errc`가 `error_code`를 저장하는 데 적합함을 나타내는 특수화입니다.|
|[uses_allocator 구조체](../standard-library/uses-allocator-structure.md)|항상 true인 특수화입니다.|

### <a name="functions"></a>함수

|Name|설명|
|----------|-----------------|
|[async](../standard-library/future-functions.md#async)|비동기 공급자를 나타냅니다.|
|[future_category](../standard-library/future-functions.md#future_category)|`future` 개체와 연결된 오류의 특징을 결정하는 `error_category` 개체에 대한 참조를 반환합니다.|
|[make_error_code](../standard-library/future-functions.md#make_error_code)|`future` 오류의 특징을 결정하는 `error_category` 개체가 포함된 `error_code`를 만듭니다.|
|[make_error_condition](../standard-library/future-functions.md#make_error_condition)|`future` 오류의 특징을 결정하는 `error_category` 개체가 포함된 `error_condition`를 만듭니다.|
|[스왑을](../standard-library/future-functions.md#swap)|`promise` 개체 하나의 연결된 비동기 상태를 다른 개체의 상태와 교환합니다.|

### <a name="enumerations"></a>열거형

|Name|설명|
|----------|-----------------|
|[future_errc](../standard-library/future-enums.md#future_errc)|`future_error` 클래스에서 보고한 오류에 대해 기호화된 이름을 제공합니다.|
|[future_status](../standard-library/future-enums.md#future_status)|timed wait 함수가 반환할 수 있는 이유에 대해 기호화된 이름을 제공합니다.|
|[시작](../standard-library/future-enums.md#launch)|템플릿 함수 `async`에 가능한 모드를 설명하는 비트 마스크 형식을 나타냅니다.|

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)
