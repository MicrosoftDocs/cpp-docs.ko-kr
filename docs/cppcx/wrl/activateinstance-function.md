---
title: ActivateInstance 함수
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Windows::Foundation::ActivateInstance
- client/ABI::Windows::Foundation::ActivateInstance
helpviewer_keywords:
- ActivateInstance function
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
ms.openlocfilehash: 43aa34153f0e71dd665090243ff2288bff704404
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029082"
---
# <a name="activateinstance-function"></a>ActivateInstance 함수

등록 하 고 ID가 지정 된 클래스에 정의 된 지정 된 형식의 인스턴스를 검색 합니다.

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
활성화 하는 형식입니다.

*activatableClassId*<br/>
매개 변수를 정의 하는 클래스 ID의 이름을 *T*합니다.

*instance*<br/>
이 작업이 완료 될 때, 인스턴스에 대 한 참조 *T*합니다.

## <a name="return-value"></a>반환 값

성공 하면 s_ok이 고 그렇지 않은 경우 오류의 원인을 나타내는 HRESULT 오류가 발생 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** client.h

**네임스페이스:** Windows::Foundation

## <a name="see-also"></a>참고자료

[Windows::Foundation 네임스페이스](windows-foundation-namespace.md)