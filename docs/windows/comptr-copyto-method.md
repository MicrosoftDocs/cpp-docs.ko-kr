---
title: 'Comptr:: Copyto 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::CopyTo
dev_langs:
- C++
helpviewer_keywords:
- CopyTo method
ms.assetid: 8801bc49-6db4-4393-a55f-a701ae3b8718
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c9b84cbcc970183222ed06752dc61b5672615868
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405387"
---
# <a name="comptrcopyto-method"></a>ComPtr::CopyTo 메서드

현재 또는 지정 된 인터페이스와 관련 된 복사 **ComPtr** 지정 된 포인터에 대 한 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CopyTo(
   _Deref_out_ InterfaceType** ptr
);

HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ void** ptr
) const;

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
) const;
```

### <a name="parameters"></a>매개 변수

*U*<br/>
형식 이름.

*ptr*<br/>
이 작업이 완료 될 때 요청된 된 인터페이스에 대 한 포인터입니다.

*riid*<br/>
인터페이스 ID입니다.

## <a name="return-value"></a>반환 값

성공 하면 s_ok이 고 그렇지 않은 경우 이유를 나타내는 HRESULT 암시적 `QueryInterface` 작업이 실패 했습니다.

## <a name="remarks"></a>설명

와 연결 된 인터페이스에 대 한 포인터의 복사본을 반환 하는 첫 번째 함수 **ComPtr**합니다. 이 함수는 항상 S_OK를 반환합니다.

수행 하는 두 번째 함수는 `QueryInterface` 와 연결 된 인터페이스에 대 한 작업 **ComPtr** 으로 지정한 인터페이스에 대 한 합니다 *riid* 매개 변수입니다.

수행 하는 세 번째 함수는 `QueryInterface` 와 연결 된 인터페이스에 대 한 작업 **ComPtr** 의 기본 인터페이스에 대 한 합니다 *U* 매개 변수.

## <a name="requirements"></a>요구 사항

**헤더:** client.h

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목

[ComPtr 클래스](../windows/comptr-class.md)