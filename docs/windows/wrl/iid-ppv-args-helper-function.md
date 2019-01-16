---
title: IID_PPV_ARGS_Helper 함수
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
ms.openlocfilehash: cae29c70c551701a351cdcf404342ed1634a0e3b
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336473"
---
# <a name="iidppvargshelper-function"></a>IID_PPV_ARGS_Helper 함수

지정 된 인수의 형식에서 파생 되는 확인 된 `IUnknown` 인터페이스입니다.

> [!IMPORTANT]
> 이 템플릿 특수화 WRL 인프라를 지원 하며 코드에서 직접 사용할 수 없습니다. 사용 하 여 [IID_PPV_ARGS](https://msdn.microsoft.com/library/windows/desktop/ee330727.aspx) 대신 합니다.

## <a name="syntax"></a>구문

```cpp
template<typename T>
void** IID_PPV_ARGS_Helper(
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp
);
```

### <a name="parameters"></a>매개 변수

*T*<br/>
인수의 형식은 *pp*합니다.

*pp*<br/>
이중 간접 포인터입니다.

## <a name="return-value"></a>반환 값

인수 *pp* 에 대 한 포인터-에-a-포인터로 캐스팅 **void**합니다.

## <a name="remarks"></a>설명

컴파일 타임 오류가 생성 됩니다 템플릿 매개 변수 *T* 에서 파생 되지 `IUnknown`합니다.

## <a name="requirements"></a>요구 사항

**헤더:** client.h

