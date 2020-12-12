---
description: '자세한 정보: 함수 만들기'
title: Make 함수
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Make
helpviewer_keywords:
- Make function
ms.assetid: 66704143-df99-4a95-904d-ed99607e1034
ms.openlocfilehash: bb83c6c163440f911bc625a8646d1758442b25f6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298905"
---
# <a name="make-function"></a>Make 함수

지정 된 Windows 런타임 클래스를 초기화 합니다. 이 함수를 사용 하 여 동일한 모듈에서 정의 된 구성 요소를 인스턴스화합니다.

## <a name="syntax"></a>구문

```cpp
template <
   typename T,
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
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7,
   TArg8 &&arg8,
   TArg9 &&arg9
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7,
   TArg8 &&arg8
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3
);
template <
   typename T,
   typename TArg1,
   typename TArg2
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2
);
template <
   typename T,
   typename TArg1
>
ComPtr<T> Make(
   TArg1 &&arg1
);
template <
   typename T
>
ComPtr<T> Make();
```

### <a name="parameters"></a>매개 변수

*T*<br/>
에서 상속 되는 사용자 지정 클래스 `WRL::RuntimeClass` 입니다.

*TArg1*<br/>
지정 된 런타임 클래스로 전달 되는 인수 1의 형식입니다.

*TArg2*<br/>
지정 된 런타임 클래스로 전달 되는 인수 2의 형식입니다.

*TArg3*<br/>
지정 된 런타임 클래스로 전달 되는 인수 3의 형식입니다.

*TArg4*<br/>
지정 된 런타임 클래스로 전달 되는 인수 4의 형식입니다.

*TArg5*<br/>
지정 된 런타임 클래스로 전달 되는 인수 5의 형식입니다.

*TArg6*<br/>
지정 된 런타임 클래스로 전달 되는 인수 6의 형식입니다.

*TArg7*<br/>
지정 된 런타임 클래스로 전달 되는 인수 7의 형식입니다.

*TArg8*<br/>
지정 된 런타임 클래스로 전달 되는 인수 8의 형식입니다.

*TArg9*<br/>
지정 된 런타임 클래스로 전달 되는 인수 9의 형식입니다.

*arg1*<br/>
지정 된 런타임 클래스로 전달 되는 인수 1입니다.

*arg2*<br/>
지정 된 런타임 클래스로 전달 되는 인수 2입니다.

*arg3*<br/>
지정 된 런타임 클래스로 전달 되는 인수 3입니다.

*arg4*<br/>
지정 된 런타임 클래스로 전달 되는 인수 4입니다.

*arg5*<br/>
지정 된 런타임 클래스로 전달 되는 인수 5입니다.

*arg6*<br/>
지정 된 런타임 클래스로 전달 되는 인수 6입니다.

*arg7*<br/>
지정 된 런타임 클래스로 전달 되는 인수 7입니다.

*arg8*<br/>
지정 된 런타임 클래스로 전달 되는 인수 8입니다.

*arg9*<br/>
지정 된 런타임 클래스로 전달 되는 인수 9입니다.

## <a name="return-value"></a>반환 값

`ComPtr<T>`성공 하면 개체이 고, 그렇지 않으면 **`nullptr`** 입니다.

## <a name="remarks"></a>설명

예제는 [방법: WRL 구성 요소 직접 인스턴스화](how-to-instantiate-wrl-components-directly.md) 를 참조 하 여이 함수와 [MICROSOFT:: WRL::D Etails:: makeandinitialize](makeandinitialize-function.md)간의 차이점을 알아봅니다.

## <a name="requirements"></a>요구 사항

**헤더:** .h를 구현 합니다.

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목

[Microsoft:: WRL 네임 스페이스](microsoft-wrl-namespace.md)
