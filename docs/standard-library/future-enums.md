---
description: '자세한 정보: &lt; 미래 &gt; 열거형'
title: '&lt;future&gt; 열거형'
ms.date: 11/04/2016
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
ms.openlocfilehash: 473533d5d22ac5708af7a86cc58a57ac033545af
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232137"
---
# <a name="ltfuturegt-enums"></a>&lt;future&gt; 열거형

[future_errc](#future_errc)\
[future_status](#future_status)\
[시작](#launch)

## <a name="future_errc-enumeration"></a><a name="future_errc"></a> future_errc 열거형

[future_error](../standard-library/future-error-class.md) 클래스에서 보고한 모든 오류에 대해 기호화된 이름을 제공합니다.

```cpp
class future_errc {
   broken_promise,
   future_already_retrieved,
   promise_already_satisfied,
   no_state
   };
```

## <a name="future_status-enumeration"></a><a name="future_status"></a> future_status 열거형

timed wait 함수가 반환할 수 있는 이유에 대해 기호화된 이름을 제공합니다.

```cpp
enum future_status{
    ready,
    timeout,
    deferred
};
```

## <a name="launch-enumeration"></a><a name="launch"></a> 시작 열거

템플릿 함수 [async](../standard-library/future-functions.md#async)에 가능한 모드를 설명하는 비트 마스크 형식을 나타냅니다.

```cpp
class launch{
   async,
   deferred
   };
```

## <a name="see-also"></a>참고 항목

[\<future>](../standard-library/future.md)
