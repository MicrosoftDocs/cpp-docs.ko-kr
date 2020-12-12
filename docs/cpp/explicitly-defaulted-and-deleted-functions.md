---
description: '자세히 알아보기: 명시적으로 기본 설정 및 삭제 된 함수'
title: 명시적으로 기본 설정 및 삭제된 함수
ms.date: 11/04/2016
ms.assetid: 5a588478-fda2-4b3f-a279-db3967f5e07e
ms.openlocfilehash: a3c4789996d39acd4ddd3bbc186ce39509a1d62f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273360"
---
# <a name="explicitly-defaulted-and-deleted-functions"></a>명시적으로 기본 설정 및 삭제된 함수

C++ 11에서 기본 설정 및 삭제된 함수를 사용하면 특수 멤버 함수가 자동으로 생성되는지 여부를 명시적으로 제어할 수 있습니다. 함수를 삭제하면 간단한 언어로 일반적인 멤버 함수와 비멤버 함수뿐 아니라 특수 멤버 함수까지 모든 형식의 함수에 대한 인수에서 문제가 발생할 수 있는 형식 승격을 방지할 수 있습니다. 그렇지 않은 경우 원하지 않는 함수 호출 시 문제가 발생할 수 있습니다.

## <a name="benefits-of-explicitly-defaulted-and-deleted-functions"></a>명시적으로 기본 설정 및 삭제된 함수의 이점

C++에서 컴파일러는 형식을 자체적으로 선언하지 않을 경우 기본 생성자, 복사 생성자, 복사 할당 연산자 및 소멸자를 자동으로 생성합니다. 이러한 함수는 *특수 멤버 함수* 라고 하며 c + +에서 간단한 사용자 정의 형식이 c의 구조체와 같이 동작 합니다. 즉, 추가 코딩 작업 없이 만들고, 복사 하 고, 삭제할 수 있습니다. C++11은 언어에 이동 의미 체계를 가져오고 이동 생성자와 이동 할당 연산자를 컴파일러가 자동으로 생성할 수 있는 특수 멤버 함수 목록에 추가합니다.

따라서 단순 형식에는 편리하지만 복합 형식은 종종 하나 이상의 특수 멤버 함수 자체를 정의하므로 다른 특수 멤버 함수가 자동으로 생성되지 않도록 할 수 있습니다. 실제로는 다음과 같습니다.

- 생성자가 명시적으로 선언된 경우 기본 생성자가 자동으로 생성되지 않습니다.

- 가상 소멸자가 명시적으로 선언된 경우 기본 소멸자가 자동으로 생성되지 않습니다.

- 이동 생성자 혹은 이동 할당 연산자가 명시적으로 선언된 경우 다음과 같습니다.

  - 복사 생성자가 자동으로 생성되지 않습니다.

  - 복사 할당 연산자가 자동으로 생성되지 않습니다.

- 복사 생성자, 복사 할당 연산자, 이동 생성자, 이동 할당 연산자 또는 소멸자가 명시적으로 선언된 경우 다음과 같습니다.

  - 이동 생성자가 자동으로 생성되지 않습니다.

  - 이동 할당 연산자가 자동으로 생성되지 않습니다.

> [!NOTE]
> 또한 C++ 11 표준은 다음 추가 규칙을 지정합니다.
>
> - 복사 생성자나 소멸자가 명시적으로 선언된 경우 복사 할당 연산자가 자동으로 생성되지 않습니다.
> - 복사 할당 연산자나 소멸자가 명시적으로 선언된 경우 복사 생성자가 자동으로 생성되지 않습니다.
>
> 두 경우 모두 Visual Studio에서는 필요한 함수가 암시적으로 자동 생성되며 경고를 생성하지 않습니다.

이러한 규칙으로 인해 개체 계층 구조에 누수가 발생할 수도 있습니다. 예를 들어 어떤 이유로 든 기본 클래스에 파생 클래스에서 호출할 수 있는 기본 생성자 ( **`public`** **`protected`** 매개 변수를 사용 하지 않는 또는 생성자)가 없는 경우이 클래스에서 파생 되는 클래스는 자체 기본 생성자를 자동으로 생성할 수 없습니다.

이러한 규칙으로 인해 간단해야 하는 사용자 정의 형식 및 일반적인 C++ 관용구의 구현이 복잡해질 수 있습니다. 예를 들어 복사 생성자 및 복사 할당 연산자를 정의하지 않고 비공개적으로 선언하여 사용자 정의 형식을 복사할 수 없게 만들 수 있습니다.

```cpp
struct noncopyable
{
  noncopyable() {};

private:
  noncopyable(const noncopyable&);
  noncopyable& operator=(const noncopyable&);
};
```

C++11 이전에 이 코드 조각은 복사할 수 없는 형식의 관용구 형태였습니다. 그러나 다음과 같은 몇가지 문제가 있습니다.

- 복사 생성자는 개별적으로 숨기도록 선언 되어야 하지만 모두 선언 되었기 때문에 기본 생성자의 자동 생성이 방지 됩니다. 기본 생성자가 아무 작업도 수행하지 않는 경우에도 원하면 명시적으로 정의해야 합니다.

- 명시적으로 정의한 기본 생성자가 아무 작업도 수행하지 않는 경우에도 컴파일러에서 특수한 것으로 간주됩니다. 기본 생성자를 자동으로 생성하는 것보다 덜 효율적이며 `noncopyable`이 진정한 POD 형식이 되지 않습니다.

- 복사 생성자 및 복사 할당 연산자는 외부 코드로부터 숨겨지지만 멤버 함수와 `noncopyable`의 friend에서는 보고 호출할 수 있습니다. 선언되지만 정의되지 않은 경우 호출하면 링커 오류가 발생합니다.

- 일반적으로 허용되는 관용구이지만 특수 멤버 함수의 자동 생성 규칙을 모두 이해하지 못하면 의도가 명확하지 않습니다.

C++ 11에서는 복사할 수 없는 관용구를 더 간단한 방법으로 구현할 수 있습니다.

```cpp
struct noncopyable
{
  noncopyable() =default;
  noncopyable(const noncopyable&) =delete;
  noncopyable& operator=(const noncopyable&) =delete;
};
```

C++11 이전 관용구 문제를 해결하는 방법을 확인합니다.

- 기본 생성자의 생성은 복사 생성자를 선언하여 예방되지만 명시적으로 기본값으로 지정하여 되돌릴 수 있습니다.

- 명시적으로 기본값으로 지정된 특수 멤버 함수는 여전히 trivial로 간주되므로 성능 저하는 없으며 `noncopyable`이 진정한 POD 형식이 되는 것을 방지하지 않습니다.

- 복사 생성자 및 복사 할당 연산자는 public이지만 삭제됩니다. 삭제된 함수를 정의하거나 호출하면 컴파일 시간 오류가 발생합니다.

- 이 의도는 `=default` 및 `=delete`를 이해하는 사용자에게 명확하게 전달됩니다. 특수 멤버 함수의 자동 생성 규칙을 이해할 필요가 없습니다.

사용자 정의 형식 만들기에도 이동할 수 없거나, 동적으로만 할당할 수 있거나, 동적으로 할당할 수 없는 유사한 관용구가 있습니다. 이러한 각 관용구에는 유사한 문제가 발생하는 C++11 이전의 구현이 있으며, C++11에서 기본 설정 및 삭제된 특수 멤버 함수 측면에서 구현하여 유사하게 해결할 수 있습니다.

## <a name="explicitly-defaulted-functions"></a>명시적으로 기본 설정된 함수

특수 멤버 함수를 기본 설정하여 특수 멤버 함수에서 기본 구현을 사용하도록 명시적으로 지정하거나, public이 아닌 액세스 한정자를 사용하여 특수 멤버 함수를 정의하거나, 다른 환경에서 자동 생성이 방지된 특수 멤버 함수를 복구할 수 있습니다.

다음 예제와 같이 선언하여 특수 멤버 함수를 기본 설정합니다.

```cpp
struct widget
{
  widget()=default;

  inline widget& operator=(const widget&);
};

inline widget& widget::operator=(const widget&) =default;
```

Inlinable 인 한 클래스 본문 외부에서 특수 멤버 함수를 기본적으로 사용할 수 있습니다.

trivial 특수 멤버 함수의 성능 이점으로 인해 기본 동작을 원하는 경우 비어 있는 함수 본문보다 자동으로 생성된 특수 멤버 함수를 사용하는 것이 좋습니다. 이렇게 하려면 특수 멤버 함수를 명시적으로 기본 설정하거나 특수 멤버 함수를 선언하지 않고 자동으로 생성될 수 없도록 하는 다른 특수 멤버 함수도 선언하지 않을 수 있습니다.

## <a name="deleted-functions"></a>삭제된 함수

특수 멤버 함수뿐만 아니라 일반 멤버 함수와 비멤버 함수도 삭제하여 정의되거나 호출되지 않도록 할 수 있습니다. 특수 멤버 함수를 삭제 하면 컴파일러가 원하지 않는 특수 멤버 함수를 생성 하는 것을 방지할 수 있습니다. 함수는 선언할 때 삭제해야 합니다. 그 이후에는 함수를 선언한 다음 나중에 기본값으로 지정할 수 있으므로 삭제할 수 없습니다.

```cpp
struct widget
{
  // deleted operator new prevents widget from being dynamically allocated.
  void* operator new(std::size_t) = delete;
};
```

일반 멤버 함수 또는 비멤버 함수를 삭제하면 문제가 있는 형식 승격에서 의도하지 않은 함수를 호출하는 것을 방지할 수 있습니다. 이 기능은 삭제된 함수가 오버로드 확인에 계속 참여하고 형식이 승격된 후 호출될 수 있는 함수보다 더 우수한 일치를 제공하기 때문에 작동합니다. 함수 호출은 보다 구체적이지만 삭제된 함수가 되고 컴파일러 오류를 발생시킵니다.

```cpp
// deleted overload prevents call through type promotion of float to double from succeeding.
void call_with_true_double_only(float) =delete;
void call_with_true_double_only(double param) { return; }
```

앞의 예제에서 인수를 사용 하 여를 호출 하면 `call_with_true_double_only` **`float`** 컴파일러 오류가 발생 하지만 인수를 사용 하 여를 호출 하는 것은 `call_with_true_double_only` **`int`** 아닙니다 .이 **`int`** 경우 인수는 의도 하지 않은 경우 **`int`** 에도에서로 승격 되 **`double`** 고 함수 버전을 성공적으로 호출 합니다 **`double`** . 비 double 인수를 사용 하 여이 함수를 호출 하면 컴파일러 오류가 발생 하는 것을 확인 하기 위해 삭제 된 함수의 템플릿 버전을 선언할 수 있습니다.

```cpp
template < typename T >
void call_with_true_double_only(T) =delete; //prevent call through type promotion of any T to double from succeeding.

void call_with_true_double_only(double param) { return; } // also define for const double, double&, etc. as needed.
```
