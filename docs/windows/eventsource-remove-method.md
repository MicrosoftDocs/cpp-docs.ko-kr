---
title: 'Eventsource:: Remove 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::Remove
dev_langs:
- C++
helpviewer_keywords:
- Remove method
ms.assetid: afafedf5-3665-4408-a639-fb6884f7c5f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 00f3275095648a41eb25d10bac1f34637b2ac242
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604574"
---
# <a name="eventsourceremove-method"></a>EventSource::Remove 메서드

현재 연결 된 이벤트 처리기 집합에서 지정 된 이벤트 등록 토큰을 나타내는 이벤트 처리기를 삭제 **EventSource** 개체입니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>매개 변수

*token*  
이벤트 처리기를 나타내는 핸들입니다. 이 토큰은 이벤트 처리기를 등록 된 경우 반환 된 합니다 [add ()](../windows/eventsource-add-method.md) 메서드.

## <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 오류를 나타내는 HRESULT입니다.

## <a name="remarks"></a>설명

에 대 한 자세한 내용은 `EventRegistrationToken` 구조체를 참조 하세요를 **Windows::Foundation::EventRegistrationToken 구조** 항목에는 **Windows 런타임** 설명서를 참조 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** event.h

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목
[EventSource 클래스](../windows/eventsource-class.md)