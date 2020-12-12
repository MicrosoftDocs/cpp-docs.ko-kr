---
description: '자세한 정보: 스레드'
title: 스레드(thread)
ms.date: 05/07/2019
f1_keywords:
- thread_cpp
helpviewer_keywords:
- thread local storage (TLS)
- thread __declspec keyword
- TLS (thread local storage), compiler implementation
- __declspec keyword [C++], thread
ms.assetid: 667f2a77-6d1f-4b41-bee8-05e67324fab8
ms.openlocfilehash: 7b83686b6641585e7e7af334a6127c71a9171610
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164707"
---
# <a name="thread"></a>스레드(thread)

**Microsoft 전용**

**`thread`** 확장 된 저장소 클래스 한정자는 스레드 지역 변수를 선언 하는 데 사용 됩니다. C + + 11 이상에서 이식 가능한 해당 항목의 경우 이식 가능한 코드에 [thread_local](../cpp/storage-classes-cpp.md#thread_local) 저장소 클래스 지정자를 사용 합니다. Windows에서는를 **`thread_local`** 사용 하 여를 구현 **`__declspec(thread)`** 합니다.

## <a name="syntax"></a>Syntax

**`__declspec(thread)`***선언 자*

## <a name="remarks"></a>설명

TLS(스레드 로컬 스토리지)는 다중 스레드 프로세스의 각 스레드가 스레드 데이터를 위한 스토리지를 할당하는 메커니즘입니다. 표준 다중 스레드 프로그램에서 데이터는 지정된 프로세스의 모든 스레드에서 공유되지만 스레드 로컬 스토리지는 스레드별 데이터를 할당하기 위한 메커니즘입니다. 스레드에 대 한 자세한 내용은 [다중 스레딩](../parallel/multithreading-support-for-older-code-visual-cpp.md)을 참조 하세요.

스레드 지역 변수의 선언에는 [확장 특성 구문과](../cpp/declspec.md) 키워드를 사용 해야 합니다 **`__declspec`** **`thread`** . 예를 들어, 다음 코드는 정수 스레드 로컬 변수를 선언한 다음 값으로 초기화합니다.

```cpp
__declspec( thread ) int tls_i = 1;
```

동적으로 로드 된 라이브러리에서 스레드 지역 변수를 사용 하는 경우 스레드 지역 변수가 올바르게 초기화 되지 않을 수 있는 요소를 알고 있어야 합니다.

1. 생성자를 비롯 한 함수 호출을 사용 하 여 변수를 초기화 하는 경우이 함수는 이진/DLL을 프로세스에 로드 하는 스레드와 이진/DLL이 로드 된 후에 시작 된 스레드에 대해서만 호출 됩니다. DLL이 로드 될 때 이미 실행 중인 다른 스레드에 대해서는 초기화 함수가 호출 되지 않습니다. 동적 초기화는 DLL_THREAD_ATTACH에 대 한 DllMain 호출에서 발생 하지만, 스레드가 시작 될 때 DLL이 프로세스에 있지 않은 경우 DLL은 해당 메시지를 받지 않습니다.

1. 상수 값을 사용 하 여 정적으로 초기화 된 스레드 로컬 변수는 일반적으로 모든 스레드에서 정상적으로 초기화 됩니다. 그러나 12 월 2017을 제외 하 고, Microsoft c + + 컴파일러에서는 **`constexpr`** 변수가 정적 초기화 대신 동적으로 수신 되는 알려진 규칙 문제가 있습니다.

   참고: 이러한 문제는 나중에 컴파일러를 업데이트할 때 수정 될 예정입니다.

또한 스레드 로컬 개체 및 변수를 선언 하는 경우 다음 지침을 따라야 합니다.

- **`thread`** 특성은 클래스 및 데이터 선언 및 정의에만 적용할 수 있으며 **`thread`** 함수 선언 또는 정의에는 사용할 수 없습니다.

- **`thread`** 특성은 정적 저장 기간이 있는 데이터 항목에만 지정할 수 있습니다. 여기에는 전역 데이터 개체 ( **`static`** 및 **`extern`** ), 지역 정적 개체 및 클래스의 정적 데이터 멤버가 포함 됩니다. 특성을 사용 하 여 자동 데이터 개체를 선언할 수 없습니다 **`thread`** .

- **`thread`** 선언과 정의가 동일한 파일이 나 별도의 파일에서 발생 하는지 여부에 상관 없이, 스레드 로컬 개체의 선언 및 정의에 대해 특성을 사용 해야 합니다.

- **`thread`** 특성은 형식 한정자로 사용할 수 없습니다.

- 특성을 사용 하는 개체의 선언이 허용 되기 때문에 **`thread`** 이러한 두 예제는 의미상 동일 합니다.

    ```cpp
    // declspec_thread_2.cpp
    // compile with: /LD
    __declspec( thread ) class B {
    public:
       int data;
    } BObject;   // BObject declared thread local.

    class B2 {
    public:
       int data;
    };
    __declspec( thread ) B2 BObject2;   // BObject2 declared thread local.
    ```

- 표준 C에서는 비정적 개체에 한 해 자신에 대 한 참조를 포함 하는 식을 사용 하 여 개체 또는 변수를 초기화할 수 있습니다. C + +에서는 일반적으로 자신에 대 한 참조를 포함 하는 식으로 개체를 동적으로 초기화할 수 있지만 스레드 로컬 개체에는이 형식의 초기화가 허용 되지 않습니다. 예를 들어:

   ```cpp
   // declspec_thread_3.cpp
   // compile with: /LD
   #define Thread __declspec( thread )
   int j = j;   // Okay in C++; C error
   Thread int tls_i = sizeof( tls_i );   // Okay in C and C++
   ```

   **`sizeof`** 초기화 되는 개체를 포함 하는 식은 자신에 대 한 참조를 구성 하지 않으며 c 및 c + +에서 허용 됩니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[__declspec](../cpp/declspec.md)<br/>
[키워드](../cpp/keywords-cpp.md)<br/>
[TLS (스레드 로컬 저장소)](../parallel/thread-local-storage-tls.md)
