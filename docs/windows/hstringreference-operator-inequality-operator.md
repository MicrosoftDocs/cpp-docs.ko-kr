---
title: 'Hstringreference:: Operator! = 연산자 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator!=
dev_langs:
- C++
ms.assetid: 01ab6691-1fc7-4feb-85f0-fe795593a160
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 996ead81a72fb3cc58544576059a8347972e2a6b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429073"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator!= 연산자

두 매개 변수가 같지 않은지를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
inline bool operator==(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()

inline bool operator!=(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()  
```

### <a name="parameters"></a>매개 변수

*lhs*<br/>
비교할 첫 번째 매개 변수입니다. *lhs* 수는 **HStringReference** 개체 또는 HSTRING 핸들입니다.

*rhs*<br/>
비교할 두 번째 매개 변수입니다.  *rhs* 수는 **HStringReference** 개체 또는 HSTRING 핸들입니다.

## <a name="return-value"></a>반환 값

**true** 경우는 *lhs* 하 고 *rhs* 매개 변수는 같고, 그렇지 않으면 **false**합니다.

## <a name="requirements"></a>요구 사항

**헤더:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>참고 항목

[HStringReference 클래스](../windows/hstringreference-class.md)