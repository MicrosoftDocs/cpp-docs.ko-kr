---
title: ActivationFactoryCallback 함수 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::ActivationFactoryCallback
dev_langs:
- C++
helpviewer_keywords:
- ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 62efb2b1aa2cd2caa0c5701696689ea3df19f962
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443620"
---
# <a name="activationfactorycallback-function"></a>ActivationFactoryCallback 함수

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
inline HRESULT STDAPICALLTYPE ActivationFactoryCallback(
   HSTRING activationId,
   IActivationFactory **ppFactory
);
```

### <a name="parameters"></a>매개 변수

*activationId*<br/>
런타임 클래스 이름을 지정 하는 문자열에 대 한 핸들입니다.

*ppFactory*<br/>
이 작업이 완료 되 면 매개 변수에 해당 하는 활성화 팩터리 *activationId*합니다.

## <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 실패를 설명하는 HRESULT가 발생합니다. 가능한 실패 Hresult는 CLASS_E_CLASSNOTAVAILABLE 및 E_INVALIDARG입니다.

## <a name="remarks"></a>설명

지정 된 활성화 ID에 대 한 활성화 팩터리를 가져옵니다.

Windows 런타임 런타임 클래스 이름을 사용 하 여 지정 된 개체를 요청 하려면이 콜백 함수를 호출 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** module.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>참고 항목

[Microsoft::WRL::Details 네임스페이스](../windows/microsoft-wrl-details-namespace.md)