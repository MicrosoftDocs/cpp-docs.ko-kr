---
title: 'Eventsource:: Invokeall 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::InvokeAll
dev_langs:
- C++
helpviewer_keywords:
- InvokeAll method
ms.assetid: 1506618f-0421-4428-a4d0-4ea2b10a3bf6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 57450abdef0a6b25731405e092520ec5589972a1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613737"
---
# <a name="eventsourceinvokeall-method"></a>EventSource::InvokeAll 메서드

현재 연결 된 각 이벤트 처리기를 호출 [EventSource](../windows/eventsource-class.md) 지정 된 인수 형식 및 인수를 사용 하 여 개체입니다.

## <a name="syntax"></a>구문

```cpp
void InvokeAll();
template <
   typename T0
>
void InvokeAll(
   T0arg0
);
template <
   typename T0,
   typename T1
>
void InvokeAll(
   T0arg0,
   T1arg1
);
template <
   typename T0,
   typename T1,
   typename T2
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8,
   typename T9
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8,
   T9arg9
);
```

### <a name="parameters"></a>매개 변수

*T0*  
0번째 이벤트 처리기 인수 형식입니다.

*T1*  
첫 번째 이벤트 처리기 인수 형식입니다.

*T2*  
두 번째 이벤트 처리기 인수 형식입니다.

*T3*  
세 번째 이벤트 처리기 인수 형식입니다.

*T4*  
네 번째 이벤트 처리기 인수 형식입니다.

*T5*  
다섯 번째 이벤트 처리기 인수 형식입니다.

*T6*  
여섯 번째 이벤트 처리기 인수 형식입니다.

*T7*  
일곱 번째 이벤트 처리기 인수 형식입니다.

*T8*  
여덟 번째 이벤트 처리기 인수 형식입니다.

*T9*  
아홉 번째 이벤트 처리기 인수 형식입니다.

*arg0*  
0번째 이벤트 처리기 인수입니다.

*arg1*  
첫 번째 이벤트 처리기 인수입니다.

*Arg2*  
두 번째 이벤트 처리기 인수입니다.

*arg3*  
세 번째 이벤트 처리기 인수입니다.

*arg4*  
네 번째 이벤트 처리기 인수입니다.

*arg5*  
다섯 번째 이벤트 처리기 인수입니다.

*a r g 6*  
여섯 번째 이벤트 처리기 인수입니다.

*arg7*  
일곱 번째 이벤트 처리기 인수입니다.

*arg8*  
여덟 번째 이벤트 처리기 인수입니다.

*arg9*  
아홉 번째 이벤트 처리기 인수입니다.

## <a name="requirements"></a>요구 사항

**헤더:** event.h

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목
[EventSource 클래스](../windows/eventsource-class.md)