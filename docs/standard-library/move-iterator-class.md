---
title: move_iterator 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- iterator/std::move_iterator
- iterator/std::move_iterator::iterator_type
- iterator/std::move_iterator::iterator_category
- iterator/std::move_iterator::value_type
- iterator/std::move_iterator::difference_type
- iterator/std::move_iterator::pointer
- iterator/std::move_iterator::reference
- iterator/std::move_iterator::base
dev_langs:
- C++
helpviewer_keywords:
- std::move_iterator [C++]
- std::move_iterator [C++], iterator_type
- std::move_iterator [C++], iterator_category
- std::move_iterator [C++], value_type
- std::move_iterator [C++], difference_type
- std::move_iterator [C++], pointer
- std::move_iterator [C++], reference
- std::move_iterator [C++], base
ms.assetid: a5e5cdd8-a264-4c6b-9f9c-68b0e8edaab7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e72f9c584f818de69b0c341ff8dba66892816d8a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/08/2018
---
# <a name="moveiterator-class"></a>move_iterator 클래스

클래스 템플릿 `move_iterator`는 반복기에 대한 래퍼입니다. move_iterator는 저장된 반복기의 역참조 연산자를 rvalue 참조로 전환하여 복사본을 이동으로 전환하는 것을 제외하고, 래핑(저장)하는 반복기와 동일한 동작을 제공합니다. rvalue에 대한 자세한 내용은 [Rvalue 참조 선언자: &&](../cpp/rvalue-reference-declarator-amp-amp.md)를 참조하세요.

## <a name="syntax"></a>구문

```cpp
class move_iterator;
```

## <a name="remarks"></a>설명

템플릿 클래스는 역참조된 경우를 제외하고 반복기와 유사하게 동작합니다. 이 클래스는 구성원 함수 `base()`로 액세스하는 `Iterator` 형식의 임의 액세스 반복기를 저장합니다. `move_iterator`에 대한 모든 작업은 `operator*` 결과가 `value_type&&`으로 묵시적으로 캐스팅되어 rvalue 참조를 만드는 것을 제외하고, 저장된 반복기에서 직접 수행됩니다.

`move_iterator`는 래핑된 반복기에서 정의하지 않은 작업을 수행할 수 있습니다. 이러한 작업을 사용하지 마십시오.

### <a name="constructors"></a>생성자

|생성자|설명|
|-|-|
|[move_iterator](#move_iterator)|`move_iterator` 형식의 개체에 대한 생성자입니다.|

### <a name="typedefs"></a>형식 정의

|형식 이름|설명|
|-|-|
|[iterator_type](#iterator_type)|템플릿 매개 변수 `RandomIterator`의 동의어.|
|[iterator_category](#iterator_category)|동일한 이름의 긴 `typename` 식에 대한 동의어. `iterator_category`는 반복기의 일반 기능을 식별합니다.|
|[value_type](#value_type)|동일한 이름의 긴 `typename` 식에 대한 동의어. `value_type`은 반복기 요소의 형식에 대해 설명합니다.|
|[difference_type](#difference_type)|동일한 이름의 긴 `typename` 식에 대한 동의어. `difference_type`은 요소 간 차이 값을 표시하는 데 필요합니다.|
|[pointer](#pointer)|템플릿 매개 변수 `RandomIterator`에 대한 동의어.|
|[reference](#reference)|`rvalue` 참조 `value_type&&`에 대한 동의어.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|설명|
|-|-|
|[base](#base)|멤버 함수는 이 `move_iterator`에서 래핑한 저장된 반복기를 반환합니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[move_iterator::operator*](#op_star)|`(reference)*base().`를 반환합니다.|
|[move_iterator::operator++](#op_add_add)|저장된 반복기를 증가시킵니다. 정확한 동작은 사전 증가인지 또는 사후 증가인지에 따라 다릅니다.|
|[move_iterator::operator--](#operator--)|저장된 반복기를 감소시킵니다. 정확한 동작은 사전 감소인지 또는 사후 감소인지에 따라 다릅니다.|
|[move_iterator::operator-&gt;](#op_arrow)|`&**this`를 반환합니다.|
|[move_iterator::operator-](#operator-)|현재 위치에서 오른쪽 값을 차감하여 `move_iterator(*this) -=`를 반환합니다.|
|[move_iterator::operator[]](#op_at)|`(reference)*(*this + off)`를 반환합니다. 현재 기준에서 해당 위치의 값을 얻기 위한 오프셋을 지정할 수 있습니다.|
|[move_iterator::operator+](#op_add)|`move_iterator(*this) +=` 값을 반환합니다. 기준에 오프셋을 추가하여 해당 위치의 값을 얻을 수 있습니다.|
|[move_iterator::operator+=](#op_add_eq)|저장된 반복기에 오른쪽 값을 더하고 `*this`를 반환합니다.|
|[move_iterator::operator-=](#operator-_eq)|저장된 반복기에서 오른쪽 값을 빼고 `*this`를 반환합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** \<iterator>

**네임스페이스:** std

## <a name="base"></a>  move_iterator::base

이 `move_iterator`에 대한 저장된 반복기를 반환합니다.

```cpp
RandomIterator base() const;
```

### <a name="remarks"></a>설명

이 멤버 함수는 저장된 반복기를 반환합니다.

## <a name="difference_type"></a>  move_iterator::difference_type

`difference_type` 형식은 반복기 특성 `difference_type`을 기반으로 하는 `move_iterator` `typedef`로서 혼용할 수 있습니다.

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type difference_type;
```

### <a name="remarks"></a>설명

이 형식은 반복기 특성 `typename iterator_traits<RandomIterator>::pointer`의 동의어입니다.

## <a name="iterator_category"></a>  move_iterator::iterator_category

`iterator_category` 형식은 반복기 특성 `iterator_category`을 기반으로 하는 `move_iterator` `typedef`로서 혼용할 수 있습니다.

```cpp
typedef typename iterator_traits<RandomIterator>::iterator_category  iterator_category;
```

### <a name="remarks"></a>설명

이 형식은 반복기 특성 `typename iterator_traits<RandomIterator>::iterator_category`의 동의어입니다.

## <a name="iterator_type"></a>  move_iterator::iterator_type

`iterator_type` 형식은 클래스 템플릿 `move_iterator`에 대한 템플릿 매개 변수 `RandomIterator`를 기반으로 하며 해당 위치에 같은 의미로 사용될 수 있습니다.

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `RandomIterator`의 동의어입니다.

## <a name="move_iterator"></a>  move_iterator::move_iterator

이동 반복기를 생성합니다. 매개 변수를 저장된 반복기로 사용합니다.

```cpp
move_iterator();
explicit move_iterator(RandomIterator right);
template <class Type>
move_iterator(const move_iterator<Type>& right);
```

### <a name="parameters"></a>매개 변수

`right` 저장 된 반복기로 사용할 반복기입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 기본 생성자를 사용하여 저장된 반복기를 초기화합니다. 나머지 생성자는 `base.base()`를 사용하여 저장된 반복기를 초기화합니다.

## <a name="op_add_eq"></a>  move_iterator::operator+=

저장된 반복기가 새 현재 위치에서 요소를 가리키도록 저장된 반복기에 오프셋을 추가합니다. 그러면 연산자가 새 현재 요소를 이동시킵니다.

```cpp
move_iterator& operator+=(difference_type _Off);
```

### <a name="parameters"></a>매개 변수

`_Off` 새 현재 위치를 결정 하는 현재 위치에 추가 하는 오프셋입니다.

### <a name="return-value"></a>반환 값

새 현재 요소를 반환합니다.

### <a name="remarks"></a>설명

연산자가 `_Off`를 저장된 반복기에 추가합니다. 그런 다음 `*this`를 반환합니다.

## <a name="move_iterator__operator-_eq"></a>  move_iterator::operator-=

지정된 수의 이전 요소를 이동합니다. 이 연산자는 저장된 반복기에서 오프셋을 뺍니다.

```cpp
move_iterator& operator-=(difference_type _Off);
```

### <a name="parameters"></a>매개 변수

### <a name="remarks"></a>설명

연산자가 `*this += -_Off`를 평가합니다. 그런 다음 `*this`를 반환합니다.

## <a name="op_add_add"></a>  move_iterator::operator++

이 `move_iterator.`에 속하는 저장된 반복기를 단계적으로 증가시킵니다. 현재 요소는 사후 증가 연산자로 액세스합니다. 다음 요소는 사전 증가 연산자로 액세스합니다.

```cpp
move_iterator& operator++();
move_iterator operator++(int);
```

### <a name="parameters"></a>매개 변수

### <a name="remarks"></a>설명

첫 번째(사전 증가) 연산자는 저장된 반복기를 단계적으로 증가시킵니다. 그런 다음 `*this`를 반환합니다.

두 번째(사후 증가) 연산자는 `*this`의 복사본을 만들고 `++*this`를 평가합니다. 그런 다음 복사본을 반환합니다.

## <a name="op_add"></a>  move_iterator::operator+

임의 요소 수만큼 앞으로 이동한 반복기 위치를 반환합니다.

```cpp
move_iterator operator+(difference_type _Off) const;
```

### <a name="parameters"></a>매개 변수

### <a name="remarks"></a>설명

연산자는 `move_iterator(*this) +=` `_Off`를 반환합니다.

## <a name="op_at"></a>  move_iterator::operator[]

배열 인덱스에 `move iterator` 범위의 요소에 대한 액세스를 허용합니다.

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>매개 변수

### <a name="remarks"></a>설명

연산자가 `(reference)*(*this + _Off)`를 반환합니다.

## <a name="move_iterator__operator--"></a>  move_iterator::operator--

사전 및 사후 감소 멤버 연산자는 저장된 반복기에서 감소를 수행합니다.

```cpp
move_iterator& operator--();
move_iterator operator--();
```

### <a name="parameters"></a>매개 변수

### <a name="remarks"></a>설명

첫 번째 멤버 연산자(사전 감소)가 저장된 반복기를 감소시킵니다. 그런 다음 `*this`를 반환합니다.

두 번째(사후 감소) 연산자가 `*this`의 복사본을 만들고 `--*this`를 계산합니다. 그런 다음 복사본을 반환합니다.

## <a name="move_iterator__operator-"></a>  move_iterator::operator-

저장된 반복기를 단계적으로 감소시키고 표시된 값을 반환합니다.

```cpp
move_iterator operator-(difference_type _Off) const;
```

### <a name="parameters"></a>매개 변수

### <a name="remarks"></a>설명

연산자가 `move_iterator(*this) -= _Off`를 반환합니다.

## <a name="op_star"></a>  move_iterator::operator*

저장된 반복기를 역참조하고 값을 반환합니다. `rvalue reference`처럼 동작하며 이동 할당을 수행합니다. 연산자는 기본 반복기에서 현재 요소를 전송합니다. 뒤에 오는 요소는 새 현재 요소가 됩니다.

```cpp
reference operator*() const;
```

### <a name="remarks"></a>설명

연산자가 `(reference)*base()`를 반환합니다.

## <a name="op_arrow"></a>  move_iterator::operator-&gt;

일반적인 `RandomIterator` `operator->`와 마찬가지로, 현재 요소에 속하는 필드에 대한 액세스를 제공합니다.

```cpp
pointer operator->() const;
```

### <a name="remarks"></a>설명

연산자가 `&**this`를 반환합니다.

## <a name="pointer"></a>  move_iterator::pointer

`pointer` 형식은 `move_iterator`에 대한 임의 반복기 `RandomIterator`를 기반으로 하는 `typedef`이며, 같은 의미로 사용될 수 있습니다.

```cpp
typedef RandomIterator  pointer;
```

### <a name="remarks"></a>설명

이 형식은 `RandomIterator`의 동의어입니다.

## <a name="reference"></a>  move_iterator::reference

`reference` 형식은 `move_iterator`의 `value_type&&`에 따른 `typedef`이며, `value_type&&`과 바꿔서 사용할 수 있습니다.

```cpp
typedef value_type&& reference;
```

### <a name="remarks"></a>설명

이 형식은 rvalue 참조인 `value_type&&`과 동일한 의미입니다.

## <a name="value_type"></a>  move_iterator::value_type

`value_type` 형식은 반복기 특성 `value_type`을 기반으로 하는 `move_iterator` `typedef`로서 혼용할 수 있습니다.

```cpp
typedef typename iterator_traits<RandomIterator>::value_type   value_type;
```

### <a name="remarks"></a>설명

이 형식은 반복기 특성 `typename iterator_traits<RandomIterator>::value_type`의 동의어입니다.

## <a name="see-also"></a>참고자료

[\<iterator>](../standard-library/iterator.md)<br/>
[Lvalue 및 Rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
[이동 생성자 및 이동 할당 연산자(C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)<br/>
[C++ 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)<br/>
