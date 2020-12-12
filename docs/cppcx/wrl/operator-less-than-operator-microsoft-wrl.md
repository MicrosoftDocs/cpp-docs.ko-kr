---
description: '자세한 정보: 연산자 &lt; 연산자 (Microsoft:: WRL)'
title: '연산자 &lt; 연산자 (Microsoft:: WRL)'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::operator<
ms.assetid: bfae0e1c-1648-482b-99c2-3217d62aba46
ms.openlocfilehash: 1edbb8218ef07355040bd05ab99db8f97be1cb59
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330777"
---
# <a name="operatorlt-operator-microsoftwrl"></a>연산자 &lt; 연산자 (Microsoft:: WRL)

한 개체의 주소가 다른 개체 보다 적은지 여부를 확인 합니다.

## <a name="syntax"></a>구문

```cpp
template<class T, class U>
bool operator<(const ComPtr<T>& a, const ComPtr<U>& b) throw();
template<class T, class U>
bool operator<(const Details::ComPtrRef<ComPtr<T>>& a, const Details::ComPtrRef<ComPtr<U>>& b) throw();
```

### <a name="parameters"></a>매개 변수

*은*<br/>
왼쪽 개체입니다.

*b*<br/>
오른쪽 개체입니다.

## <a name="return-value"></a>반환 값

**`true`** 의 주소가 *b* 의 *주소* 보다 작은 경우 그렇지 않으면 **`false`** 입니다.

## <a name="requirements"></a>요구 사항

**헤더:** client.h

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목

[Microsoft:: WRL 네임 스페이스](microsoft-wrl-namespace.md)
