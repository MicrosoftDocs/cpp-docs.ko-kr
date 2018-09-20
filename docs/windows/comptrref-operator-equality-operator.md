---
title: 'Comptrref:: Operator = = 연산자 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator==
dev_langs:
- C++
ms.assetid: 95fcf781-b473-4317-88cd-e938778d3c3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 78daa0ad22ad3bb6a63900d4c2f69d5eafb5cb6b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372125"
---
# <a name="comptrrefoperator-operator"></a>ComPtrRef::operator== 연산자

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)  
);

bool operator==(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator==(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>매개 변수

*a*<br/>
에 대 한 참조를 **ComPtrRef** 개체입니다.

*b*<br/>
다른에 대 한 참조가 **ComPtrRef** 개체 또는 무명 형식에 대 한 포인터 (`void*`).

## <a name="return-value"></a>반환 값

첫 번째 연산자 생성 **true** 하는 경우 개체 *는* 개체와 동일한 지 *b*고, 그렇지 않으면 **false**합니다.

두 번째와 세 번째 연산자에서 생성 **true** 하는 경우 개체 *는* 값과 같음 **nullptr**고, 그렇지 않으면 **false**합니다.

네 번째와 다섯 번째 연산자에서 생성 **true** 경우 개체 *는* 개체와 동일한 지 *b*고, 그렇지 않으면 **false**합니다.

## <a name="remarks"></a>설명

나타냅니다 두 **ComPtrRef** 개체는 동일 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** client.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>참고 항목

[Microsoft::WRL::Details 네임스페이스](../windows/microsoft-wrl-details-namespace.md)<br/>
[ComPtrRef 클래스](../windows/comptrref-class.md)