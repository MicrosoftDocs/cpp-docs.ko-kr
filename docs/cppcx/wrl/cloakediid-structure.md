---
description: '자세히 알아보기: CloakedIid Structure'
title: CloakedIid 구조체
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::CloakedIid
helpviewer_keywords:
- CloakedIid structure
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
ms.openlocfilehash: 06bddded27882ae1216064aafc311364a8d2fd9f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338788"
---
# <a name="cloakediid-structure"></a>CloakedIid 구조체

`RuntimeClass`지정 된 인터페이스를 `Implements` `ChainInterfaces` IID 목록에서 액세스할 수 없는 및 템플릿에 대 한를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
template<typename T>
struct CloakedIid : T;
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
숨겨진 (숨겨짐) 인터페이스입니다.

## <a name="remarks"></a>설명

다음은 **CloakedIid** 를 사용 하는 방법의 예입니다 `struct MyRuntimeClass : RuntimeClass<CloakedIid<IMyCloakedInterface>> {}` .

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`T`

`CloakedIid`

## <a name="requirements"></a>요구 사항

**헤더:** .h를 구현 합니다.

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목

[Microsoft:: WRL 네임 스페이스](microsoft-wrl-namespace.md)
