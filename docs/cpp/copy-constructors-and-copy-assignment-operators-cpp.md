---
description: '자세한 정보: 복사 생성자 및 복사 할당 연산자 (c + +)'
title: 복사 생성자 및 복사 할당 연산자(C++)
ms.date: 11/04/2016
helpviewer_keywords:
- = operator [C++], copying objects
- assignment statements [C++], copying objects
- assignment operators [C++], for copying objects
- objects [C++], copying
- initializing objects, by copying objects
- copying objects
- assigning values to copy objects
ms.assetid: a94fe1f9-0289-4fb9-8633-77c654002c0d
ms.openlocfilehash: 881470c92e0261dc5c4cd63876d7cb59fcc68fef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344577"
---
# <a name="copy-constructors-and-copy-assignment-operators-c"></a>복사 생성자 및 복사 할당 연산자(C++)

> [!NOTE]
> C + + 11부터 *복사 할당* 및 *이동 할당* 이라는 두 가지 종류의 할당이 언어에서 지원 됩니다. 이 문서에서 별도로 명시하지 않는 한 "할당"은 복사 할당을 의미합니다. 이동 할당에 대 한 자세한 내용은 [이동 생성자 및 이동 할당 연산자 (c + +)](move-constructors-and-move-assignment-operators-cpp.md)를 참조 하세요.
>
> 할당 작업과 초기화 작업은 모두 개체를 복사합니다.

- **할당**: 한 개체의 값이 다른 개체에 할당 되 면 첫 번째 개체가 두 번째 개체에 복사 됩니다. 따라서

    ```cpp
    Point a, b;
    ...
    a = b;
    ```

   `b`의 값이 `a`에 복사되도록 합니다.

- **초기화**: 새 개체가 선언 될 때, 인수가 값으로 함수에 전달 되는 경우 또는 값으로 함수에서 값을 반환 하는 경우 초기화가 수행 됩니다.

클래스 형식의 개체에 대해 "복사"의 의미를 정의할 수 있습니다. 다음 코드를 예로 들 수 있습니다.

```cpp
TextFile a, b;
a.Open( "FILE1.DAT" );
b.Open( "FILE2.DAT" );
b = a;
```

앞의 코드는 "FILE1.DAT의 내용을 FILE2.DAT에 복사"를 의미하거나, "FILE2.DAT를 무시하고 `b`를 FILE1.DAT의 두 번째 핸들로 만들기"를 의미할 수도 있습니다. 다음과 같이 각 클래스에 적절한 복사 의미를 연결해야 합니다.

- 예를 들어, 할당 연산자 **연산자 =** 를 클래스 형식에 대 한 참조와 함께 반환 형식으로 사용 하 고 참조로 전달 되는 매개 변수를 사용 **`const`** `ClassName& operator=(const ClassName& x);` 합니다.

- 복사 생성자를 사용합니다.

복사 생성자를 선언하지 않으면 컴파일러는 자동으로 멤버 단위 복사 생성자를 생성합니다.  복사 할당 연산자를 선언하지 않으면 컴파일러는 자동으로 멤버 단위 복사 할당 연산자를 생성합니다. 복사 생성자의 선언은 컴파일러에서 생성된 복사 할당 연산자를 숨기지 않으며 그 반대의 경우에도 마찬가지입니다. 둘 중 하나를 구현하는 경우 다른 하나도 구현하여 코드의 의미를 분명히 하는 것이 좋습니다.

Copy 생성자는 <em>클래스 이름</em>형식의 인수를 사용 합니다 <strong>&</strong> . 여기서 *class-name* 은 생성자가 정의 된 클래스의 이름입니다. 예를 들어:

```cpp
// spec1_copying_class_objects.cpp
class Window
{
public:
    Window( const Window& ); // Declare copy constructor.
    // ...
};

int main()
{
}
```

> [!NOTE]
> 가능 하면 복사 생성자의 인수 **`const`** <em>클래스 이름</em> 형식을 설정 합니다 <strong>&</strong> . 이는 복사 생성자가 복사 중인 개체를 실수로 변경하는 것을 방지합니다. 또한 개체에서 복사할 수 있습니다 **`const`** .

## <a name="compiler-generated-copy-constructors"></a>컴파일러에서 생성된 복사 생성자

사용자 정의 복사 생성자와 같은 컴파일러 생성 복사 생성자에는 " *클래스 이름* 에 대 한 참조" 형식의 단일 인수가 있습니다. 예외는 모든 기본 클래스와 멤버 클래스에 **`const`** <em>클래스 이름</em>형식의 단일 인수를 사용할 때 복사 생성자가 선언 된 경우입니다 <strong>&</strong> . 이 경우 컴파일러에서 생성 된 복사 생성자의 인수도 이기도 **`const`** 합니다.

복사 생성자에 대 한 인수 형식이가 아닌 경우 **`const`** 개체를 복사 하 여 초기화 하면 **`const`** 오류가 생성 됩니다. 반대의 경우는 그렇지 않습니다. 인수가 이면이 **`const`** 아닌 개체를 복사 하 여 초기화할 수 있습니다 **`const`** .

컴파일러에서 생성 된 할당 연산자는 const와 관련 하 여 동일한 패턴을 따릅니다 **.** <em></em> <strong>&</strong> 모든 기본 및 멤버 클래스의 할당 연산자가 클래스 이름 형식의 인수를 사용 하지 않는 한 클래스 이름 형식의 단일 인수를 사용 **`const`** <em></em> <strong>&</strong> 합니다. 이 경우 클래스의 생성 된 할당 연산자는 인수를 사용 **`const`** 합니다.

> [!NOTE]
> 가상 기본 클래스가 복사 생성자에 의해 초기화되고 컴파일러에서 생성되거나 사용자 정의되는 경우 생성되는 시점에 한 번만 초기화됩니다.

의미는 복사 생성자의 의미와 비슷합니다. 인수 형식이가 아닌 경우 **`const`** 개체에서 할당 하면 **`const`** 오류가 발생 합니다. 반대의 경우는 그렇지 않습니다. **`const`** 값이가 아닌 값에 할당 되 면 **`const`** 할당이 성공 합니다.

오버 로드 된 할당 연산자에 대 한 자세한 내용은 [할당](../cpp/assignment.md)을 참조 하세요.
