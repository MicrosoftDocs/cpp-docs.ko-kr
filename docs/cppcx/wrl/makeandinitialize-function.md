---
description: '자세한 정보: MakeAndInitialize 함수'
title: MakeAndInitialize 함수
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAndInitialize
ms.assetid: 71ceeb12-d2a2-4317-b010-3dcde1b39467
ms.openlocfilehash: 108da1f19d6956527f06e5239f5ce2e14716d664
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317924"
---
# <a name="makeandinitialize-function"></a>MakeAndInitialize 함수

지정 된 Windows 런타임 클래스를 초기화 합니다. 이 함수를 사용 하 여 동일한 모듈에서 정의 된 구성 요소를 인스턴스화합니다.

## <a name="syntax"></a>구문

```cpp
template <
    typename T,
    typename I,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8,
    typename TArg9>
HRESULT MakeAndInitialize(
    _Outptr_result_nullonfailure_ I** ppvObject,
    TArg1 &&arg1,
    TArg2 &&arg2,
    TArg3 &&arg3,
    TArg4 &&arg4,
    TArg5 &&arg5,
    TArg6 &&arg6,
    TArg7 &&arg7,
    TArg8 &&arg8,
    TArg9 &&arg9) throw()
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

HRESULT 값입니다.

## <a name="remarks"></a>설명

예제는 [방법: WRL 구성 요소 직접 인스턴스화](how-to-instantiate-wrl-components-directly.md) 를 참조 하 여이 함수와 [Microsoft:: WRL::](make-function.md)간의 차이점을 알아봅니다.

## <a name="requirements"></a>요구 사항

**헤더:** .h를 구현 합니다.

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="see-also"></a>참고 항목

[Microsoft:: WRL::D etails 네임 스페이스](microsoft-wrl-details-namespace.md)
