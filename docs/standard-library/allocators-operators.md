---
title: '&lt;allocators&gt; 연산자'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: b7429e298cdf14d727fc481db6c4a3bf8574b5e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377897"
---
# <a name="ltallocatorsgt-operators"></a>&lt;allocators&gt; 연산자

&lt;allocators&gt;에 정의된 전역 템플릿 연산자 함수입니다. 클래스 멤버 연산자 함수에 대해서는 클래스 설명서를 참조하십시오.

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  operator!=

지정된 클래스의 할당자 개체가 다른지 테스트합니다.

```cpp
template <class Type, class Sync>
bool operator!=(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------------|-----------------|
|*left*|같지 않은지를 테스트할 할당자 개체 중 하나입니다.|
|*right*|같지 않은지를 테스트할 할당자 개체 중 하나입니다.|

### <a name="return-value"></a>반환 값

할당자 개체가 같지 않으면 **true**이고 할당자 개체가 같으면 **false**입니다.

### <a name="remarks"></a>설명

템플릿 연산자가 `!(left == right)`를 반환합니다.

## <a name="op_eq_eq"></a>  operator==

지정된 클래스의 할당자 개체가 같은지 테스트합니다.

```cpp
template <class Type, class Sync>
bool operator==(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------------|-----------------|
|*left*|같은지를 테스트할 할당자 개체 중 하나입니다.|
|*right*|같은지를 테스트할 할당자 개체 중 하나입니다.|

### <a name="return-value"></a>반환 값

할당자 개체가 같으면 **true**이고 할당자 개체가 같지 않으면 **false**입니다.

### <a name="remarks"></a>설명

템플릿 연산자가 `left.equals(right)`를 반환합니다.

## <a name="see-also"></a>참고자료

[\<allocators>](../standard-library/allocators-header.md)
