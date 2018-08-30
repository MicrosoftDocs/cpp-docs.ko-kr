---
title: '방법: WRL을 사용 하 여 클래식 COM 구성 요소 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 5efe7690-90d5-4c3c-9e53-11a14cefcb19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3844c0ad304c1ebd18a707ca1821b72b60e92707
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198021"
---
# <a name="how-to-create-a-classic-com-component-using-wrl"></a>방법: WRL을 사용하여 기본 COM 구성 요소 만들기

유니버설 Windows 플랫폼 (UWP) 앱에이 사용 하는 것 외에도 데스크톱 앱의 사용에 대 한 기본 클래식 COM 구성 요소를 만들려면 Windows 런타임 c + + 템플릿 라이브러리 (WRL)를 사용할 수 있습니다. COM 구성 요소를 만드는 Windows Runtime c + + 템플릿 라이브러리에 ATL 보다 적은 코드가 필요할 수 있습니다. Windows 런타임 c + + 템플릿 라이브러리를 지 원하는 COM의 하위 집합에 대 한 정보를 참조 하세요 [Windows 런타임 c + + 템플릿 라이브러리 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)합니다.

이 문서는 Windows 런타임 c + + 템플릿 라이브러리를 사용 하 여 기본 COM 구성 요소를 만드는 방법을 보여 줍니다. 사용자 요구에 가장 적합한 배포 메커니즘을 사용할 수 있지만 이 문서에서는 데스크톱 앱에서 COM 구성 요소를 등록 및 사용하는 기본 방법도 보여 줍니다.

### <a name="to-use-the-windows-runtime-c-template-library-to-create-a-basic-classic-com-component"></a>Windows 런타임 c + + 템플릿 라이브러리를 만드는 데 기본 클래식 COM 구성 요소

1. Visual Studio에서 만들기를 **빈 솔루션** 프로젝트입니다. 예를 들어, 프로젝트 이름을 `WRLClassicCOM`입니다.

2. 추가 된 **Win32 프로젝트** 솔루션입니다. 예를 들어, 프로젝트 이름을 `CalculatorComponent`입니다. 에 **응용 프로그램 설정** 탭을 선택 **DLL**합니다.

3. 추가 된 **Midl 파일 (.idl)** 프로젝트 파일입니다. 예를 들어, 파일 이름을 `CalculatorComponent.idl`입니다.

4. CalculatorComponent.idl에 다음 코드를 추가합니다.

   [!code-cpp[wrl-classic-com-component#1](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_1.idl)]

5. CalculatorComponent.cpp에서 `CalculatorComponent` 클래스를 정의합니다. 합니다 `CalculatorComponent` 클래스에서 상속 [Microsoft::WRL::RuntimeClass](../windows/runtimeclass-class.md)합니다. [Microsoft::WRL::RuntimeClassFlags\<ClassicCom >](../windows/runtimeclassflags-structure.md) 클래스에서 파생 되는 지정 [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) 아니라 [IInspectable](https://msdn.microsoft.com/library/br205821\(v=vs.85\).aspx)합니다. (`IInspectable` Windows 런타임 앱 구성 요소에만 사용할 수 있습니다.) `CoCreatableClass` 와 같은 함수를 사용 하 여 사용할 수 있는 클래스에 대 한 팩터리를 만듭니다 [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance)합니다.

   [!code-cpp[wrl-classic-com-component#2](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_2.cpp)]

6. 다음 코드를 사용 하 여 코드를 바꿉니다 `dllmain.cpp`합니다. 이 파일은 DLL 내보내기 함수를 정의합니다. 이러한 함수를 사용 합니다 [Microsoft::WRL::Module](../windows/module-class.md) 모듈에 대 한 클래스 팩터리를 관리 하는 클래스입니다.

   [!code-cpp[wrl-classic-com-component#3](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_3.cpp)]

7. 추가 된 **모듈 정의 파일 (.def)** 프로젝트 파일입니다. 예를 들어, 파일 이름을 `CalculatorComponent.def`입니다. 이 파일은 링커에 내보낼 함수의 이름을 제공합니다.

8. CalculatorComponent.def에 다음 코드를 추가합니다.

    ```
    LIBRARY

    EXPORTS
        DllGetActivationFactory PRIVATE
        DllGetClassObject       PRIVATE
        DllCanUnloadNow         PRIVATE
    ```

9. 링커 줄에 runtimeobject.lib를 추가합니다. 자세한 내용은 [합니다. 링커 입력 파일로 파일을 lib](../build/reference/dot-lib-files-as-linker-input.md)합니다.

### <a name="to-consume-the-com-component-from-a-desktop-app"></a>데스크톱 앱에서 COM 구성 요소를 사용하려면

1. Windows 레지스트리에 COM 구성 요소를 등록합니다. 이렇게 하려면 등록 항목 파일을 만들고, 이름을 `RegScript.reg`, 다음 텍스트를 추가 합니다. 바꿉니다  *\<dll 경로 >* DLL의 경로 사용 하 여-예를 들어 `C:\temp\WRLClassicCOM\Debug\CalculatorComponent.dll`합니다.

    ```
    Windows Registry Editor Version 5.00

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}]
    @="CalculatorComponent Class"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\InprocServer32]
    @="<dll-path>"
    "ThreadingModel"="Apartment"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\Programmable]

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\TypeLib]
    @="{9D3E6826-CB8E-4D86-8B14-89F0D7EFCD01}"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\Version]
    @="1.0"
    ```

2. RegScript.reg를 실행 하거나 프로젝트에 추가할 **빌드 후 이벤트**합니다. 자세한 내용은 [빌드 전 이벤트/빌드 후 이벤트 명령줄 대화 상자](/visualstudio/ide/reference/pre-build-event-post-build-event-command-line-dialog-box)합니다.

3. 추가 된 **Win32 콘솔 응용 프로그램** 프로젝트를 솔루션입니다. 예를 들어, 프로젝트 이름을 `Calculator`입니다.

4. 이 코드의 내용을 대체 하는 데 `Calculator.cpp`:

   [!code-cpp[wrl-classic-com-component#6](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_6.cpp)]

## <a name="robust-programming"></a>강력한 프로그래밍

이 문서는 표준 COM 함수를 사용 하 여 COM 구성 요소를 작성 하 고 모든 COM 기반 기술에 사용할 수 있도록 하는 Windows 런타임 c + + 템플릿 라이브러리를 사용할 수 있는 보여 줍니다. 또한 형식을 사용할 수 있습니다 Windows Runtime c + + 템플릿 라이브러리와 같은 [Microsoft::WRL::ComPtr](../windows/comptr-class.md) COM 및 기타 개체의 수명을 관리 하 여 데스크톱 앱에서 합니다. 다음 코드는 Windows 런타임 c + + 템플릿 라이브러리를 사용 하 여의 수명을 관리 하는 `ICalculatorComponent` 포인터입니다. `CoInitializeWrapper` 클래스는 COM 라이브러리가 해제되도록 보장하고 COM 라이브러리의 수명이 `ComPtr` 스마트 포인터 개체보다 길도록 보장하는 RAII 래퍼입니다.

[!code-cpp[wrl-classic-com-component#7](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_7.cpp)]

## <a name="see-also"></a>참고 항목

[Windows 런타임 C++ 템플릿 라이브러리(WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)