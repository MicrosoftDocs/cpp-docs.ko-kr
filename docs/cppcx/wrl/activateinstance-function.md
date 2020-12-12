---
description: '자세한 정보: 기능 인스턴스 함수'
title: ActivateInstance 함수
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Windows::Foundation::ActivateInstance
- client/ABI::Windows::Foundation::ActivateInstance
helpviewer_keywords:
- ActivateInstance function
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
ms.openlocfilehash: 03d7b67810ee2ab287072546b098f81f43687233
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287855"
---
# <a name="activateinstance-function"></a>ActivateInstance 함수

지정 된 클래스 ID에 정의 된 지정 된 형식의 인스턴스를 등록 하 고 검색 합니다.

## <a name="syntax"></a>구문

```cpp
template<typename T>
inline HRESULT ActivateInstance(
   _In_ HSTRING activatableClassId,
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance
);
```

### <a name="parameters"></a>매개 변수

*T*<br/>
활성화할 형식입니다.

*activatableClassId*<br/>
매개 변수 *T* 를 정의 하는 클래스 ID의 이름입니다.

*인스턴스*<br/>
이 작업이 완료 되 면 *T* 의 인스턴스에 대 한 참조입니다.

## <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 오류의 원인을 나타내는 오류 HRESULT가 발생 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** client.h

**네임 스페이스:** Windows:: Foundation

## <a name="see-also"></a>참고 항목

[Windows:: Foundation 네임 스페이스](windows-foundation-namespace.md)
