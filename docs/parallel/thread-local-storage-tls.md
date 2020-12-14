---
description: '자세한 정보: TLS (스레드 로컬 저장소)'
title: TLS
ms.date: 08/09/2019
helpviewer_keywords:
- multithreading [C++], Thread Local Storage
- TLS [C++]
- threading [C++], Thread Local Storage
- storing thread-specific data
- thread attribute
- Thread Local Storage [C++]
ms.assetid: 80801907-d792-45ca-b776-df0cf2e9f197
ms.openlocfilehash: 1259f0c3af84f90fcd82483d3891124d1553eeb9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342324"
---
# <a name="thread-local-storage-tls"></a>TLS

TLS(스레드 로컬 스토리지)는 지정된 다중 스레드 프로세스의 각 스레드에서 스레드별 데이터를 저장하는 위치를 할당하는 방법입니다. 동적으로 바인딩된 (런타임) 스레드별 데이터는 TLS API ([TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc))를 통해 지원 됩니다. 이제 Win32 및 Microsoft c + + 컴파일러는 기존 API 구현 뿐만 아니라 스레드 단위 데이터에 대 한 정적 바인딩 (로드 시간)을 지원 합니다.

## <a name="compiler-implementation-for-tls"></a><a name="_core_compiler_implementation_for_tls"></a> TLS에 대 한 컴파일러 구현

**C + + 11:**  **`thread_local`** 저장소 클래스 지정자는 개체 및 클래스 멤버에 대 한 스레드 로컬 저장소를 지정 하는 데 권장 되는 방법입니다. 자세한 내용은 [저장소 클래스 (c + +)](../cpp/storage-classes-cpp.md)를 참조 하세요.

또한 MSVC는 확장 저장소 클래스 한정자로 서의 Microsoft 전용 특성 [스레드](../cpp/thread.md)를 제공 합니다. 키워드를 사용 **`__declspec`** 하 여 변수를 선언 **`thread`** 합니다. 예를 들어, 다음 코드는 정수 스레드 로컬 변수를 선언한 다음 값으로 초기화합니다.

```C
__declspec( thread ) int tls_i = 1;
```

## <a name="rules-and-limitations"></a>규칙 및 제한 사항

정적으로 바인딩된 스레드 로컬 개체 및 변수를 선언할 때는 다음 지침을 준수해야 합니다. 이러한 지침은 [스레드](../cpp/thread.md) 및 [thread_local](../cpp/storage-classes-cpp.md)에 모두 적용 됩니다.

- **`thread`** 특성은 클래스 및 데이터 선언 및 정의에만 적용할 수 있습니다. 함수 선언 또는 정의에는 사용할 수 없습니다. 예를 들어, 다음 코드는 컴파일러 오류를 생성합니다.

    ```C
    __declspec( thread )void func();     // This will generate an error.
    ```

- **`thread`** 한정자는 익스텐트가 있는 데이터 항목에만 지정할 수 있습니다 **`static`** . 여기에는 전역 데이터 개체 ( **`static`** 및 **`extern`** ), 지역 정적 개체 및 c + + 클래스의 정적 데이터 멤버가 포함 됩니다. 자동 데이터 개체는 특성을 사용 하 여 선언할 수 없습니다 **`thread`** . 다음 코드는 컴파일러 오류를 생성합니다.

    ```C
    void func1()
    {
        __declspec( thread )int tls_i;            // This will generate an error.
    }

    int func2(__declspec( thread )int tls_i )     // This will generate an error.
    {
        return tls_i;
    }
    ```

- 스레드 로컬 개체의 선언 및 정의는 모두 특성을 지정 해야 합니다 **`thread`** . 예를 들어, 다음 코드는 오류를 생성합니다.

    ```C
    #define Thread  __declspec( thread )
    extern int tls_i;        // This will generate an error, since the
    int __declspec( thread )tls_i;        // declaration and definition differ.
    ```

- **`thread`** 특성은 형식 한정자로 사용할 수 없습니다. 예를 들어, 다음 코드는 컴파일러 오류를 생성합니다.

    ```C
    char __declspec( thread ) *ch;        // Error
    ```

- 특성을 사용 하는 c + + 개체의 선언이 허용 되기 때문에 **`thread`** 다음 두 예제는 의미상 동일 합니다.

    ```cpp
    __declspec( thread ) class B
    {
    // Code
    } BObject;  // OK--BObject is declared thread local.

    class B
    {
    // Code
    };
    __declspec( thread ) B BObject;  // OK--BObject is declared thread local.
    ```

- 스레드 로컬 개체의 주소는 상수로 간주 되지 않으며 이러한 주소를 포함 하는 모든 식은 상수 식으로 간주 되지 않습니다. 표준 C에서는 스레드 지역 변수의 주소를 개체나 포인터에 대 한 이니셜라이저로 사용 하지 못하게 하는 것이 효과가 있습니다. 예를 들어 다음 코드는 C 컴파일러에서 오류로 플래그 지정됩니다.

    ```C
    __declspec( thread ) int tls_i;
    int *p = &tls_i;       //This will generate an error in C.
    ```

   이 제한은 c + +에서 적용 되지 않습니다. C++에서는 모든 개체의 동적 초기화가 허용되기 때문에, 스레드 로컬 변수의 주소를 사용하는 식을 사용하여 개체를 초기화할 수 있습니다. 스레드 로컬 개체의 생성과 마찬가지로 수행 됩니다. 예를 들어 앞에 표시 된 코드는 c + + 소스 파일로 컴파일될 때 오류를 생성 하지 않습니다. 스레드 지역 변수의 주소는 주소가 사용 된 스레드가 존재 하는 동안에만 유효 합니다.

- 표준 C에서는 비정적 범위의 개체에 한 해 자신에 대 한 참조를 포함 하는 식을 사용 하 여 개체 또는 변수를 초기화할 수 있습니다. C + +에서는 일반적으로 자신에 대 한 참조를 포함 하는 식으로 개체를 동적으로 초기화할 수 있지만 스레드 로컬 개체에서는 이러한 종류의 초기화가 허용 되지 않습니다. 예를 들어:

    ```C
    __declspec( thread )int tls_i = tls_i;                // Error in C and C++
    int j = j;                               // OK in C++, error in C
    __declspec( thread )int tls_i = sizeof( tls_i )       // Legal in C and C++
    ```

   **`sizeof`** 초기화 되는 개체를 포함 하는 식은 자신에 대 한 참조를 나타내지 않으며 c 및 c + +에서 모두 사용할 수 있습니다.

   C + +는 스레드 로컬 저장소 기능에 대 한 향후 개선 사항으로 인해 스레드 데이터를 동적으로 초기화할 수 없습니다.

- Windows Vista 이전의 Windows 운영 체제에는 `__declspec( thread )` 몇 가지 제한 사항이 있습니다. DLL에서 데이터 또는 개체를로 선언 하는 경우 `__declspec( thread )` 동적으로 로드 되는 경우 보호 오류가 발생할 수 있습니다. DLL이 [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw)로 로드 된 후에는 코드에서 데이터를 참조할 때마다 시스템 오류가 발생 합니다 `__declspec( thread )` . 런타임에 스레드에 대한 전역 변수 공간이 할당되기 때문에, 이 공간의 크기는 애플리케이션의 요구 사항과 정적으로 연결되는 모든 DLL의 요구 사항을 계산하여 결정됩니다. 를 사용 하 `LoadLibrary` 는 경우로 선언 된 스레드 지역 변수를 허용 하도록이 공간을 확장할 수 없습니다 `__declspec( thread )` . Dll이로 로드 될 수 있는 경우 DLL에서 [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)와 같은 tls api를 사용 하 여 tls를 할당 `LoadLibrary` 합니다.

## <a name="see-also"></a>참고 항목

[C 및 Wind32를 사용한 다중 스레딩](multithreading-with-c-and-win32.md)
