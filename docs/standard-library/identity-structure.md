---
description: '자세히 알아보기: id 구조'
title: identity 구조체
ms.date: 11/04/2016
f1_keywords:
- utility/std::identity
helpviewer_keywords:
- identity class
- identity structure
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
ms.openlocfilehash: 753a3b697eb2a77dd102f681403fd23d7062cb36
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231760"
---
# <a name="identity-structure"></a>identity 구조체

형식 정의를 템플릿 매개 변수로 제공하는 구조체입니다.

## <a name="syntax"></a>구문

```cpp
struct identity {
   typedef Type type;
   Type operator()(const Type& left) const;
};
```

### <a name="parameters"></a>매개 변수

*비어*\
식별할 값입니다.

## <a name="remarks"></a>설명

클래스에는 템플릿 매개 변수 Type과 동일한 public 형식 정의 `type`이 포함되어 있습니다. 템플릿 함수 [forward](../standard-library/utility-functions.md#forward)와 함께 사용되어 함수 매개 변수가 원하는 형식을 갖도록 합니다.

이전 코드와의 호환성을 위해 클래스는 인수를 왼쪽으로 `operator()` 반환 하는 id 함수도 정의 합니다.
