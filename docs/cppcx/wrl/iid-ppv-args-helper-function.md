---
description: IID_PPV_ARGS_Helper 함수에 대해 자세히 알아보세요.
title: IID_PPV_ARGS_Helper 함수
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
ms.openlocfilehash: 7003a3270a6fdb2070055e0059b106f55324c63e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229147"
---
# <a name="iid_ppv_args_helper-function"></a>IID_PPV_ARGS_Helper 함수

지정 된 인수의 형식이 인터페이스에서 파생 되는지 확인 `IUnknown` 합니다.

> [!IMPORTANT]
> 이 템플릿 특수화는 WRL 인프라를 지원 하며 사용자 코드에서 직접 사용 하기 위한 것이 아닙니다. 대신 [IID_PPV_ARGS](/windows/win32/api/combaseapi/nf-combaseapi-iid_ppv_args) 를 사용 해야 합니다.

## <a name="syntax"></a>구문

```cpp
template<typename T>
void** IID_PPV_ARGS_Helper(
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp
);
```

### <a name="parameters"></a>매개 변수

*T*<br/>
인수 *pp* 의 유형입니다.

*페이지*<br/>
이중 간접 포인터입니다.

## <a name="return-value"></a>반환 값

인수 *pp* 를에 대 한 포인터 포인터에 캐스팅 **`void`** 합니다.

## <a name="remarks"></a>설명

템플릿 매개 변수 *T* 가에서 파생 되지 않으면 컴파일 시간 오류가 발생 `IUnknown` 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** client.h
