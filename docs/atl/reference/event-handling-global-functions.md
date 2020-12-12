---
description: '자세한 정보: 이벤트 처리 전역 함수'
title: 이벤트 처리 전역 함수
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWaitWithMessageLoop
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
ms.openlocfilehash: 89e5ec38ff8884f5b99592541df6e397e2dd7116
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139856"
---
# <a name="event-handling-global-functions"></a>이벤트 처리 전역 함수

이 함수는 이벤트 처리기를 제공 합니다.

> [!IMPORTANT]
> 다음 표에 나열 된 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

|Name|설명|
|-|-|
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|필요에 따라 창 메시지를 디스패치 하 여 개체가 신호를 받을 때까지 기다립니다.|

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="atlwaitwithmessageloop"></a><a name="atlwaitwithmessageloop"></a> AtlWaitWithMessageLoop

필요에 따라 창 메시지를 디스패치하는 중에 개체가 신호를 받는 동안 대기합니다.

> [!IMPORTANT]
> 이 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```

### <a name="parameters"></a>매개 변수

*hEvent*<br/>
진행 대기할 개체의 핸들입니다.

### <a name="return-value"></a>반환 값

개체가 신호를 받으면 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

이는 개체의 이벤트가 발생 하 고 발생 하는 것을 알 수 있지만 대기 하는 동안 창 메시지를 디스패치할 수 있도록 하려는 경우에 유용 합니다.

## <a name="see-also"></a>참조

[함수](../../atl/reference/atl-functions.md)
