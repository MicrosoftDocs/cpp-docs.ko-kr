---
description: '자세한 정보: &lt; 벡터 &gt; 함수'
title: '&lt;vector&gt; 함수'
ms.date: 11/04/2016
f1_keywords:
- vector/std::swap
ms.assetid: 6cdcf043-eef6-4330-83f0-4596fb9f968a
helpviewer_keywords:
- std::swap [vector]
ms.openlocfilehash: c59e2626a2062be90d2cb8201b058d5ee148ef55
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187886"
---
# <a name="ltvectorgt-functions"></a>&lt;vector&gt; 함수

## <a name="swap"></a><a name="swap"></a> 스왑을

두 벡터의 요소를 교환합니다.

```cpp
template <class Type, class Allocator>
void swap(vector<Type, Allocator>& left, vector<Type, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
교환할 요소를 제공 하는 벡터 또는 해당 요소를 *왼쪽* 벡터의 요소와 교환할 벡터입니다.

*비어*\
해당 요소를 벡터 *오른쪽* 벡터와 교환할 벡터입니다.

### <a name="remarks"></a>설명

템플릿 함수는 멤버 함수를 실행 하기 위해 컨테이너 클래스 vector에서 특수화 된 알고리즘입니다 `left` . [vector:: swap](../standard-library/vector-class.md) *(right*). 이러한 함수는 컴파일러에서 지정하는 함수 템플릿의 부분 순서 인스턴스입니다. 함수를 호출할 때 템플릿이 고유하게 일치하지 않는 방식으로 템플릿 함수가 오버로드되면 컴파일러는 템플릿 함수의 가장 특수화된 버전을 선택합니다. **`template`** \< **class T**> 알고리즘 클래스에서 템플릿 함수 **void swap**( **t&**, **t&**)의 일반 버전은 할당에 따라 작동 하 고 속도가 느립니다. 각 컨테이너의 특수화된 버전은 컨테이너 클래스의 내부 표현을 사용할 수 있으므로 속도가 훨씬 빠릅니다.

### <a name="example"></a>예제

`swap`의 템플릿 버전을 사용하는 예제를 확인하려면 구성원 함수 [vector:: swap](../standard-library/vector-class.md)의 코드 예제를 참조하세요.
