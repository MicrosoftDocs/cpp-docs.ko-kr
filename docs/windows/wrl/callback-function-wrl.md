---
title: 콜백 함수 (WRL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Callback
ms.assetid: afb15d25-3230-44f7-b321-e17c54872943
ms.openlocfilehash: e5cccd337514df34729fc916900a7b16a15596fc
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336769"
---
# <a name="callback-function-wrl"></a>콜백 함수 (WRL)

멤버 함수가 콜백 메서드인 개체를 만듭니다.

## <a name="syntax"></a>구문

```cpp
template<
   typename TDelegateInterface,
   typename TCallback
>
ComPtr<TDelegateInterface> Callback(
   TCallbackcallback
);
template<
   typename TDelegateInterface,
   typename TCallbackObject
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)()
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5,
   TArg6)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5,
   TArg6,
   TArg7)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5,
   TArg6,
   TArg7,
   TArg8)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8,
   typename TArg9
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5,
   TArg6,
   TArg7,
   TArg8,
   TArg9)
);
```

### <a name="parameters"></a>매개 변수

*TDelegateInterface*<br/>
이벤트가 발생할 때 호출할 대리자의 인터페이스를 지정하는 템플릿 매개 변수입니다.

*TCallback*<br/>
개체 및 해당 콜백 멤버 함수를 나타내는 개체 형식을 지정하는 템플릿 매개 변수입니다.

*TCallbackObject*<br/>
이벤트가 발생할 때 호출할 메서드가 메서드 함수인 개체를 지정하는 템플릿 매개 변수입니다.

*TArg1*<br/>
첫 번째 콜백 메서드 인수의 형식을 지정하는 템플릿 매개 변수입니다.

*TArg2*<br/>
두 번째 콜백 메서드 인수의 형식을 지정하는 템플릿 매개 변수입니다.

*TArg3*<br/>
세 번째 콜백 메서드 인수의 형식을 지정하는 템플릿 매개 변수입니다.

*TArg4*<br/>
네 번째 콜백 메서드 인수의 형식을 지정하는 템플릿 매개 변수입니다.

*TArg5*<br/>
다섯 번째 콜백 메서드 인수의 형식을 지정하는 템플릿 매개 변수입니다.

*TArg6*<br/>
여섯 번째 콜백 메서드 인수의 형식을 지정하는 템플릿 매개 변수입니다.

*TArg7*<br/>
일곱 번째 콜백 메서드 인수의 형식을 지정하는 템플릿 매개 변수입니다.

*TArg8*<br/>
여덟 번째 콜백 메서드 인수의 형식을 지정하는 템플릿 매개 변수입니다.

*TArg9*<br/>
아홉 번째 콜백 메서드 인수의 형식을 지정하는 템플릿 매개 변수입니다.

*callback*<br/>
콜백 개체 및 해당 멤버 함수를 나타내는 개체입니다.

*object*<br/>
이벤트가 발생할 때 해당 멤버 함수를 호출하는 개체입니다.

*method*<br/>
이벤트가 발생할 때 호출할 멤버 함수입니다.

## <a name="return-value"></a>반환 값

멤버 함수가 지정된 콜백 메서드인 개체입니다.

## <a name="remarks"></a>설명

대리자 개체의 기본 이어야 합니다 `IUnknown`이 아니라 `IInspectable`합니다.

## <a name="requirements"></a>요구 사항

**헤더:** event.h

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목

[Microsoft::WRL 네임스페이스](microsoft-wrl-namespace.md)