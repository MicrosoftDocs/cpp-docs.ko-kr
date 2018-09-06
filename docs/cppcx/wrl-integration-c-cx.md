---
title: WRL 통합 (C + + /cli CX) | Microsoft Docs
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 3ad43894-c574-477c-ad3e-240301f381d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff2fc36582e6ffbff8f7608a5a26cc472687132e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760980"
---
# <a name="wrl-integration-ccx"></a>WRL 통합(C++/CX)

자유롭게 WRL 코드와 Windows 런타임 c + + 템플릿 라이브러리 (WRL) 코드를 혼합할 수 있습니다. 동일한 번역 단위에 WRL 개체 핸들을 사용 하 여 선언 된 개체를 사용할 수 있습니다 (`^`) 표기법 및 WRL 스마트 포인터 (`ComPtr<T>`) 표기법입니다. 그러나 반환 값 및 WRL HRESULT 오류 코드 및 WRL 예외 처리 수동으로 해야 합니다.
  
## <a name="wrl-development"></a>WRL 개발

작성 하 고 WRL 구성 요소를 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [Windows 런타임 c + + 템플릿 라이브러리 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)합니다.

### <a name="example"></a>예제

다음 코드 조각은 WRL 및 WRL을 사용 하 여 Windows 런타임 클래스를 사용 하 고 메타 데이터 파일을 검사 하는 방법을 보여 줍니다.

이 예제에서는 구성 Microsoft Store 앱 포럼의 코드 조각에서 수행 됩니다. 이 코드 조각의 작성자가 제공한 고지 사항과 조건은 다음과 같습니다.

1. C + + Windows 런타임 형식에 반영 하기 위한 특정 Api를 제공 하지 않습니다 하지만 CLR 메타 데이터 파일과 완전히 호환 되는 형식에 대 한 Windows 메타 데이터 파일 (.winmd). Windows는 특정 형식에 대한 .winmd 파일을 가져오기 위한 새로운 메타데이터 검색 API(RoGetMetaDataFile)를 제공합니다. 그러나 이러한 API는 C++ 개발자만 사용할 수 있으므로 사용자가 클래스를 인스턴스화할 수 없습니다.

1. 또한 코드가 컴파일되면 Runtimeobject.lib 및 Rometadata.lib를 링커에 전달해야 합니다.

1. 이 조각은 있는 그대로 제공됩니다. 올바르게 작동할 것이라 예상하지만 오류를 포함하고 있을 수 있습니다.

```cpp
#include <hstring.h>
#include <cor.h>
#include <rometadata.h>
#include <rometadataresolution.h>
#include <collection.h>

namespace ABI_Isolation_Workaround {
    #include <inspectable.h>
    #include <WeakReference.h>
}
using namespace ABI_Isolation_Workaround;
#include <wrl/client.h>

using namespace Microsoft::WRL;
using namespace Windows::Foundation::Collections;

IVector<String^>^ GetTypeMethods(Object^);

MainPage::MainPage()
{
    InitializeComponent();

    Windows::Foundation::Uri^ uri = ref new Windows::Foundation::Uri("http://buildwindows.com/");
    auto methods = GetTypeMethods(uri);

    std::wstring strMethods;
    std::for_each(begin(methods), end(methods), [&strMethods](String^ methodName) {
        strMethods += methodName->Data();
        strMethods += L"\n";
    });

    wprintf_s(L"%s\n", strMethods.c_str());
}

IVector<String^>^ GetTypeMethods(Object^ instance)
{
    HRESULT hr;
    HSTRING hStringClassName;
    hr = instance->__cli_GetRuntimeClassName(reinterpret_cast<__cli_HSTRING__**>(&hStringClassName)); // internal method name subject to change post BUILD
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD
    String^ className = reinterpret_cast<String^>(hStringClassName);

    ComPtr<IMetaDataDispenserEx> metadataDispenser; ComPtr<IMetaDataImport2> metadataImport; hr = MetaDataGetDispenser(CLSID_CorMetaDataDispenser, IID_IMetaDataDispenser, (LPVOID*)metadataDispenser.GetAddressOf());
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD

    HSTRING hStringFileName;
    mdTypeDef typeDefToken;
    hr = RoGetMetaDataFile(hStringClassName, metadataDispenser.Get(), &hStringFileName, &metadataImport, &typeDefToken);
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD
    String^ fileName = reinterpret_cast<String^>(hStringFileName);

    HCORENUM hCorEnum = 0;
    mdMethodDef methodDefs[2048];
    ULONG countMethodDefs = sizeof(methodDefs);
    hr = metadataImport->EnumMethods(&hCorEnum, typeDefToken, methodDefs, countMethodDefs,  &countMethodDefs);
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD

    wchar_t methodName[1024];
    ULONG countMethodName;
    std::wstring strMethods;
    Vector<String^>^ retVal = ref new Vector<String^>();

    for (int i = 0; i < countMethodDefs; ++i)
    {
        countMethodName = sizeof(methodName);
        hr = metadataImport->GetMethodProps(methodDefs[i], nullptr, methodName, countMethodName, &countMethodName, nullptr, nullptr, nullptr, nullptr, nullptr);
        if (SUCCEEDED(hr))
        {
            methodName[ countMethodName ] = 0;
            retVal->Append(ref new String(methodName));
        }
    }
    return retVal;
}

```

## <a name="see-also"></a>참고자료

[다른 언어와 상호 운용](interoperating-with-other-languages-c-cx.md)  
