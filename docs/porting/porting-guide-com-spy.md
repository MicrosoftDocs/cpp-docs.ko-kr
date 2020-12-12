---
description: '자세한 정보: 포팅 가이드: COM Spy'
title: '포팅 가이드: COM Spy'
ms.date: 11/04/2016
ms.assetid: 24aa0d52-4014-4acb-8052-f4e2e4bbc3bb
ms.openlocfilehash: 69a97a04d255e64fdde0d863e637d72dfb238967
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322637"
---
# <a name="porting-guide-com-spy"></a>포팅 가이드: COM Spy

이 항목은 이전 Visual Studio C++ 프로젝트를 최신 버전의 Visual Studio로 업그레이드하는 프로세스를 보여주는 일련의 문서 중 두 번째입니다. 이 항목의 예제 코드는 Visual Studio 2005를 사용하여 마지막으로 컴파일되었습니다.

## <a name="comspy"></a>COMSpy

COMSpy는 컴퓨터에서 서비스 구성 요소의 활동을 모니터링 및 기록하는 프로그램입니다. 서비스 구성 요소는 시스템에서 실행되며 동일한 네트워크의 컴퓨터에서 사용할 수 있는 COM+ 구성 요소입니다. Windows 제어판의 구성 요소 서비스 기능으로 관리됩니다.

### <a name="step-1-converting-the-project-file"></a>1단계. 프로젝트 파일 변환

프로젝트 파일은 쉽게 변환되며 마이그레이션 보고서를 생성합니다. 보고서에는 처리해야 할 수도 있는 문제를 알려주는 몇 개의 항목이 있습니다. 다음은 보고되는 문제 중 하나입니다(이 항목 전체에서 오류 메시지는 때때로 전체 경로를 제거하는 등 읽기 쉽도록 축약됨).

```Output
ComSpyAudit\ComSpyAudit.vcproj: MSB8012: $(TargetPath) ('C:\Users\UserName\Desktop\spy\spy\ComSpyAudit\.\XP32_DEBUG\ComSpyAudit.dll') does not match the Librarian's OutputFile property value '.\XP32_DEBUG\ComSpyAudit.dll' ('C:\Users\UserName\Desktop\spy\spy\XP32_DEBUG\ComSpyAudit.dll') in project configuration 'Unicode Debug|Win32'. This may cause your project to build incorrectly. To correct this, please make sure that $(TargetPath) property value matches the value specified in %(Lib.OutputFile).
```

프로젝트를 업그레이드할 때 자주 발생하는 문제 중 하나는 프로젝트 속성 대화 상자의 **링커 OutputFile** 설정을 검토해야 할 수도 있다는 것입니다. Visual Studio 2010 이전 프로젝트에서 OutputFile은 비표준 값으로 설정할 경우 자동 변환 마법사에서 문제가 발생하는 설정 중 하나입니다. 이 경우 출력 파일의 경로가 비표준 폴더인 XP32_DEBUG로 설정되었습니다. 이 오류에 대해 자세히 알아보기 위해, 중요한 변경 내용인 vcbuild에서 msbuild로의 변경을 포함하는 업그레이드인 Visual Studio 2010 프로젝트 업그레이드와 관련된 [블로그 게시물](https://devblogs.microsoft.com/cppblog/visual-studio-2010-c-project-upgrade-guide/)을 참조했습니다. 이 정보에 따라 새 프로젝트를 만들 때 **출력 파일** 설정의 기본값은 `$(OutDir)$(TargetName)$(TargetExt)`이지만, 변환된 프로젝트에서 모두 올바른지 확인할 수 없기 때문에 변환 중에는 설정되지 않았습니다. 그러나 OutputFile에 대해 이 값을 설정하고 작동하는지 살펴보겠습니다.  작동하므로 계속 진행할 수 있습니다. 비표준 출력 폴더를 사용할 특별한 이유가 없는 경우 표준 위치를 사용하는 것이 좋습니다. 이 경우 포팅 및 업그레이드 프로세스 중에 출력 위치를 비표준 폴더로 그대로 두었습니다. `$(OutDir)`은 **디버그** 구성의 XP32_DEBUG 폴더 및 **릴리스** 구성의 ReleaseU 폴더로 확인됩니다.

### <a name="step-2-getting-it-to-build"></a>2단계. 빌드

포팅된 프로젝트를 빌드하면 다양한 오류와 경고가 발생합니다.

다음 컴파일러 오류로 인해 `ComSpyCtl`이 컴파일되지 않습니다.

```Output
atlcom.h(611): error C2664: 'HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM,BOOL,ATL::ATL_PROPMAP_ENTRY *)': cannot convert argument 3 from 'const ATL::ATL_PROPMAP_ENTRY *' to 'ATL::ATL_PROPMAP_ENTRY *'atlcom.h(611): note: Conversion loses qualifiersatlcom.h(608): note: while compiling class template member function 'HRESULT ATL::IPersistStreamInitImpl<CComSpy>::Save(LPSTREAM,BOOL)'\spy\spy\comspyctl\ccomspy.h(28): note: see reference to class template instantiation 'ATL::IPersistStreamInitImpl<CComSpy>' being compiled
```

오류는 atlcom.h에서 `IPersistStreamInitImpl` 클래스의 `Save` 메서드를 참조합니다.

```cpp
STDMETHOD(Save)(_Inout_ LPSTREAM pStm, _In_ BOOL fClearDirty)
{
     T* pT = static_cast<T*>(this);
     ATLTRACE(atlTraceCOM, 2, _T("IPersistStreamInitImpl::Save\n"));
     return pT->IPersistStreamInit_Save(pStm, fClearDirty, T::GetPropertyMap());
}
```

문제는 이전 버전의 컴파일러에서 허용된 변환이 더 이상 유효하지 않은 것입니다. C++ 표준을 준수하기 위해 이전에 허용된 일부 코드가 더 이상 허용되지 않습니다. 이 경우 const 포인터가 필요한 함수에 const가 아닌 포인터를 전달하는 것은 안전하지 않습니다.  해결 방법은 `CComSpy` 클래스에서 `IPersistStreamInit_Save` 선언을 찾아 세 번째 매개 변수에 const 한정자를 추가하는 것입니다.

```cpp
HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM pStm, BOOL /* fClearDirty */, const ATL_PROPMAP_ENTRY* pMap)
```

유사한 방식으로 `IPersistStreamInit_Load`를 변경합니다.

```cpp
HRESULT IPersistStreamInit_Load(LPSTREAM pStm, const ATL_PROPMAP_ENTRY* pMap);
```

다음 오류는 등록을 다룹니다.

```Output
error MSB3073: The command "regsvr32 /s /c "C:\Users\username\Desktop\spy\spy\ComSpyCtl\.\XP32_DEBUG\ComSpyCtl.lib"error MSB3073: echo regsvr32 exec. time > ".\XP32_DEBUG\regsvr32.trg"error MSB3073:error MSB3073: :VCEnd" exited with code 3.
```

이 빌드 후 등록 명령은 더 이상 필요하지 않습니다. 대신, 사용자 지정 빌드 명령을 제거하고 **링커** 설정에서 출력을 등록하도록 지정합니다.

### <a name="dealing-with-warnings"></a>경고 처리

프로젝트에서 다음과 같은 링커 경고를 생성합니다.

```Output
warning LNK4075: ignoring '/EDITANDCONTINUE' due to '/SAFESEH' specification
```

`/SAFESEH` 컴파일러 옵션은 디버그 모드에서 유용하지 않습니다. 디버그 모드에서는 `/EDITANDCONTINUE`가 유용하므로 여기서 해결 방법은 **디버그** 구성에 대해서만 `/SAFESEH`를 사용하지 않도록 설정하는 것입니다. 속성 대화 상자에서 이 작업을 수행하려면 이 오류를 생성하는 프로젝트에 대한 속성 대화 상자를 열고, 먼저 **구성** 을 **디버그**(실제로는 **디버그 유니코드**)로 설정한 다음, **링커 고급** 섹션에서 **이미지에 안전한 예외 처리기가 있음** 속성을 **아니요**(`/SAFESEH:NO`)로 다시 설정합니다.

컴파일러에서 `PROP_ENTRY_EX`가 사용되지 않는다고 경고합니다. 보안되지 않으므로 `PROP_ENTRY_TYPE_EX`를 대신 사용하는 것이 좋습니다.

```cpp
BEGIN_PROPERTY_MAP(CComSpy)
     PROP_ENTRY_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_PAGE(CLSID_StockFontPage)
END_PROPERTY_MAP()
```

그에 따라 ccomspy.h의 코드를 변경하고 COM 형식을 적절하게 추가합니다.

```cpp
BEGIN_PROPERTY_MAP(CComSpy)
     PROP_ENTRY_TYPE_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy, VT_BSTR)
     PROP_ENTRY_TYPE_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)
     PROP_ENTRY_TYPE_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)
     PROP_ENTRY_TYPE_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy, VT_UINT)
     PROP_PAGE(CLSID_StockFontPage)
END_PROPERTY_MAP()
```

이제 보다 엄격한 컴파일러 규칙 검사에 의해서도 발생하는 마지막 몇 개의 경고를 살펴보겠습니다.

```Output
\spy\comspyctl\usersub.h(70): warning C4457: declaration of 'var' hides function parameter\spy\comspyctl\usersub.h(48): note: see declaration of 'var'\spy\comspyctl\usersub.h(94): warning C4018: '<': signed/unsigned mismatch  ComSpy.cpp\spy\comspyctl\comspy.cpp(186): warning C4457: declaration of 'bHandled' hides function parameter\spy\spy\comspyctl\comspy.cpp(177): note: see declaration of 'bHandled'
```

경고 C4018은 다음 코드에서 발생합니다.

```cpp
for (i=0;i<lCount;i++)
    CoTaskMemFree(pKeys[i]);
```

문제는 `i` 는로 선언 되 `UINT` 고 `lCount` 로 선언 되므로 부호 있는 **`long`** /부호 없는 불일치입니다. 형식을 `lCount` `UINT` 사용 하 `IMtsEventInfo::get_Count` **`long`** 고 사용자 코드에 있지 않으므로의 형식을로 변경 하는 것은 불편할 수 있습니다. 따라서 코드에 캐스트를 추가합니다. C 스타일 캐스트는 이와 같은 숫자 캐스트에 대해 수행 하지만 **`static_cast`** 권장 되는 스타일입니다.

```cpp
for (i=0;i<static_cast<UINT>(lCount);i++)
    CoTaskMemFree(pKeys[i]);
```

이러한 경고는 동일한 이름의 매개 변수가 있는 함수에서 변수가 선언되어 잠재적으로 코드가 모호해질 수 있는 경우입니다. 지역 변수의 이름을 변경하여 이 문제를 해결했습니다.

### <a name="step-3-testing-and-debugging"></a>3단계. 테스트 및 디버깅

먼저 다양한 메뉴 및 명령을 실행한 후 애플리케이션을 닫아 앱을 테스트했습니다. 발견된 문제는 앱을 닫을 때 발생하는 디버그 어설션뿐이었습니다. 이 문제는 애플리케이션의 기본 COM 구성 요소인 `CSpyCon` 개체의 기본 클래스인 `CWindowImpl`의 소멸자에서 나타났습니다. atlwin.h의 다음 코드에서 어설션 오류가 발생했습니다.

```cpp
virtual ~CWindowImplRoot()
{
     #ifdef _DEBUG
     if(m_hWnd != NULL)// should be cleared in WindowProc
     {
          ATLTRACE(atlTraceWindowing, 0, _T("ERROR - Object deleted before window was destroyed\n"));
          ATLASSERT(FALSE);
     }
     #endif //_DEBUG
}
```

`hWnd`는 일반적으로 `WindowProc` 함수에서 0으로 설정되지만 창을 닫는 Windows 메시지(WM_SYSCOMMAND)에 대해 기본 `WindowProc` 대신 사용자 지정 처리기가 호출되었기 때문에 0으로 설정되지 않았습니다. 사용자 지정 처리기에서 `hWnd`를 0으로 설정하지 않았습니다. MFC의 `CWnd` 클래스에서 유사한 코드를 살펴보면 창을 삭제할 때 `OnNcDestroy`가 호출되고, MFC의 설명서에서 `CWnd::OnNcDestroy`를 재정의할 때 창에서 창 핸들을 분리하는 작업, 즉 `hWnd`를 0으로 설정하는 작업을 포함하여 올바른 정리 작업이 수행되도록 기본 `NcDestroy`를 호출해야 한다고 조언합니다. 동일한 어설션 코드가 이전 버전의 atlwin.h에 있었기 때문에 원래 버전의 샘플에서도 이 어설션이 트리거되었을 수 있습니다.

앱의 기능을 테스트하기 위해 ATL 프로젝트 템플릿을 사용하여 **서비스 구성 요소** 를 만들고 ATL 프로젝트 마법사에서 COM+ 지원을 추가하도록 선택했습니다. 이전에 서비스 구성 요소를 사용 하지 않은 경우에는이를 만들고 다른 앱이 사용할 수 있도록 시스템 또는 네트워크에서 등록 하 고 사용할 수 있는 것은 어려울 수 있습니다. COM Spy 앱은 진단 보조 기능으로 서비스 구성 요소의 활동을 모니터링하도록 설계되었습니다.

그런 다음, 클래스를 추가하고, ATL 개체를 선택하고, `Dog`라는 개체 이름을 지정했습니다. 그런 다음 dog.h 및 dog.cpp에서 구현을 추가했습니다.

```cpp
STDMETHODIMP CDog::Wag(LONG* lDuration)
{
    // TODO: Add your implementation code here
    *lDuration = 100l;
    return S_OK;
}
```

다음으로, Windows 제어판의 **서비스 구성 요소** 응용 프로그램을 사용 하 여 빌드 및 등록 하 고 (Visual Studio를 관리자 권한으로 실행 해야 함) 활성화 했습니다. C# Windows Forms 프로젝트를 만들고 도구 상자에서 폼으로 단추를 끌어다 놓은 다음 click 이벤트 처리기에 대해 단추를 두 번 클릭했습니다. 다음 코드를 추가하여 `Dog` 구성 요소를 인스턴스화했습니다.

```cpp
private void button1_Click(object sender, EventArgs e)
{
    ATLProjectLib.Dog dog1 = new ATLProjectLib.Dog();
    dog1.Wag();
}
```

이 코드는 문제없이 실행되었으며, COM Spy가 작동하여 실행되고 `Dog` 구성 요소를 모니터링하도록 구성된 경우 활동을 보여 주는 많은 데이터가 나타납니다.

## <a name="see-also"></a>참고 항목

[포팅 및 업그레이드: 예제 및 사례 연구](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[다음 예제: Spy++](../porting/porting-guide-spy-increment.md)<br/>
[이전 예제: MFC Scribble](../porting/porting-guide-mfc-scribble.md)
