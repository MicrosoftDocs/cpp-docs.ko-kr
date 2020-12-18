---
description: '자세한 정보: DLL에 실행 파일 링크'
title: DLL에 실행 파일 링크
ms.date: 08/22/2019
helpviewer_keywords:
- run time [C++], linking
- dynamic load linking [C++]
- linking [C++], DLLs
- DLLs [C++], linking
- implicit linking [C++]
- explicit linking [C++]
- executable files [C++], linking to DLLs
- loading DLLs [C++]
ms.assetid: 7592e276-dd6e-4a74-90c8-e1ee35598ea3
ms.openlocfilehash: bfcc1f506b1e9c8da14549795a9c282b66788c6b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172052"
---
# <a name="link-an-executable-to-a-dll"></a>DLL에 실행 파일 링크

실행 파일은 다음 두 가지 방법 중 하나로 DLL에 연결(또는 로드)됩니다.

- *암시적 연결*: 여기에서는 운영 체제가 DLL을 사용하는 실행 파일과 동시에 DLL을 로드합니다. 클라이언트 실행 파일은 마치 함수가 정적으로 연결되고 실행 파일 내에 포함된 것처럼 DLL의 내보낸 함수를 호출합니다. 암시적 연결은 때로 *정적 로드* 또는 *로드 시간 동적 연결* 이라고 합니다.

- *명시적 연결*: 여기에서 운영 체제는 런타임에 요청 시 DLL을 로드합니다. 명시적 연결로 DLL을 사용하는 실행 파일은 DLL을 명시적으로 로드하고 언로드해야 합니다. 또한 DLL에서 사용하는 각 함수에 액세스할 함수 포인터를 설정해야 합니다. 정적으로 연결된 라이브러리나 암시적으로 연결된 DLL에서 함수를 호출하는 것과 달리, 클라이언트 실행 파일은 함수 포인터를 통해 명시적으로 연결된 DLL에서 내보낸 함수를 호출해야 합니다. 명시적 연결은 때로 *동적 로드* 또는 *런타임 동적 연결* 이라고 합니다.

실행 파일은 이 두 연결 방법 중 하나를 사용하여 동일한 DLL에 연결할 수 있습니다. 뿐만 아니라 이러한 메서드는 상호 배타적이지 않습니다. 즉 하나의 실행 파일이 암시적으로 DLL에 연결될 수 있고, 다른 실행 파일은 명시적으로 DLL에 연결될 수 있습니다.

<a name="determining-which-linking-method-to-use"></a>

## <a name="determine-which-linking-method-to-use"></a>사용할 연결 방법 결정

암시적 연결을 사용할지 아니면 명시적 연결을 사용할지 여부는 애플리케이션에 대해 내려야 하는 아키텍처 의사 결정입니다. 각 방법에는 장단점이 있습니다.

### <a name="implicit-linking"></a>암시적 연결[C++]

암시적 연결은 애플리케이션의 코드가 내보낸 DLL 함수를 호출할 때 이루어집니다. 호출 실행 파일에 대한 소스 코드가 컴파일되거나 어셈블될 때 DLL 함수 호출은 개체 코드에 외부 함수 참조를 생성합니다. 이 외부 참조를 확인하려면 애플리케이션이 DLL 작성자가 제공하는 가져오기 라이브러리(.lib 파일)와 연결되어야 합니다.

가져오기 라이브러리에는 DLL을 로드하고 DLL의 함수에 대한 호출을 구현하는 코드만 포함되어 있습니다. 가져오기 라이브러리에서 외부 함수를 찾으면 해당 함수의 코드가 DLL에 있음을 링커에 알립니다. DLL에 대한 외부 참조를 확인하려면 링커는 프로세스가 시작될 때 DLL 코드를 찾을 수 있는 위치를 시스템에 알려주는 정보를 실행 파일에 추가하기만 하면 됩니다.

시스템이 동적으로 연결된 참조를 포함하는 프로그램을 시작하면 프로그램의 실행 파일에 있는 정보를 사용하여 필요한 DLL을 찾습니다. DLL을 찾을 수 없는 경우 시스템은 프로세스를 종료하고 오류를 보고하는 대화 상자를 표시합니다. 아니면 시스템은 DLL 모듈을 프로세스 주소 공간으로 매핑합니다.

어느 DLL이든 `DllMain`과 같은 초기화 및 종료 코드에 대한 진입점 함수가 있는 경우 운영 체제가 이 함수를 호출합니다. 진입점 함수에 전달된 매개 변수 중 하나는 DLL이 프로세스에 연결되고 있음을 나타내는 코드를 지정합니다. 진입점 함수에서 TRUE를 반환하지 않는 경우 시스템은 프로세스를 종료하고 오류를 보고합니다.

마지막으로 시스템은 프로세스의 실행 코드를 수정하여 DLL 함수에 대한 시작 주소를 제공합니다.

프로그램의 나머지 코드와 마찬가지로 로더는 프로세스가 시작될 때 DLL 코드를 프로세스의 주소 공간으로 매핑합니다. 운영 체제는 DLL 코드를 필요한 경우에만 메모리에 로드합니다. 따라서 이전 버전 Windows에서 로딩을 제어하기 위해 .def 파일이 사용하는 `PRELOAD` 및 `LOADONCALL` 코드 특성은 더 이상 의미가 없습니다.

### <a name="explicit-linking"></a>명시적 연결

암시적 연결이 가장 사용하기 쉬운 방법이므로 대부분의 애플리케이션은 이 방법을 사용합니다. 그러나 명시적 연결이 필요한 경우가 있습니다. 명시적 연결을 사용하는 몇 가지 일반적인 이유는 다음과 같습니다.

- 애플리케이션은 자신이 런타임까지 로드하는 DLL의 이름을 알지 못합니다. 예를 들어 애플리케이션은 시작할 때 구성 파일에서 DLL의 이름과 내보낸 함수를 가져올 수 있습니다.

- 프로세스 시작 시 DLL을 찾을 수 없으면 운영 체제에서 암시적 연결을 사용하는 프로세스를 종료합니다. 명시적 연결을 사용하는 프로세스는 이 상황에서 종료되지 않으며 오류로부터 복구를 시도할 수 있습니다. 예를 들어 프로세스에서 사용자에게 오류를 알리고 사용자가 DLL에 대한 다른 경로를 지정하게 할 수 있습니다.

- 연결된 DLL 중 하나라도 실패하는 `DllMain` 함수가 있는 경우에는 암시적 연결을 사용하는 프로세스도 종료됩니다. 명시적 연결을 사용하는 프로세스는 이 상황에서 종료되지 않습니다.

- 애플리케이션이 로드될 때 Windows에서 모든 DLL을 로드하기 때문에 많은 DLL에 암시적으로 연결되는 애플리케이션을 시작하는 속도가 느릴 수 있습니다. 시작 성능을 향상시키기 위해 애플리케이션은 로드 직후에 필요한 DLL에 대해서만 암시적 연결을 사용할 수 있습니다. 애플리케이션은 필요한 경우에만 다른 DLL을 로드하는 명시적 연결을 사용할 수 있습니다.

- 명시적 연결을 사용하면 가져오기 라이브러리를 사용하여 애플리케이션을 연결할 필요가 없습니다. DLL 변경으로 인해 내보내기 서수가 변경되는 경우 애플리케이션은 서수 값이 아닌 함수의 이름을 사용하여 `GetProcAddress`를 호출할 때는 다시 연결할 필요가 없습니다. 암시적 연결을 사용하는 애플리케이션은 여전히 변경된 가져오기 라이브러리에 다시 연결해야 합니다.

다음은 알아 두어야 할 명시적 연결의 두 가지 위험입니다.

- DLL에 `DllMain` 진입점 함수가 있는 경우 운영 체제는 `LoadLibrary`를 호출한 스레드의 컨텍스트에서 이 함수를 호출합니다. `FreeLibrary` 함수에 대한 상응하는 호출이 없었던 `LoadLibrary`에 대한 이전 호출로 인해 DLL이 이미 프로세스에 연결되어 있으면 진입점 함수가 호출되지 않습니다. `LoadLibrary`(또는 `AfxLoadLibrary`)를 호출할 때 이미 존재하는 모든 스레드가 초기화되지 않기 때문에 DLL이 `DllMain` 함수를 사용하여 프로세스의 각 스레드를 초기화하는 경우 명시적 연결로 인해 문제가 발생할 수 있습니다.

- DLL이 정적 범위 데이터를 `__declspec(thread)`으로 선언하는 경우 명시적으로 연결되면 보호 오류가 발생할 수 있습니다. `LoadLibrary`를 호출하여 DLL을 로드한 후에는 코드가 이 데이터를 참조할 때마다 보호 오류가 발생합니다. (정적 범위 데이터는 전역 및 로컬 정적 항목을 모두 포함합니다.) 따라서 DLL을 만들 때 스레드 로컬 스토리지를 사용해서는 안 됩니다. 피할 수 없는 경우 DLL을 동적으로 로드할 때 발생할 수 있는 문제에 대해 DLL 사용자에게 알립니다. 자세한 내용은 [동적 연결 라이브러리에서 스레드 로컬 스토리지 사용(Windows SDK)](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library)을 참조하세요.

<a name="linking-implicitly"></a>

## <a name="how-to-use-implicit-linking"></a>암시적 연결을 사용하는 방법

암시적 연결로 DLL을 사용하려면 클라이언트 실행 파일이 DLL 공급자로부터 다음 파일을 가져와야 합니다.

- DLL에서 내보낸 데이터, 함수 및 C++ 클래스의 선언을 포함하는 하나 이상의 헤더 파일(.h 파일). DLL에서 내보낸 클래스, 함수 및 데이터는 모두 헤더 파일에 `__declspec(dllimport)`으로 표시되어야 합니다. 자세한 내용은 [dllexport, dllimport](../cpp/dllexport-dllimport.md)를 참조하세요.

- 실행 파일에 연결할 가져오기 라이브러리. 링커는 DLL이 빌드될 때 가져오기 라이브러리를 만듭니다. 자세한 내용은 [링커 입력인 LIB 파일](reference/dot-lib-files-as-linker-input.md)을 참조하세요.

- 실제 DLL 파일입니다.

암시적 연결로 DLL에서 데이터, 함수 및 클래스를 사용하려면 클라이언트 소스 파일은 이를 선언하는 헤더 파일을 포함해야 합니다. 코딩 관점에서 내보낸 함수를 호출하는 것은 다른 함수 호출과 마찬가지입니다.

클라이언트 실행 파일을 빌드하려면 DLL의 가져오기 라이브러리와 연결해야 합니다. 외부 메이크파일 또는 빌드 시스템을 사용하는 경우에는 연결하는 다른 개체 파일이나 라이브러리와 함께 가져오기 라이브러리를 지정하세요.

운영 체제는 호출하는 실행 파일을 로드할 때 DLL 파일을 찾을 수 있어야 합니다. 즉 애플리케이션을 설치할 때 DLL을 배포하거나 DLL이 있는지 확인해야 합니다.

<a name="linking-explicitly"></a>

## <a name="how-to-link-explicitly-to-a-dll"></a>DLL에 명시적으로 연결하는 방법

명시적 연결로 DLL을 사용하려면 애플리케이션이 런타임에 DLL을 명시적으로 로드하는 함수 호출을 수행해야 합니다. DLL에 명시적으로 연결하려면 애플리케이션이 다음을 수행해야 합니다.

- [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) 또는 유사한 함수를 호출하여 DLL을 로드하고 모듈 핸들을 가져옵니다.

- [GetProcAddress](getprocaddress.md)를 호출하여 애플리케이션이 호출하는 내보낸 각 함수에 대한 함수 포인터를 가져옵니다. 애플리케이션은 포인터를 통해 DLL 함수를 호출하기 때문에 컴파일러는 외부 참조를 생성하지 않으므로 가져오기 라이브러리와 연결할 필요가 없습니다. 그러나 사용자가 호출하는 내보낸 함수의 호출 시그니처를 정의하는 **`typedef`** 또는 **`using`** 문이 있어야 합니다.

- DLL을 사용한 작업이 완료되면 [FreeLibrary](freelibrary-and-afxfreelibrary.md)를 호출합니다.

예를 들어 이 샘플 함수는 `LoadLibrary`를 호출하여 "MyDLL"이라는 DLL을 로드하고, `GetProcAddress`를 호출하여 "DLLFunc1"이라는 함수에 대한 포인터를 가져오고, 이 함수를 호출하여 결과를 저장한 다음, `FreeLibrary`를 호출하여 DLL을 언로드합니다.

```C
#include "windows.h"

typedef HRESULT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT*);

HRESULT LoadAndCallSomeFunction(DWORD dwParam1, UINT * puParam2)
{
    HINSTANCE hDLL;               // Handle to DLL
    LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer
    HRESULT hrReturnVal;

    hDLL = LoadLibrary("MyDLL");
    if (NULL != hDLL)
    {
        lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL, "DLLFunc1");
        if (NULL != lpfnDllFunc1)
        {
            // call the function
            hrReturnVal = lpfnDllFunc1(dwParam1, puParam2);
        }
        else
        {
            // report the error
            hrReturnVal = ERROR_DELAY_LOAD_FAILED;
        }
        FreeLibrary(hDLL);
    }
    else
    {
        hrReturnVal = ERROR_DELAY_LOAD_FAILED;
    }
    return hrReturnVal;
}
```

이 예와 달리 대부분의 경우 해당 DLL에 대한 애플리케이션에서 `LoadLibrary` 및 `FreeLibrary`를 한 번만 호출해야 합니다. DLL에서 여러 함수를 호출하거나 DLL 함수를 반복해서 호출하려는 경우에 특히 그렇습니다.

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [가져오기 라이브러리 및 내보내기 파일을 사용한 작업](reference/working-with-import-libraries-and-export-files.md)

- [동적 연결 라이브러리 검색 순서](/windows/win32/Dlls/dynamic-link-library-search-order)

## <a name="see-also"></a>참조

[Visual Studio에서 C/C++ DLL 만들기](dlls-in-visual-cpp.md)
