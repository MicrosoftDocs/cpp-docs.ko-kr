---
title: '&lt;ostream&gt; 연산자'
ms.date: 11/04/2016
f1_keywords:
- ostream/std::operator&lt;&lt;
ms.assetid: 9282a62e-a3d1-4371-a284-fbc9515bb9a2
ms.openlocfilehash: c80abcb08423b4bb269e7d60ac43ef97d197a0e9
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425282"
---
# <a name="ltostreamgt-operators"></a>&lt;ostream&gt; 연산자

||
|-|
|[operator&lt;&lt;](#op_lt_lt)|

## <a name="op_lt_lt"></a>  operator&lt;&lt;

스트림에 다양한 형식을 씁니다.

```cpp
template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const Elem* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    Elem _Ch);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const char* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);

template <class _Elem, class _Tr, class T>
basic_ostream <_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>&& _Ostr,
    Ty val);
```

### <a name="parameters"></a>매개 변수

*_Ch*\
단일 문자입니다.

*_Elem*\
요소 형식입니다.

*_Ostr*\
`basic_ostream` 개체입니다.

*str*\
문자열입니다.

*_Tr*\
문자 특성입니다.

*val*\
형식입니다.

### <a name="return-value"></a>Return Value

스트림입니다.

### <a name="remarks"></a>설명

`basic_ostream` 클래스도 여러 가지 삽입 연산자를 정의합니다. 자세한 내용은 [basic_ostream::operator&lt;&lt;](../standard-library/basic-ostream-class.md#basic_ostream_operator_lt_lt)를 참조하세요.

다음 템플릿 함수는

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _ostr,
    const Elem *str);
```

*str*에서 시작 하는 시퀀스의 길이 N = `traits_type::`[길이](../standard-library/char-traits-struct.md#length)(`str`)를 결정 하 고 시퀀스를 삽입 합니다. N < `_Ostr.`[width](../standard-library/ios-base-class.md#width)인 경우 함수는 `_Ostr.width` - N 채우기 문자의 반복도 삽입합니다. (`_Ostr`인 경우 반복은 시퀀스 앞에 옵니다. [flags](../standard-library/ios-base-class.md#flags) & `adjustfield` != [left](../standard-library/ios-functions.md#left)인 경우 반복은 시퀀스 앞에 옵니다. 그렇지 않은 경우에는 반복이 시퀀스 뒤에 옵니다. 함수는 *_Ostr*를 반환 합니다.

다음 템플릿 함수는

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

`_Ch` 요소를 삽입합니다. 1 < `_Ostr.width`인 경우 함수는 `_Ostr.width` - 1 채우기 문자의 반복도 삽입합니다. `_Ostr.flags & adjustfield != left`인 경우 반복은 시퀀스 앞에 옵니다. 그렇지 않은 경우에는 반복이 시퀀스 뒤에 옵니다. *_Ostr*를 반환 합니다.

다음 템플릿 함수는

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const char *str);
```

다음 코드와 동일하게 동작합니다.

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

*str* 에서 시작 하는 시퀀스의 각 요소가 `_Ostr.`[put](../standard-library/basic-ostream-class.md#put)(`_Ostr.`[확장](../standard-library/basic-ios-class.md#widen)(`_Ch`))을 호출 하 여 `Elem` 형식의 개체로 변환 된다는 점을 제외 하 고 *_Ch* .

다음 템플릿 함수는

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    char _Ch);
```

다음 코드와 동일하게 동작합니다.

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

*_Ch* 를 제외 하 고 `_Ostr.put`(`_Ostr.widen`(`_Ch`))를 호출 하 여 `Elem` 형식의 개체로 변환 합니다.

다음 템플릿 함수는

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char *str);
```

다음 코드와 동일하게 동작합니다.

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

요소를 삽입하기 전에 확장할 필요가 없습니다.

다음 템플릿 함수는

```cpp
template <class _Tr>
basic_ostream<char, Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    char _Ch);
```

다음 코드와 동일하게 동작합니다.

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

(삽입 하기 전에 *_Ch* 을 확장할 필요가 없습니다.)

다음 템플릿 함수는

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char *str);
```

`const char *`(`_Ostr` < <) `str`를 반환 합니다.

다음 템플릿 함수는

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);
```

`char`(`_Ostr` < <) `_Ch`를 반환 합니다.

다음 템플릿 함수는

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char *str);
```

`const char *`(`_Ostr` < <) `str`를 반환 합니다.

다음 템플릿 함수는

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);
```

`char`(`_Ostr` < <) `_Ch`를 반환 합니다.

다음 템플릿 함수는

```cpp
template <class _Elem, class _Tr, class T>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<char, _Tr>&& _Ostr,
    T val);
```

`val` `<<` `_Ostr` 반환 하 고 [RValue 참조](../cpp/rvalue-reference-declarator-amp-amp.md) 를 프로세스의 lvalue로 `_Ostr` 변환 합니다.

### <a name="example"></a>예제

[를 사용하는 방법의 예제를 보려면 ](../standard-library/ostream-functions.md#flush)flush`operator<<`를 참조하세요.

## <a name="see-also"></a>참고 항목

[\<ostream>](../standard-library/ostream.md)
