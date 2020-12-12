---
description: '자세히 알아보기: 방법: WRL를 사용 하 여 Windows 런타임 구성 요소 활성화 및 사용'
title: '방법: WRL을 사용하여 Windows 런타임 구성 요소 활성화 및 사용'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 54828f02-6af3-45d1-b965-d0104442f8d5
ms.openlocfilehash: 1f66565956b1f7c3a0232e9271131e4ae8d53101
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249947"
---
# <a name="how-to-activate-and-use-a-windows-runtime-component-using-wrl"></a>방법: WRL을 사용하여 Windows 런타임 구성 요소 활성화 및 사용

이 문서에서는 Windows 런타임 c + + 템플릿 라이브러리 (WRL)를 사용 하 여 Windows 런타임를 초기화 하는 방법과 Windows 런타임 구성 요소를 활성화 하 고 사용 하는 방법을 보여 줍니다.

구성 요소를 사용 하려면 구성 요소에서 구현 하는 형식에 대 한 인터페이스 포인터를 가져와야 합니다. Windows 런타임의 기본 기술은 COM (구성 요소 개체 모델) 이기 때문에 형식의 인스턴스를 유지 관리 하려면 COM 규칙을 따라야 합니다. 예를 들어 메모리에서 형식이 삭제 되는 시기를 결정 하는 *참조 횟수* 를 유지 해야 합니다.

Windows 런타임 사용을 간소화 하기 위해 Windows 런타임 c + + 템플릿 라이브러리는 참조 횟수를 자동으로 수행 하는 스마트 포인터 템플릿 [ComPtr \<T> ](comptr-class.md)를 제공 합니다. 변수를 선언 하는 경우 `ComPtr<` *인터페이스 이름* `>` *식별자* 를 지정 합니다. 인터페이스 멤버에 액세스 하려면 화살표 멤버 액세스 연산자 ( `->` )를 식별자에 적용 합니다.

> [!IMPORTANT]
> 인터페이스 함수를 호출 하는 경우 항상 HRESULT 반환 값을 테스트 합니다.

## <a name="activating-and-using-a-windows-runtime-component"></a>Windows 런타임 구성 요소 활성화 및 사용

다음 단계에서는 인터페이스를 사용 하 여 `Windows::Foundation::IUriRuntimeClass` Windows 런타임 구성 요소에 대 한 활성화 팩터리를 만들고 해당 구성 요소의 인스턴스를 만들고 속성 값을 검색 하는 방법을 보여 줍니다. 또한 Windows 런타임를 초기화 하는 방법을 보여 줍니다. 전체 예제는 다음과 같습니다.

> [!IMPORTANT]
> 일반적으로 UWP (유니버설 Windows 플랫폼) 앱에서 Windows 런타임 c + + 템플릿 라이브러리를 사용 하지만이 예제에서는 콘솔 앱을 사용 하 여 설명 합니다. 와 같은 함수 `wprintf_s` 는 UWP 앱에서 사용할 수 없습니다. UWP 앱에서 사용할 수 있는 형식 및 함수에 대 한 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원 되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) 및 [Uwp 앱 용 Win32 및 COM](/uwp/win32-and-com/win32-and-com-for-uwp-apps)을 참조 하세요.

#### <a name="to-activate-and-use-a-windows-runtime-component"></a>Windows 런타임 구성 요소를 활성화 하 고 사용 하려면

1. `#include`필요한 Windows 런타임, Windows 런타임 c + + 템플릿 라이브러리 또는 c + + 표준 라이브러리 헤더를 포함 합니다.

   [!code-cpp[wrl-consume-component#2](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_1.cpp)]

   .cpp 파일의 `using namespace` 지시문을 활용하여 코드를 보다 읽기 쉽게 만드는 것이 좋습니다.

2. 앱이 실행 되는 스레드를 초기화 합니다. 모든 앱은 해당 스레드 및 스레딩 모델을 초기화 해야 합니다. 이 예제에서는 [Microsoft:: WRL:: wrapper:: RoInitializeWrapper](roinitializewrapper-class.md) 클래스를 사용 하 여 Windows 런타임를 초기화 하 고 [RO_INIT_MULTITHREADED](/windows/win32/api/roapi/ne-roapi-ro_init_type) 을 스레딩 모델로 지정 합니다. `RoInitializeWrapper`클래스는 `Windows::Foundation::Initialize` 생성 시와 `Windows::Foundation::Uninitialize` 소멸 될 때를 호출 합니다.

   [!code-cpp[wrl-consume-component#3](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_2.cpp)]

   두 번째 문에서 [Roinitializewrapper:: HRESULT](roinitializewrapper-class.md#hresult) 연산자는를 호출 하 여를 반환 합니다 `HRESULT` `Windows::Foundation::Initialize` .

3. 인터페이스에 대 한 *활성화 팩터리* 를 만듭니다 `ABI::Windows::Foundation::IUriRuntimeClassFactory` .

   [!code-cpp[wrl-consume-component#4](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_3.cpp)]

   Windows 런타임는 정규화 된 이름을 사용 하 여 형식을 식별 합니다. `RuntimeClass_Windows_Foundation_Uri`매개 변수는 Windows 런타임에서 제공 하 고 필요한 런타임 클래스 이름을 포함 하는 문자열입니다.

4. URI를 나타내는 [Microsoft:: WRL:: 래퍼:: HString](hstring-class.md) 변수를 초기화 `"https://www.microsoft.com"` 합니다.

   [!code-cpp[wrl-consume-component#6](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_4.cpp)]

   Windows 런타임에서 Windows 런타임 사용 하는 문자열에 대해 메모리를 할당 하지 않습니다. 대신 Windows 런타임는 유지 관리 하 고 작업에 사용 하는 버퍼에 문자열의 복사본을 만든 다음 생성 된 버퍼에 대 한 핸들을 반환 합니다.

5. `IUriRuntimeClassFactory::CreateUri`팩터리 메서드를 사용 하 여 개체를 만듭니다 `ABI::Windows::Foundation::IUriRuntimeClass` .

   [!code-cpp[wrl-consume-component#7](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_5.cpp)]

6. 메서드를 호출 `IUriRuntimeClass::get_Domain` 하 여 속성의 값을 `Domain` 검색 합니다.

   [!code-cpp[wrl-consume-component#8](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_6.cpp)]

7. 콘솔에 도메인 이름을 인쇄 하 고를 반환 합니다. 모든 `ComPtr` 및 RAII 개체는 범위를 벗어나면 자동으로 릴리스됩니다.

   [!code-cpp[wrl-consume-component#9](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_7.cpp)]

   [WindowsGetStringRawBuffer](/windows/win32/api/winstring/nf-winstring-windowsgetstringrawbuffer) 함수는 URI 문자열의 기본 유니코드 형식을 검색 합니다.

다음은 전체 예제입니다.

[!code-cpp[wrl-consume-component#1](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_8.cpp)]

## <a name="compiling-the-code"></a>코드 컴파일

코드를 컴파일하려면 코드를 복사한 다음 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 후 `wrl-consume-component.cpp` Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

`cl.exe wrl-consume-component.cpp runtimeobject.lib`

## <a name="see-also"></a>참고 항목

[Windows 런타임 C++ 템플릿 라이브러리(WRL)](windows-runtime-cpp-template-library-wrl.md)
