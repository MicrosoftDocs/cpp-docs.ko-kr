---
title: SafeInt 클래스
ms.date: 10/22/2018
ms.topic: reference
f1_keywords:
- SafeInt
- SafeInt::SafeInt
- SafeInt.SafeInt
helpviewer_keywords:
- SafeInt class
- SafeInt class, constructor
ms.assetid: 27a8f087-2511-46f9-8d76-2aeb66ca272f
ms.openlocfilehash: c69dc7ed5e34d98d5acff8f2bc28c34761bd31c6
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076814"
---
# <a name="safeint-class"></a>SafeInt 클래스

기본 정수형을 확장하여 정수 오버플로를 방지하고 다양한 유형의 정수를 비교할 수 있습니다.

> [!NOTE]
> 이 라이브러리의 최신 버전은 [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt)에 있습니다.

## <a name="syntax"></a>구문

```cpp
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>
class SafeInt;
```

### <a name="parameters"></a>매개 변수

| 템플릿  |  설명 |
|--------|------------|
| T         |  `SafeInt`로 대체되는 정수 또는 부울 매개 변수의 형식입니다. |
| E         |  정책 처리 오류를 정의하는 열거형 데이터 형식입니다. |
| U         |  보조 피연산자에 대한 정수 또는 부울 매개 변수의 형식입니다. |

| 매개 변수  |  설명 |
|---------|-----------------|
| *rhs*      |  [in] 여러 독립 실행형 함수에서 연산자의 오른쪽에 있는 값을 나타내는 입력 매개 변수입니다. |
| *i*        |  [in] 여러 독립 실행형 함수에서 연산자의 오른쪽에 있는 값을 나타내는 입력 매개 변수입니다. |
| *bits*     |  [in] 여러 독립 실행형 함수에서 연산자의 오른쪽에 있는 값을 나타내는 입력 매개 변수입니다. |

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

| 이름                          |  설명 |
|---------------------------|--------------------|
| [SafeInt::SafeInt](#safeint)  |  기본 생성자입니다. |

### <a name="assignment-operators"></a>대입 연산자

| 이름  |  구문 |
|----|---------|
| =     |  `template<typename U>`<br />`SafeInt<T,E>& operator= (const U& rhs)` |
| =     |  `SafeInt<T,E>& operator= (const T& rhs) throw()` |
| =     |  `template<typename U>`<br />`SafeInt<T,E>& operator= (const SafeInt<U, E>& rhs)` |
| =     |  `SafeInt<T,E>& operator= (const SafeInt<T,E>& rhs) throw()` |

### <a name="casting-operators"></a>캐스팅 연산자

| 이름              |  구문 |
|------|---------------------------------|
| bool              |  `operator bool() throw()` |
| char              |  `operator char() const` |
| signed char       |  `operator signed char() const` |
| unsigned char     |  `operator unsigned char() const` |
| __int16           |  `operator __int16() const` |
| unsigned __int16  |  `operator unsigned __int16() const` |
| __int32           |  `operator __int32() const` |
| unsigned __int32  |  `operator unsigned __int32() const` |
| long              |  `operator long() const` |
| unsigned long     |  `operator unsigned long() const` |
| __int64           |  `operator __int64() const` |
| unsigned __int64  |  `operator unsigned __int64() const` |
| wchar_t           |  `operator wchar_t() const` |

### <a name="comparison-operators"></a>비교 연산자

| 이름  |  구문 |
|----|----------------|
| \<     |  `template<typename U>`<br /><br /> `bool operator< (U rhs) const throw()` |
| \<     |  `bool operator< (SafeInt<T,E> rhs) const throw()` |
| \>=    |  `template<typename U>`<br /><br /> `bool operator>= (U rhs) const throw()` |
| \>=    |  `Bool operator>= (SafeInt<T,E> rhs) const throw()` |
| \>     |  `template<typename U>`<br /><br /> `bool operator> (U rhs) const throw()` |
| \>     |  `Bool operator> (SafeInt<T,E> rhs) const throw()` |
| \<=    |  `template<typename U>`<br /><br /> `bool operator<= (U rhs) const throw()` |
| \<=    |  `bool operator<= (SafeInt<T,E> rhs) const throw()` |
| ==    |  `template<typename U>`<br /><br /> `bool operator== (U rhs) const throw()` |
| ==    |  `bool operator== (bool rhs) const throw()` |
| ==    |  `bool operator== (SafeInt<T,E> rhs) const throw()` |
| !=    |  `template<typename U>`<br /><br /> `bool operator!= (U rhs) const throw()` |
| !=    |  `bool operator!= (bool b) const throw()` |
| !=    |  `bool operator!= (SafeInt<T,E> rhs) const throw()` |

### <a name="arithmetic-operators"></a>산술 연산자

| 이름  |  구문 |
|----|--------------|
| +     |  `const SafeInt<T,E>& operator+ () const throw()` |
| -     |  `SafeInt<T,E> operator- () const` |
| ++    |  `SafeInt<T,E>& operator++ ()` |
| --    |  `SafeInt<T,E>& operator-- ()` |
| %     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator% (U rhs) const` |
| %     |  `SafeInt<T,E> operator% (SafeInt<T,E> rhs) const` |
| %=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (U rhs)` |
| %=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (SafeInt<U, E> rhs)` |
| \*     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator* (U rhs) const` |
| \*     |  `SafeInt<T,E> operator* (SafeInt<T,E> rhs) const` |
| \*=    |  `SafeInt<T,E>& operator*= (SafeInt<T,E> rhs)` |
| \*=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (U rhs)` |
| \*=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (SafeInt<U, E> rhs)` |
| /     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator/ (U rhs) const` |
| /     |  `SafeInt<T,E> operator/ (SafeInt<T,E> rhs ) const` |
| /=    |  `SafeInt<T,E>& operator/= (SafeInt<T,E> i)` |
| /=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (U i)` |
| /=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (SafeInt<U, E> i)` |
| +     |  `SafeInt<T,E> operator+ (SafeInt<T,E> rhs) const` |
| +     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator+ (U rhs) const` |
| +=    |  `SafeInt<T,E>& operator+= (SafeInt<T,E> rhs)` |
| +=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (U rhs)` |
| +=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (SafeInt<U, E> rhs)` |
| -     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator- (U rhs) const` |
| -     |  `SafeInt<T,E> operator- (SafeInt<T,E> rhs) const` |
| -=    |  `SafeInt<T,E>& operator-= (SafeInt<T,E> rhs)` |
| -=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (U rhs)` |
| -=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (SafeInt<U, E> rhs)` |

### <a name="logical-operators"></a>논리 연산자

| 이름     |  구문 |
|------|--------------|
| !        |  `bool operator !() const throw()` |
| ~        |  `SafeInt<T,E> operator~ () const throw()` |
| \<\<       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (U bits) const throw()` |
| \<\<       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (SafeInt<U, E> bits) const throw()` |
| \<\<=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (U bits) throw()` |
| \<\<=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (SafeInt<U, E> bits) throw()` |
| \>\>       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (U bits) const throw()` |
| \>\>       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (SafeInt<U, E> bits) const throw()` |
| \>\>=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (U bits) throw()` |
| \>\>=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (SafeInt<U, E> bits) throw()` |
| &        |  `SafeInt<T,E> operator& (SafeInt<T,E> rhs) const throw()` |
| &        |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator& (U rhs) const throw()` |
| &=       |  `SafeInt<T,E>& operator&= (SafeInt<T,E> rhs) throw()` |
| &=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (U rhs) throw()` |
| &=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (SafeInt<U, E> rhs) throw()` |
| ^        |  `SafeInt<T,E> operator^ (SafeInt<T,E> rhs) const throw()` |
| ^        |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator^ (U rhs) const throw()` |
| ^=       |  `SafeInt<T,E>& operator^= (SafeInt<T,E> rhs) throw()` |
| ^=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (U rhs) throw()` |
| ^=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (SafeInt<U, E> rhs) throw()` |
| &#124;   |  `SafeInt<T,E> operator&#124; (SafeInt<T,E> rhs) const throw()` |
| &#124;   |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator&#124; (U rhs) const throw()` |
| &#124;=  |  `SafeInt<T,E>& operator&#124;= (SafeInt<T,E> rhs) throw()` |
| &#124;=  |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (U rhs) throw()` |
| &#124;=  |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (SafeInt<U, E> rhs) throw()` |

## <a name="remarks"></a>주의

`SafeInt` 클래스는 수학 연산에서 정수 오버플로를 방지합니다. 예를 들어, 두 개의 8 비트 정수를 추가할 때, 첫 번째 값인 200과 두 번째 값인 100이 있을 때. 올바른 수학 연산에는 200 + 100 = 300일 것입니다. 그러나 8비트 정수 제한으로 인해 상위 비트는 손실되고, 컴파일러에서 44(300 - 2<sup>8</sup>)가 결과로 반환됩니다. 이 수학 수식을 사용하는 모든 연산에서 예기치 않은 동작이 생성됩니다.

`SafeInt` 클래스는 산술 오버플로가 발생하는지 여부 또는 코드에서 0으로 나누기를 시도하는지 여부를 확인합니다. 두 경우 모두 클래스 프로그램의 잠재적 문제를 경고하는 오류 처리기를 호출합니다.

이 클래스를 사용하여 `SafeInt` 개체인 서로 다른 두 형식의 정수를 비교할 수도 있습니다. 일반적으로 비교를 수행하는 경우 먼저 동일한 형식이 되도록 숫자를 변환해야 합니다. 다른 형식으로 숫자를 변환하는 것은 종종 그로 인한 데이터 손실 없이 있는지 확인하기 위한 검사가 필요합니다.

이 항목의 연산자 표에는 `SafeInt` 클래스에서 지원하는 수학 연산자와 비교 연산자가 나와 있습니다. 대부분의 수학 연산자는 `SafeInt` 형식의 `T` 개체를 반환합니다.

`SafeInt`와 정수 형식 간의 비교 작업은 양쪽으로 모두 수행할 수 있습니다. 예를 들어 `SafeInt<int>(x) < y`와 `y> SafeInt<int>(x)`는 둘 다 유효하며 동일한 결과를 반환합니다.

서로 다른 두 `SafeInt` 형식의 사용을 지원하지 않는 이항 연산자가 많습니다. 이러한 예로 `&` 연산자가 있습니다. `SafeInt<T, E> & int`는 지원되지만, `SafeInt<T, E> & SafeInt<U, E>`는 지원되지 않습니다. 두 번째는 컴파일러가 어떤 유형의 매개 변수를 반환할지 알지 못합니다. 이 문제 해결 방법 중 하나는 두 번째 매개 변수를 기본 형식으로 다시 캐스팅하는 것 입니다. 이 작업은 같은 매개 변수를 사용하여 `SafeInt<T, E> & (U)SafeInt<U, E>`로 수행할 수 있습니다.

> [!NOTE]
> 모든 비트 연산에 대한 두 개의 서로 다른 매개 변수 크기가 동일해야 합니다. 크기가 다르면, 컴파일러에서 [ASSERT](../mfc/reference/diagnostic-services.md#assert) 예외가 throw됩니다. 이 동작에 대한 결과는 보장할 수 없습니다. 이 문제를 해결하려면 작은 매개 변수를 큰 크기의 매개 변수로 캐스팅합니다.

시프트 연산자의 경우 템플릿 형식보다 더 많은 비트를 시프트하면 ASSERT 예외가 발생합니다. 릴리스 모드에서는 아무런 영향을 주지 않습니다. 반환 형식은 원래 형식과 동일하기 때문에 두 가지 유형의 SafeInt 매개 변수를 혼합하는 것이 가능합니다. 연산자의 오른쪽에 있는 번호는 오직 이동할 비트 수를 나타냅니다.

SafeInt 개체 간 논리 비교를 수행하는 경우, 비교 동작은 엄격하게 계산됩니다. 예를 들어 다음 식을 참조하십시오.

- `SafeInt<uint>((uint)~0) > -1`

- `((uint)~0) > -1`

첫 번째 문은 **true**이고, 두 번째 문은 `false`입니다. 0에 대한 비트 부정은 0xFFFFFFFF입니다. 두 번째 문은 기본 비교 연산자 0xFFFFFFFF와 0xFFFFFFFF로 비교하고 동일한 것으로 간주합니다. `SafeInt` 클래스의 비교 연산자는 첫 번째 매개 변수는 부호가 없지만 두 번째 매개 변수는 음수임을 인식합니다. 따라서 비트 표현은 동일하지만, `SafeInt` 논리 연산자에서 부호 없는 정수가 -1보다 크다고 인식합니다.

`SafeInt` 클래스와 `?:` 3개로 구성된 연산자를 함께 사용할 때는 주의하세요. 다음 코드 줄이 있다고 가정합니다.

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : -1;
```

컴파일러는 다음과 같이 변환합니다.

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);
```

`flag`가 `false`이면, 컴파일러는 `x`에 값 -1을 할당하는 대신 예외를 throw합니다. 따라서 이 문제를 방지하려면 다음과 같이 올바른 코드를 사용해야 합니다.

```cpp
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;
```

`T` 및 `U`에 부울 형식, 문자 형식 또는 정수 형식을 할당할 수 있습니다. 정수 형식은 부호가 있을 수도 없을 수도 있고, 크기가 8비트에서 64비트까지 될 수 있습니다.

> [!NOTE]
> `SafeInt` 클래스는 모든 종류의 정수를 허용하지만, 부호 없는 형식에서 성능이 향상됩니다.

`E`는 `SafeInt`에서 사용하는 오류 처리 메커니즘입니다. 두 오류 처리 메커니즘이 SafeInt 라이브러리에서 제공됩니다. 기본 정책은 `SafeIntErrorPolicy_SafeIntException`으로, 오류가 발생하면 [SafeIntException 클래스](../safeint/safeintexception-class.md) 예외가 throw됩니다. 다른 정책은 `SafeIntErrorPolicy_InvalidParameter`로, 오류가 발생하면 프로그램을 중지합니다.

오류 정책을 사용자 지정하는 방법은 두 가지가 있습니다. 첫 번째 옵션은 `E`를 만들 때 `SafeInt` 매개 변수를 설정하는 것입니다. 하나의 `SafeInt`에 대해서만 오류 처리 정책을 변경하려는 경우 이 옵션을 사용합니다. 다른 옵션은 `SafeInt` 라이브러리를 포함하기 전에 _SAFEINT_DEFAULT_ERROR_POLICY를 사용자 지정 오류 처리 클래스로 정의하는 것입니다. 코드의 모든 `SafeInt` 클래스 인스턴스에 대해 기본 오류 처리 정책을 변경하려는 경우 이 옵션을 사용합니다.

> [!NOTE]
> SafeInt 라이브러리에서 발생하는 오류를 처리하는 사용자 지정 클래스는 오류 처리기를 호출한 모드에 제어를 반환하지 않아야 합니다. 오류 처리기가 호출된 후에는 `SafeInt` 작업의 결과를 신뢰할 수 없습니다.

## <a name="inheritance-hierarchy"></a>상속 계층

`SafeInt`

## <a name="requirements"></a>요구 사항

**헤더:** safeint.h

**네임스페이스:** msl::utilities

## <a name="safeintsafeint"></a><a name="safeint"></a>SafeInt::SafeInt

`SafeInt` 개체를 생성합니다.

```cpp
SafeInt() throw

SafeInt (
   const T& i
) throw ()

SafeInt (
   bool b
) throw ()

template <typename U>
SafeInt (
   const SafeInt <U, E>& u
)

I template <typename U>
SafeInt (
   const U& i
)
```

### <a name="parameters"></a>매개 변수

*i*<br/>
[in] 새로운 `SafeInt` 개체의 값입니다. 이 생성자에 따라 T 또는 U 형식의 매개 변수여야 합니다.

*b*<br/>
[in] 새로운 `SafeInt` 개체의 부울 값입니다.

*u*<br/>
[in] U 형식의 `SafeInt`입니다. 새로운 `SafeInt` 개체는 *u*와 동일한 값을 갖지만 T 형식입니다.

U `SafeInt`에 저장된 데이터의 형식입니다. 부울, 문자 또는 정수 형식이 될 수 있습니다. 데이터 형식이 정수 형식인 경우 부호가 없거나 있을 수도 있으며 8비트에서 64비트 사이여야 합니다.

### <a name="remarks"></a>주의

생성자 *i* 또는 *u*의 입력 매개 변수는 부울, 문자 또는 정수 형식이어야 합니다. 또 다른 형식의 매개 변수인 경우 `SafeInt` 클래스에서 [static_assert](../cpp/static-assert.md)를 호출하여 잘못된 입력 매개 변수를 나타냅니다.

템플릿 형식 `U`를 사용하는 생성자는 입력 매개 변수를 `T`에 지정된 형식으로 자동 변환합니다. `SafeInt` 클래스에서 데이터 손실 없이 데이터를 변환합니다. 데이터 손실 없이 데이터를 `E` 형식으로 변환할 수 없으면, 오류 처리기 `T`에 보고합니다.

부울 매개 변수에서 `SafeInt`를 만드는 경우 값을 즉시 초기화해야 합니다. `SafeInt` 코드를 사용하여 `SafeInt<bool> sb;`를 생성할 수 없습니다. 이를 시도하면 컴파일 에러가 발생합니다.
