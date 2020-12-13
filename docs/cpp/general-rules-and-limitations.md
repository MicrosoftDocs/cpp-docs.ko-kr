---
description: '자세한 정보: 일반 규칙 및 제한 사항'
title: 일반 규칙 및 제한 사항
ms.date: 11/04/2016
ms.assetid: 6c48902d-4259-4761-95d4-e421d69aa050
ms.openlocfilehash: 935befff4cce7f87217e1a05e8ca92835c82565d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332537"
---
# <a name="general-rules-and-limitations"></a>일반 규칙 및 제한 사항

**Microsoft 전용**

- 또는 특성을 사용 하지 않고 함수 또는 개체를 선언 하는 경우 **`dllimport`** **`dllexport`** 함수 또는 개체는 DLL 인터페이스의 일부분으로 간주 되지 않습니다. 따라서 해당 모듈 또는 같은 프로그램의 다른 모듈에 함수 또는 개체의 정의가 있어야 합니다. DLL 인터페이스의 함수 또는 개체 부분을 만들려면 다른 모듈에서 함수 또는 개체의 정의를로 선언 해야 합니다 **`dllexport`** . 그렇게 하지 않으면 링커 오류가 생성됩니다.

   특성을 사용 하 여 함수 또는 개체를 선언 하는 경우 **`dllexport`** 해당 정의가 같은 프로그램의 일부 모듈에 표시 되어야 합니다. 그렇게 하지 않으면 링커 오류가 생성됩니다.

- 프로그램의 단일 모듈에 **`dllimport`** **`dllexport`** 동일한 함수 또는 개체에 대 한 및 선언이 모두 포함 되어 있으면 특성이 **`dllexport`** 특성 보다 우선적으로 적용 **`dllimport`** 됩니다. 그러나 이 경우 컴파일러 경고가 생성됩니다. 예를 들어:

    ```cpp
    __declspec( dllimport ) int i;
    __declspec( dllexport ) int i;   // Warning; inconsistent;
                                     // dllexport takes precedence.
    ```

- C + +에서는 특성을 사용 하 여 선언 된 데이터 개체의 주소를 사용 하 여 전역적으로 선언 되거나 정적 로컬 데이터 포인터를 초기화할 수 있습니다 **`dllimport`** . 그러면 c에서 오류가 생성 됩니다. 또한 특성을 사용 하 여 선언 된 함수의 주소를 사용 하 여 정적 로컬 함수 포인터를 초기화할 수 있습니다 **`dllimport`** . C에서는 이러한 대입으로 인해 포인터가 함수의 주소 대신 DLL 가져오기 썽크(함수로 제어를 전송하는 코드 스텁)의 주소로 설정됩니다. C++에서는 포인터가 함수의 주소로 설정됩니다. 예를 들어:

    ```cpp
    __declspec( dllimport ) void func1( void );
    __declspec( dllimport ) int i;

    int *pi = &i;                             // Error in C
    static void ( *pf )( void ) = &func1;     // Address of thunk in C,
                                              // function in C++

    void func2()
    {
       static int *pi = &i;                  // Error in C
       static void ( *pf )( void ) = &func1; // Address of thunk in C,
                                             // function in C++
    }
    ```

   그러나 개체 선언에 특성을 포함 하는 프로그램은 **`dllexport`** 프로그램의 어딘가에 해당 개체에 대 한 정의를 제공 해야 하므로 함수의 주소로 전역 또는 로컬 정적 함수 포인터를 초기화할 수 있습니다 **`dllexport`** . 마찬가지로 데이터 개체의 주소로 전역 또는 로컬 정적 데이터 포인터를 초기화할 수 있습니다 **`dllexport`** . 예를 들어, 다음 코드는 C 또는 C++에서 오류를 발생시키지 않습니다.

    ```cpp
    __declspec( dllexport ) void func1( void );
    __declspec( dllexport ) int i;

    int *pi = &i;                              // Okay
    static void ( *pf )( void ) = &func1;      // Okay

    void func2()
    {
        static int *pi = &i;                   // Okay
        static void ( *pf )( void ) = &func1;  // Okay
    }
    ```

- **`dllexport`** 로 표시 되지 않은 기본 클래스를 포함 하는 일반 클래스에 적용 하는 경우 **`dllexport`** 컴파일러는 C4275을 생성 합니다.

   컴파일러는 기본 클래스가 클래스 템플릿의 특수화인 경우 동일한 경고를 생성합니다. 이 문제를 해결 하려면 기본 클래스를로 표시 합니다 **`dllexport`** . 클래스 템플릿의 특수화와 관련 된 문제는를 어디에 배치할지를 표시 하는 데 **`__declspec(dllexport)`** 사용할 수 있습니다. 대신, 명시적으로 클래스 템플릿을 인스턴스화하고이 명시적 인스턴스화를로 표시 **`dllexport`** 합니다. 예를 들어:

    ```cpp
    template class __declspec(dllexport) B<int>;
    class __declspec(dllexport) D : public B<int> {
    // ...
    ```

   템플릿 인수가 파생 클래스일 경우 이 해결 방법은 실패합니다. 예를 들어:

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

   이는 템플릿에서 일반적인 패턴 이므로 하나 이상의 기본 클래스를 **`dllexport`** 포함 하는 클래스에 적용 될 때 및 하나 이상의 기본 클래스가 클래스 템플릿의 특수화 인 경우 컴파일러가의 의미 체계를 변경 했습니다. 이 경우 컴파일러는 **`dllexport`** 클래스 템플릿의 특수화에 암시적으로 적용 됩니다. 다음 작업을 수행 하 고 경고를 받을 수 없습니다.

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[dllexport, dllimport](../cpp/dllexport-dllimport.md)
