---
description: '자세한 정보: 스레드 로컬 스토리지'
title: 스레드 로컬 스토리지
ms.date: 11/04/2016
helpviewer_keywords:
- thread-local variables
- TLS (thread local storage)
- thread storage-class attribute
- thread-local storage
- storage, thread local storage
ms.assetid: a0f1b109-c953-4079-aa10-e47f5483173d
ms.openlocfilehash: 188646ec6ae980cc61bd5882c15e2e9040e4a7ca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114340"
---
# <a name="thread-local-storage"></a>스레드 로컬 스토리지

**Microsoft 전용**

TLS(스레드 로컬 스토리지)는 지정된 다중 스레드 프로세스의 각 스레드에서 스레드별 데이터의 스토리지를 할당하는 메커니즘입니다. 표준 다중 스레드 프로그램에서 데이터는 지정된 프로세스의 모든 스레드에서 공유되지만 스레드 로컬 스토리지는 스레드별 데이터를 할당하기 위한 메커니즘입니다. 스레드에 대한 자세한 내용은 Windows SDK에서 [프로세스 및 스레드](/windows/win32/ProcThread/processes-and-threads)를 참조하세요.

Microsoft C 언어에는 스레드 로컬 변수를 선언하기 위해 __declspec 키워드와 함께 사용되는 확장 스토리지 클래스 특성, 스레드가 포함되어 있습니다. 예를 들어, 다음 코드는 정수 스레드 로컬 변수를 선언한 다음 값으로 초기화합니다.

```
__declspec( thread ) int tls_i = 1;
```

정적으로 바인딩된 스레드 로컬 변수를 선언하는 경우 이러한 지침을 준수해야 합니다.

- 동적 초기화가 있는 스레드 로컬 변수는 DLL이 로드되게 하는 스레드와 프로세스에서 이미 실행 중인 스레드에서만 초기화됩니다. 자세한 내용은 [스레드](../cpp/thread.md)를 참조하세요.

- 데이터 선언 및 정의에만 thread 특성을 적용할 수 있습니다. 함수 선언 또는 정의에는 사용할 수 없습니다. 예를 들어, 다음 코드는 컴파일러 오류를 생성합니다.

    ```C
    #define Thread   __declspec( thread )
    Thread void func();      /* Error */
    ```

- 정적 스토리지 기간이 있는 데이터 항목에만 thread 특성을 지정할 수 있습니다. 여기에는 전역 데이터(정적 및 외부 모두)와 지역 정적 데이터가 포함됩니다. 자동 데이터는 thread 특성을 사용하여 선언할 수 없습니다. 예를 들어, 다음 코드는 컴파일러 오류를 생성합니다.

    ```C
    #define Thread   __declspec( thread )
    void func1()
    {
        Thread int tls_i;            /* Error */
    }

    int func2( Thread int tls_i )    /* Error */
    {
       return tls_i;
    }
    ```

- 스레드 로컬 데이터의 선언과 정의가 같은 파일에서 발생하는지 다른 파일에서 발생하는지에 관계없이 해당 선언과 정의에 대해 thread 특성을 사용해야 합니다. 예를 들어, 다음 코드는 오류를 생성합니다.

    ```C
    #define Thread   __declspec( thread )
    extern int tls_i;     /* This generates an error, because the   */
    int Thread tls_i;     /* declaration and the definition differ. */
    ```

- thread 특성은 형식 한정자로 사용할 수 없습니다. 예를 들어, 다음 코드는 컴파일러 오류를 생성합니다.

    ```C
    char *ch __declspec( thread );      /* Error */
    ```

- 스레드 지역 변수의 주소는 상수로 간주되지 않으므로 이 주소를 포함하는 모든 식은 상수 식으로 간주되지 않습니다. 이는 스레드 지역 변수의 주소를 포인터에 대한 이니셜라이저로 사용할 수 없음을 의미합니다. 예를 들어, 컴파일러는 다음 코드를 오류로 플래그를 지정합니다.

    ```C
    #define Thread   __declspec( thread )
    Thread int tls_i;
    int *p = &tls_i;      /* Error */
    ```

- C에서는 비정적 범위의 개체에 한해 자신에 대한 참조를 포함하는 식으로 변수를 초기화할 수 있습니다. 예를 들어:

    ```C
    #define Thread   __declspec( thread )
    Thread int tls_i = tls_i;             /* Error */
    int j = j;                            /* Error */
    Thread int tls_i = sizeof( tls_i )    /* Okay  */
    ```

   초기화되는 변수를 포함하는 sizeof 식은 자신에 대한 참조를 구성하지 않으며 허용됩니다.

- **\_\_declspec(thread)** 의 사용은 DLL 가져오기의 [지연 로드](../build/reference/linker-support-for-delay-loaded-dlls.md)를 방해할 수 있습니다.

thread 특성 사용에 대한 자세한 내용은 [다중 스레딩 항목](../parallel/multithreading-support-for-older-code-visual-cpp.md)을 참조하세요.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[C 확장 스토리지 클래스 특성](../c-language/c-extended-storage-class-attributes.md)
