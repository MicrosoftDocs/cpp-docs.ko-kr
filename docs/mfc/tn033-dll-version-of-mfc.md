---
title: 'TN033: MFC의 DLL 버전'
description: Mfc 응용 프로그램 및 mfc 확장명 Dll에서 MFC 공유 동적 연결 라이브러리를 사용 하는 방법을 보여 줍니다.
ms.date: 11/30/2020
helpviewer_keywords:
- MFC DLLs [MFC], writing MFC extension DLLS
- AFXDLL library
- DLLs [MFC], MFC
- DLL version of MFC [MFC]
- TN033
ms.openlocfilehash: b9330fe7c756f962a8b06a04b840bfda343f3a49
ms.sourcegitcommit: 432c24dde31c400437c4320e8432b1ddb232f844
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440314"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033: MFC의 DLL 버전

이 정보는 *`MFCxx.DLL`* *`MFCxxD.DLL`* mfc 응용 프로그램 및 Mfc 확장명 dll을 사용 하 여 및 (여기서 *xx* 는 mfc 버전 번호) 공유 동적 연결 라이브러리를 사용 하는 방법을 설명 합니다. 일반 MFC Dll에 대 한 자세한 내용은 [dll의 일부로 MFC 사용](../mfc/tn011-using-mfc-as-part-of-a-dll.md)을 참조 하세요.

이 기술 참고 사항은 Dll의 세 가지 측면을 다룹니다. 마지막 두 가지는 고급 사용자를 위한 것입니다.

- [MFC 확장 DLL을 빌드하는 방법](#_mfcnotes_how_to_write_an_mfc_extension_dll)

- [MFC의 DLL 버전을 사용 하는 MFC 응용 프로그램을 빌드하는 방법](#_mfcnotes_writing_an_application_that_uses_the_dll_version)

- [MFC 공유 동적 연결 라이브러리를 구현 하는 방법](#_mfcnotes_how_the_mfc30.dll_is_implemented)

Mfc가 아닌 응용 프로그램 ( *일반 MFC DLL* 이라고 함)과 함께 사용할 수 있는 mfc를 사용 하 여 DLL을 빌드하는 데 관심이 있는 경우 [기술 참고 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md)을 참조 하세요.

## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>MFCxx.DLL 지원 개요: 용어 및 파일

**일반 MFC dll**: 일반 mfc dll을 사용 하 여 일부 mfc 클래스를 사용 하 여 독립 실행형 DLL을 빌드합니다. 앱/DLL 경계의 인터페이스는 "C" 인터페이스 이며 클라이언트 응용 프로그램은 MFC 응용 프로그램 일 필요가 없습니다.

기본 MFC Dll은 MFC 1.0에서 지원 되는 Dll의 버전입니다. [기술 정보 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md) 및 MFC 고급 개념 샘플에서 설명 [`DLLScreenCap`](../overview/visual-cpp-samples.md) 합니다.

> [!NOTE]
> Visual C++ 버전 4.0을 기준으로 **USRDLL** 라는 용어는 사용 되지 않으며, 정적으로 mfc에 링크 하는 일반 mfc DLL로 대체 되었습니다. MFC에 동적으로 연결 되는 일반 MFC DLL을 빌드할 수도 있습니다.

MFC 3.0 이상에서는 OLE 및 데이터베이스 클래스를 비롯 한 모든 새로운 기능을 사용 하 여 일반 MFC Dll을 지원 합니다.

**AFXDLL**: MFC 라이브러리의 공유 버전도 라고도 합니다. MFC 2.0에 추가 된 새로운 DLL 지원입니다. MFC 라이브러리 자체는 여러 Dll에 있습니다 (아래 설명 참조). 클라이언트 응용 프로그램 또는 DLL은 필요한 Dll을 동적으로 연결 합니다. 응용 프로그램/DLL 경계의 인터페이스는 c + +/MFC 클래스 인터페이스입니다. 클라이언트 응용 프로그램은 MFC 응용 프로그램 이어야 합니다. 이 DLL은 모든 MFC 3.0 기능을 지원 합니다 (예외: 데이터베이스 클래스에 대해 유니코드가 지원 되지 않음).

> [!NOTE]
> Visual C++ 버전 4.0을 통해이 DLL 유형을 "확장 DLL" 이라고 합니다.

이 메모는 *`MFCxx.DLL`* 를 사용 하 여 전체 MFC DLL 집합을 참조 합니다. 여기에는 다음이 포함 됩니다.

- Debug: *`MFCxxD.DLL`* (결합) 및 *`MFCSxxD.LIB`* (정적)

- Release: *`MFCxx.DLL`* (결합) 및 *`MFCSxx.LIB`* (정적)

- 유니코드 디버그: *`MFCxxUD.DLL`* (결합) 및 *`MFCSxxD.LIB`* (정적)

- 유니코드 릴리스: *`MFCxxU.DLL`* (결합) 및 *`MFCSxxU.LIB`* (정적)

> [!NOTE]
> *`MFCSxx[U][D].LIB`* 라이브러리는 MFC 공유 dll과 함께 사용 됩니다. 이러한 라이브러리에는 응용 프로그램 또는 DLL에 정적으로 연결 되어야 하는 코드가 포함 되어 있습니다.

응용 프로그램은 해당 하는 가져오기 라이브러리에 연결 됩니다.

- 디버그 *`MFCxxD.LIB`*

- 릴리스 *`MFCxx.LIB`*

- 유니코드 디버그: *`MFCxxUD.LIB`*

- 유니코드 릴리스: *`MFCxxU.LIB`*

*Mfc 확장 dll* 은 *`MFCxx.DLL`* (또는 다른 mfc 공유 dll)를 확장 하는 dll입니다. 여기서는 MFC 구성 요소 아키텍처가 시작 됩니다. MFC 클래스에서 유용한 클래스를 파생 시키거나 다른 MFC 유사 도구 키트를 빌드하는 경우 DLL에 삽입할 수 있습니다. 에서 사용 하는 DLL은 *`MFCxx.DLL`* 최종 클라이언트 응용 프로그램과 마찬가지로를 사용 합니다. MFC 확장 DLL은 다시 사용할 수 있는 리프 클래스, 재사용 가능한 기본 클래스 및 재사용 가능한 뷰와 문서 클래스를 허용 합니다.

## <a name="pros-and-cons"></a>장점 및 단점

MFC의 공유 버전을 사용 해야 하는 이유

- 공유 라이브러리를 사용 하면 더 작은 응용 프로그램이 생성 될 수 있습니다. 대부분의 MFC 라이브러리를 사용 하는 최소 응용 프로그램은 10K 보다 낮습니다.

- 공유 버전의 MFC는 MFC 확장명 Dll 및 일반 MFC Dll을 지원 합니다.

- 정적으로 연결 된 MFC 응용 프로그램 보다는 공유 MFC 라이브러리를 사용 하는 응용 프로그램을 빌드하는 것이 더 빠릅니다. 이는 MFC 자체를 연결할 필요가 없기 때문입니다. **`DEBUG`** 링커가 디버그 정보를 압축 해야 하는 빌드에서 특히 그렇습니다. 응용 프로그램이 디버그 정보를 이미 포함 하 고 있는 DLL에 연결 된 경우 압축할 디버그 정보가 줄어듭니다.

공유 버전의 MFC를 사용 하지 않는 이유는 다음과 같습니다.

- 공유 라이브러리를 사용 하는 응용 프로그램을 제공 하려면 *`MFCxx.DLL`* 및 기타 라이브러리를 프로그램에 제공 해야 합니다. *`MFCxx.DLL`* 는 많은 Dll과 같이 자유롭게 재배포할 수 있지만 설치 프로그램에 DLL을 설치 해야 합니다. 또한 프로그램 및 MFC Dll 자체에서 사용 되는 다른 재배포 가능 라이브러리를 제공 해야 합니다.

## <a name="how-to-write-an-mfc-extension-dll"></a><a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a> MFC 확장 DLL을 작성 하는 방법

MFC 확장 DLL은 MFC 클래스의 기능을 확장 하는 클래스와 함수를 포함 하는 DLL입니다. MFC 확장 DLL은 응용 프로그램에서 사용 하는 것과 동일한 방식으로 공유 MFC Dll을 사용 합니다. 몇 가지 추가 고려 사항이 있습니다.

- 빌드 프로세스는 몇 가지 추가 컴파일러 및 링커 옵션으로 공유 된 MFC 라이브러리를 사용 하는 응용 프로그램을 빌드하는 것과 비슷합니다.

- MFC 확장 DLL에는 `CWinApp` 파생 클래스가 없습니다.

- MFC 확장 DLL은 특수를 제공 해야 합니다 `DllMain` . 응용 프로그램 마법사는 `DllMain` 수정할 수 있는 함수를 제공 합니다.

- Mfc 확장 dll `CDynLinkLibrary` 은 `CRuntimeClass` 응용 프로그램에 형식 또는 리소스를 내보내는 경우 일반적으로를 만드는 초기화 루틴을 제공 합니다. `CDynLinkLibrary`MFC 확장 DLL에서 응용 프로그램 별 데이터를 유지 관리 해야 하는 경우의 파생 클래스를 사용할 수 있습니다.

이러한 고려 사항은 아래에 자세히 설명 되어 있습니다. 또한 MFC 고급 개념 샘플을 참조 [`DLLHUSK`](../overview/visual-cpp-samples.md) 하세요. 다음 작업을 수행 하는 방법을 보여 줍니다.

- 공유 라이브러리를 사용 하 여 응용 프로그램을 빌드합니다. *`DLLHUSK.EXE`* 는 mfc 라이브러리 및 기타 dll에 동적으로 연결 되는 mfc 응용 프로그램입니다.

- MFC 확장 DLL을 빌드합니다. MFC 확장 DLL을 빌드할 때와 같은 특수 플래그를 사용 하는 방법을 보여 줍니다 `_AFXEXT` .

- MFC 확장 Dll의 두 가지 예제를 빌드합니다. 하나는 TESTDLL1 (제한 된 내보내기)를 사용 하는 MFC 확장 DLL의 기본 구조를 보여주고 다른 하나는 TESTDLL2 (전체 클래스 인터페이스)를 내보내는 것을 보여 줍니다.

클라이언트 응용 프로그램과 MFC 확장 Dll은 모두 동일한 버전의를 사용 해야 합니다 *`MFCxx.DLL`* . MFC Dll의 규칙을 따르고 MFC 확장명 DLL의 디버그 및 릴리스 () 버전을 모두 제공 **`/release`** 합니다. 이 방법을 사용 하면 클라이언트 프로그램에서 응용 프로그램의 디버그 버전과 릴리스 버전을 모두 빌드하고 모든 Dll의 적절 한 디버그 또는 릴리스 버전에 연결할 수 있습니다.

> [!NOTE]
> C + + 이름 및 내보내기 문제 때문에 다른 플랫폼에 대 한 dll과 dll의 디버그 버전과 릴리스 버전 간에 MFC 확장명 DLL의 내보내기 목록이 다를 수 있습니다. 릴리스에는 *`MFCxx.DLL`* 2000 개의 내보내진 진입점이 있습니다. 디버그에는 *`MFCxxD.DLL`* 3000 개의 내보낸 진입점이 있습니다.

### <a name="quick-note-on-memory-management"></a>메모리 관리에 대 한 빠른 노트

이 기술 정보 뒷부분의 "메모리 관리" 섹션에서는 *`MFCxx.DLL`* 공유 버전의 MFC를 사용 하 여를 구현 하는 방법을 설명 합니다. MFC 확장 DLL을 구현 하기 위해 알아야 하는 정보는 여기에 설명 되어 있습니다.

*`MFCxx.DLL`* 클라이언트 응용 프로그램의 주소 공간에 로드 된 모든 MFC 확장 Dll은 같은 응용 프로그램에 있는 것 처럼 동일한 메모리 할당자, 리소스 로드 및 기타 MFC "전역" 상태를 사용 합니다. Mfc에 정적으로 연결 되는 MFC DLL이 아닌 라이브러리와 일반 MFC Dll은 정확히 반대 방향으로 수행 됩니다. 각 DLL은 자체 메모리 풀에서 할당 합니다.

MFC 확장 DLL에서 메모리를 할당 하는 경우 해당 메모리는 다른 응용 프로그램 할당 개체와 자유롭게 섞 수 있습니다. 또한 공유 MFC 라이브러리를 사용 하는 응용 프로그램이 충돌 하는 경우 운영 체제는 DLL을 공유 하는 다른 모든 MFC 응용 프로그램의 무결성을 유지 합니다.

마찬가지로, 다른 "전역" MFC 상태 (예: 리소스를 로드 하는 현재 실행 파일)도 클라이언트 응용 프로그램, 모든 MFC 확장명 Dll 및 자체 간에 공유 *`MFCxx.DLL`* 됩니다.

### <a name="building-an-mfc-extension-dll"></a>MFC 확장 DLL 빌드

응용 프로그램 마법사를 사용 하 여 MFC 확장명 DLL 프로젝트를 만들 수 있으며, 적절 한 컴파일러 및 링커 설정이 자동으로 생성 됩니다. 또한 `DllMain` 수정할 수 있는 함수를 생성 합니다.

기존 프로젝트를 MFC 확장명 DLL로 변환 하는 경우 공유 버전의 MFC를 사용 하 여 빌드하는 표준 설정부터 시작 합니다. 그런 다음 다음과 같이 변경 합니다.

- **`/D_AFXEXT`** 컴파일러 플래그에를 추가 합니다. 프로젝트 속성 대화 상자에서 **C/c + +**  >  **전처리기** 범주를 선택 합니다. `_AFXEXT`각 항목을 세미콜론으로 구분 하 여 **매크로 정의** 필드에를 추가 합니다.

- **`/Gy`** 컴파일러 스위치를 제거 합니다. 프로젝트 속성 대화 상자에서 **C/c + +**  >  **코드 생성** 범주를 선택 합니다. **Function-Level 연결 사용** 속성이 사용 하도록 설정 되어 있지 않은지 확인 합니다. 이 설정을 사용 하면 링커가 참조 되지 않은 함수를 제거 하지 않으므로 더 쉽게 클래스를 내보낼 수 있습니다. 원본 프로젝트에서 정적으로 MFC에 링크 된 기본 MFC DLL을 빌드한 경우 **`/MT`** (또는 **`/MTd`** ) 컴파일러 옵션을 **`/MD`** (또는)로 변경 **`/MDd`** 합니다.

- 링크할 옵션을 사용 하 여 내보내기 라이브러리를 빌드합니다 **`/DLL`** . 이 옵션은 새 대상을 만들고 Win32 Dynamic-Link 라이브러리를 대상 유형으로 지정 하는 경우에 설정 됩니다.

### <a name="changing-your-header-files"></a>헤더 파일 변경

MFC 확장 DLL의 일반적인 목표는 해당 기능을 사용할 수 있는 하나 이상의 응용 프로그램에 몇 가지 일반적인 기능을 내보내는 것입니다. 기본적으로 DLL은 클라이언트 응용 프로그램에서 사용할 클래스 및 전역 함수를 내보냅니다.

각 멤버 함수가 가져오기 또는 내보내기에 맞게 표시 되도록 하려면 특수 선언 및를 사용 합니다 `__declspec(dllexport)` `__declspec(dllimport)` . 클라이언트 응용 프로그램에서 클래스를 사용 하는 경우 클래스를로 선언 하려고 `__declspec(dllimport)` 합니다. MFC 확장 DLL 자체가 빌드되면 함수는로 선언 해야 합니다 `__declspec(dllexport)` . 또한 빌드된 DLL은 클라이언트 프로그램이 로드 시 바인딩할 수 있도록 함수를 내보내야 합니다.

전체 클래스를 내보내려면 `AFX_EXT_CLASS` 클래스 정의에서를 사용 합니다. 프레임 워크는 `__declspec(dllexport)` 및가 정의 될 때이 매크로 `_AFXDLL` 를 정의 `_AFXEXT` 하지만가 `__declspec(dllimport)` `_AFXEXT` 정의 되지 않은 경우로 정의 합니다. `_AFXEXT` 는 MFC 확장명 DLL을 빌드할 때만 정의 됩니다. 다음은 그 예입니다. 

```cpp
class AFX_EXT_CLASS CExampleExport : public CObject
{ /* ... class definition ... */ };
```

### <a name="not-exporting-the-entire-class"></a>전체 클래스를 내보내지 않음

클래스의 필요한 개별 멤버만 내보내려는 경우가 있습니다. 예를 들어 파생 클래스를 내보내는 경우 `CDialog` 생성자와 호출만 내보내야 할 수 있습니다 `DoModal` . DLL의 DEF 파일을 사용 하 여 이러한 멤버를 내보낼 수 있지만 `AFX_EXT_CLASS` 내보내기에 필요한 개별 멤버에 대해 거의 동일한 방법으로를 사용할 수도 있습니다.

다음은 그 예입니다. 

```cpp
class CExampleDialog : public CDialog
{
public:
    AFX_EXT_CLASS CExampleDialog();
    AFX_EXT_CLASS int DoModal();
    // rest of class definition
    // ...
};
```

이렇게 하면 클래스의 모든 멤버를 내보내지 않으므로 추가 문제가 발생할 수 있습니다. 이 문제는 MFC 매크로의 작동 방식에 있습니다. 여러 MFC 도우미 매크로는 실제로 데이터 멤버를 선언하거나 정의합니다. DLL도 이러한 데이터 멤버를 내보내야 합니다.

예를 들어 DECLARE_DYNAMIC 매크로는 MFC 확장명 DLL을 빌드할 때 다음과 같이 정의 됩니다.

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
    static CRuntimeClass* PASCAL _GetBaseClass(); \
    public: \
    static AFX_DATA CRuntimeClass class##class_name; \
    virtual CRuntimeClass* GetRuntimeClass() const; \
```

시작 하는 줄은 `static AFX_DATA` 클래스 내에서 정적 개체를 선언 합니다. 이 클래스를 올바르게 내보내고 클라이언트 EXE에서 런타임 정보에 액세스 하려면이 정적 개체를 내보내야 합니다. 정적 개체는 한정자를 사용 하 여 선언 되므로 `AFX_DATA` DLL을 빌드하는 경우에만 정의 하면 됩니다 `AFX_DATA` `__declspec(dllexport)` . `__declspec(dllimport)`클라이언트 실행 파일을 빌드할 때로 정의 합니다.

위에서 설명한 것 처럼 `AFX_EXT_CLASS` 는 이러한 방식으로 이미 정의 되어 있습니다. `AFX_DATA`클래스 정의와 동일 하 게 다시 정의 하기만 하면 `AFX_EXT_CLASS` 됩니다.

다음은 그 예입니다. 

```cpp
#undef  AFX_DATA
#define AFX_DATA AFX_EXT_CLASS
class CExampleView : public CView
{
    DECLARE_DYNAMIC()
    // ... class definition ...
};
#undef  AFX_DATA
#define AFX_DATA
```

MFC는 항상 `AFX_DATA` 해당 매크로 내에서 정의 하는 데이터 항목에 대해 기호를 사용 하므로이 기술은 이러한 모든 시나리오에 적용 됩니다. 예를 들어 DECLARE_MESSAGE_MAP에 대해 작동 합니다.

> [!NOTE]
> 클래스의 일부 멤버가 아니라 전체 클래스를 내보내는 경우 정적 데이터 멤버가 자동으로 내보내집니다.

동일한 기술을 사용 하 여 `CArchive` DECLARE_SERIAL 및 IMPLEMENT_SERIAL 매크로를 사용 하는 클래스에 대 한 추출 연산자를 자동으로 내보낼 수 있습니다. 다음 코드를 사용 하 여 클래스 선언 (헤더 파일에 있음)을 bracketing 하 여 archive 연산자를 내보냅니다.

```cpp
#undef AFX_API
#define AFX_API AFX_EXT_CLASS

/* your class declarations here */

#undef AFX_API
#define AFX_API
```

### <a name="limitations-of-_afxext"></a>_AFXEXT의 제한 사항

Mfc 확장 `_AFXEXT` dll의 여러 계층이 없는 경우 mfc 확장 dll에 대해 전처리기 기호를 사용할 수 있습니다. MFC 클래스에서 파생되는 고유한 MFC 확장 DLL의 클래스를 호출하거나 해당 클래스에서 파생되는 MFC 확장 DLL이 있는 경우 모호성을 방지하기 위해 고유한 전처리기 기호를 사용해야 합니다.

문제는 Win32에서 데이터를 `__declspec(dllexport)` dll에서 내보내고 dll에서 가져오는 경우 데이터를 명시적으로 선언 해야 한다는 것입니다 `__declspec(dllimport)` . 를 정의할 때 `_AFXEXT` MFC 헤더는 `AFX_EXT_CLASS` 가 올바르게 정의 되었는지 확인 합니다.

여러 계층이 있는 경우와 같은 한 가지 기호가 `AFX_EXT_CLASS` 충분 하지 않습니다. mfc 확장 dll에서 자체 클래스를 내보내고 다른 mfc 확장 dll에서 다른 클래스를 가져올 수도 있습니다. 이 문제를 해결 하려면 DLL을 사용 하는 대신 DLL 자체를 작성 하 고 있음을 나타내는 특수 전처리기 기호를 사용 합니다. 예를 들어, 및 이라는 두 개의 MFC 확장 Dll이 있다고 가정 *`A.DLL`* *`B.DLL`* 합니다. 각각 및의 일부 클래스를 *`A.H`* 내보냅니다 *`B.H`* . *`B.DLL`* 는의 클래스를 사용 *`A.DLL`* 합니다. 헤더 파일은 다음과 같습니다.

```cpp
/* A.H */
#ifdef A_IMPL
    #define CLASS_DECL_A   __declspec(dllexport)
#else
    #define CLASS_DECL_A   __declspec(dllimport)
#endif

class CLASS_DECL_A CExampleA : public CObject
{ /* ... class definition ... */ };

/* B.H */
#ifdef B_IMPL
    #define CLASS_DECL_B   __declspec(dllexport)
#else
    #define CLASS_DECL_B   __declspec(dllimport)
#endif

class CLASS_DECL_B CExampleB : public CExampleA
{ /* ... class definition ... */ };
```

가 빌드될 때가 빌드되고를 빌드할 *`A.DLL`* 때를 사용 하 여 빌드됩니다 **`/DA_IMPL`** *`B.DLL`* **`/DB_IMPL`** . 각 DLL에 대해 별도의 기호를 사용 하 여를 `CExampleB` 내보내면 `CExampleA` 빌드할 때이를 가져오게 됩니다 *`B.DLL`* . `CExampleA`*`A.DLL`* 또는 다른 클라이언트에서 사용 하는 경우 빌드하고 가져올 때를 내보냅니다 *`B.DLL`* .

기본 제공 `AFX_EXT_CLASS` 및 전처리기 기호를 사용 하는 경우이 유형의 계층화를 수행할 수 없습니다 `_AFXEXT` . 위에서 설명한 기법은 MFC와 동일한 방식으로이 문제를 해결 합니다. MFC는 OLE, 데이터베이스 및 네트워크 MFC 확장명 Dll을 빌드할 때이 기법을 사용 합니다.

### <a name="not-exporting-the-entire-class"></a>전체 클래스를 내보내지 않음

전체 클래스를 내보내지 않는 경우에는 특별히 주의 해야 합니다. MFC 매크로를 통해 만든 필수 데이터 항목을 올바르게 내보낼지 확인 합니다. 특정 클래스의 매크로를 재정의 하 여이 작업을 수행할 수 있습니다 `AFX_DATA` . 전체 클래스를 내보내지 않을 때마다 재정의 합니다.

다음은 그 예입니다. 

```cpp
// A.H
#ifdef A_IMPL
    #define CLASS_DECL_A  _declspec(dllexport)
#else
    #define CLASS_DECL_A  _declspec(dllimport)
#endif

#undef  AFX_DATA
#define AFX_DATA CLASS_DECL_A

class CExampleA : public CObject
{
    DECLARE_DYNAMIC()
    CLASS_DECL_A int SomeFunction();
    // class definition
    // ...
};

#undef AFX_DATA
#define AFX_DATA
```

### <a name="dllmain"></a>DllMain

MFC 확장 DLL에 대 한 기본 소스 파일에 저장 해야 하는 코드는 다음과 같습니다. 이는 표준 포함 뒤에와 야 합니다. 응용 프로그램 마법사를 사용 하 여 MFC 확장명 DLL에 대 한 시작 파일을 만드는 경우에는를 제공 `DllMain` 합니다.

```cpp
#include "afxdllx.h"

static AFX_EXTENSION_MODULE extensionDLL;

extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID)
{
   if (dwReason == DLL_PROCESS_ATTACH)
   {
      // MFC extension DLL one-time initialization
      if (!AfxInitExtensionModule(
             extensionDLL, hInstance))
         return 0;

      // TODO: perform other initialization tasks here
   }
   else if (dwReason == DLL_PROCESS_DETACH)
   {
      // MFC extension DLL per-process termination
      AfxTermExtensionModule(extensionDLL);

      // TODO: perform other cleanup tasks here
   }
   return 1;   // ok
}
```

에 대 `AfxInitExtensionModule` 한 호출은 나중에 개체를 만들 때 사용할 모듈의 런타임 클래스 ( `CRuntimeClass` 구조체)와 해당 개체 팩터리 (개체)를 캡처합니다 `COleObjectFactory` `CDynLinkLibrary` . (선택 사항)에 대 한 호출을 통해 mfc는 `AfxTermExtensionModule` 각 프로세스가 분리 될 때 (프로세스가 종료 될 때 또는 DLL이 호출에 의해 언로드된 경우에 발생 `FreeLibrary` ) MFC 확장명 dll에서 MFC 확장명 dll을 정리할 수 있습니다. 대부분의 MFC 확장 Dll은 동적으로 로드 되지 않으므로 (일반적으로 해당 가져오기 라이브러리를 통해 연결 됨)에 대 한 호출이 `AfxTermExtensionModule` 일반적으로 필요 하지 않습니다.

응용 프로그램이 MFC 확장명 Dll을 동적으로 로드 하 고 해제 하는 경우 `AfxTermExtensionModule` 위에 표시 된 대로를 호출 해야 합니다. 또한 `AfxLoadLibrary` `AfxFreeLibrary` `LoadLibrary` `FreeLibrary` 응용 프로그램에서 여러 스레드를 사용 하거나 MFC 확장명 DLL을 동적으로 로드 하는 경우 및 (Win32 함수 대신)를 사용 해야 합니다. `AfxLoadLibrary`및를 사용 하면 `AfxFreeLibrary` MFC 확장 DLL을 로드 하 고 언로드할 때 실행 되는 시작 및 종료 코드가 전역 mfc 상태를 손상 하지 않습니다.

헤더 파일에 *`AFXDLLX.H`* 는 및에 대 한 정의와 같은 MFC 확장명 dll에서 사용 되는 구조에 대 한 특수 정의가 포함 되어 있습니다 `AFX_EXTENSION_MODULE` `CDynLinkLibrary` .

전역 *Extensiondll* 은 표시 된 대로 선언 해야 합니다. 16 비트 버전의 MFC와 달리이 시간 동안 메모리를 할당 하 고 MFC 함수를 호출할 수 있습니다 .는 *`MFCxx.DLL`* 가 호출 된 시간에 의해 완전히 초기화 되기 때문입니다 `DllMain` .

### <a name="sharing-resources-and-classes"></a>리소스 및 클래스 공유

간단한 MFC 확장 Dll은 클라이언트 응용 프로그램에 대 한 저대역폭 함수를 몇 개만 내보내야 하며 더 이상 필요 하지 않습니다. 더 많은 사용자 인터페이스를 많이 사용 하는 Dll은 리소스 및 c + + 클래스를 클라이언트 응용 프로그램으로 내보낼 수 있습니다.

리소스 내보내기는 리소스 목록을 통해 수행됩니다. 각 응용 프로그램은 개체의 단일 연결 목록입니다 `CDynLinkLibrary` . 리소스를 찾을 때 리소스를 로드 하는 대부분의 표준 MFC 구현은 먼저 현재 리소스 모듈 ()에서 확인 `AfxGetResourceHandle` 하 고, 찾을 수 없는 경우 요청 된 리소스를 로드 하려고 시도 하는 개체 목록을 탐색 합니다 `CDynLinkLibrary` .

C + + 클래스 이름이 지정 된 경우에는 c + + 개체를 동적으로 만들 수 있습니다. MFC 개체 deserialization 메커니즘은 `CRuntimeClass` 이전에 저장 된 항목을 기반으로 필요한 형식의 c + + 개체를 동적으로 만들어 다시 생성할 수 있도록 모든 개체를 등록 해야 합니다.

클라이언트 응용 프로그램에서 MFC 확장명 DLL의 클래스를 사용 하도록 하려면 `DECLARE_SERIAL` 클래스를 내보내 클라이언트 응용 프로그램에 표시 해야 합니다. 또한 목록을 탐색 하 여 수행 `CDynLinkLibrary` 합니다.

MFC 고급 개념 샘플에서 [`DLLHUSK`](../overview/visual-cpp-samples.md) 목록은 다음과 같습니다.

```Example
head ->   DLLHUSK.EXE   - or - DLLHUSK.EXE
               |                    |
          TESTDLL2.DLL         TESTDLL2.DLL
               |                    |
          TESTDLL1.DLL         TESTDLL1.DLL
               |                    |
               |                    |
           MFC90D.DLL           MFC90.DLL
```

*`MFCxx.DLL`* 항목은 일반적으로 리소스 및 클래스 목록에 마지막으로 제공 됩니다. *`MFCxx.DLL`* 모든 표준 명령 Id에 대 한 프롬프트 문자열을 포함 하 여 모든 표준 MFC 리소스를 포함 합니다. 이를 목록의 끝에 배치 하면 Dll과 클라이언트 응용 프로그램 자체에서 자체 복사본을 사용 하는 대신의 공유 리소스를 사용할 수 있습니다 *`MFCxx.DLL`* .

모든 Dll의 리소스 및 클래스 이름을 클라이언트 응용 프로그램의 이름 공간에 병합 하는 경우 선택 하는 Id 또는 이름을 신중 하 게 선택 해야 한다는 단점이 있습니다. 리소스 또는 `CDynLinkLibrary` 개체를 클라이언트 응용 프로그램으로 내보내지 않고이 기능을 사용 하지 않도록 설정할 수 있습니다. 이 [`DLLHUSK`](../overview/visual-cpp-samples.md) 샘플에서는 여러 헤더 파일을 사용 하 여 공유 리소스 이름 공간을 관리 합니다. 공유 리소스 파일 사용에 대 한 자세한 팁은 [Technical Note 35](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md) 을 참조 하세요.

### <a name="initializing-the-dll"></a>DLL 초기화

위에서 설명한 것 처럼 일반적으로 `CDynLinkLibrary` 리소스와 클래스를 클라이언트 응용 프로그램으로 내보내는 개체를 만들려고 합니다. DLL을 초기화 하려면 내보낸 진입점을 제공 해야 합니다. 최소한 `void` 인수를 사용 하지 않고 아무 것도 반환 하지 않는 루틴 이지만 원하는 모든 것이 될 수 있습니다.

이 방법을 사용 하는 경우 DLL을 사용 하려는 각 클라이언트 응용 프로그램에서이 초기화 루틴을 호출 해야 합니다. 를 `CDynLinkLibrary` 호출한 직후에이 개체를 할당할 수도 있습니다 `DllMain` `AfxInitExtensionModule` .

초기화 루틴은 `CDynLinkLibrary` MFC 확장명 DLL 정보에 연결 된 현재 응용 프로그램 힙에서 개체를 만들어야 합니다. 다음과 같은 함수를 정의 하 여이 작업을 수행할 수 있습니다.

```cpp
extern "C" extern void WINAPI InitXxxDLL()
{
    new CDynLinkLibrary(extensionDLL);
}
```

이 예제에서 *InitXxxDLL* 루틴 이름은 원하는 모든 이름일 수 있습니다. 이렇게 할 필요 **`extern "C"`** 는 없지만 내보내기 목록을 더 쉽게 유지 관리할 수 있습니다.

> [!NOTE]
> 일반 MFC DLL에서 MFC 확장명 DLL을 사용 하는 경우이 초기화 함수를 내보내야 합니다. MFC 확장 DLL 클래스 또는 리소스를 사용 하기 전에 일반 MFC DLL에서이 함수를 호출 해야 합니다.

### <a name="exporting-entries"></a>항목 내보내기

클래스를 내보내는 간단한 방법은 `__declspec(dllimport)` `__declspec(dllexport)` 내보내고 싶은 각 클래스 및 전역 함수에서 및를 사용 하는 것입니다. 이는 훨씬 간단 하지만 아래에 설명 된 대로 DEF 파일에서 각 진입점의 이름을 지정 하는 것 보다 효율성이 낮습니다. 내보내는 함수를 더 잘 제어할 수 없기 때문입니다. 그리고 함수를 서 수로 내보낼 수 없습니다. TESTDLL1 및 TESTDLL2이 메서드를 사용 하 여 해당 항목을 내보냅니다.

보다 효율적인 방법은 .DEF 파일에서 각 항목의 이름을 지정 하 여 내보내는 것입니다. 이 메서드는에서 사용 됩니다 *`MFCxx.DLL`* . DLL에서 선택적으로 내보내기 때문에 내보내려는 특정 인터페이스를 결정 해야 합니다. .DEF 파일의 항목 형식으로 링커에 대 한 이름을 지정 해야 하므로이는 어렵습니다. C + + 클래스에 대 한 바로 가기 링크를 반드시 포함 해야 하는 경우를 제외 하 고는 내보내지 마세요.

이전에 DEF 파일을 사용 하 여 c + + 클래스 내보내기를 시도한 경우이 목록을 자동으로 생성 하는 도구를 개발할 수 있습니다. 2 단계 링크 프로세스를 사용 하 여이 작업을 수행할 수 있습니다. 내보내기를 사용 하지 않고 DLL을 한 번 연결 하 고 링커가 맵 파일을 생성 하도록 허용 합니다. 맵 파일에는 내보내려는 함수의 목록이 포함 되어 있습니다. 다시 정렬 하는 경우이를 사용 하 여 DEF 파일의 내보내기 항목을 생성할 수 있습니다. *`MFCxx.DLL`* 및 OLE 및 DATABASE MFC 확장 dll의 내보내기 목록 (수천 개)이 이러한 프로세스를 사용 하 여 생성 되었습니다 (완전히 자동이 지 않으며 한 번에 한 번만 조정 해야 함).

### <a name="cwinapp-vs-cdynlinklibrary"></a>CWinApp 및 그렇지 않으면 cdynlinklibrary

MFC 확장 DLL에는 `CWinApp` 자체의 파생 개체가 없습니다. 대신 `CWinApp` 클라이언트 응용 프로그램의 파생 개체에서 작동 해야 합니다. 클라이언트 응용 프로그램이 주 메시지 펌프, 유휴 루프 등을 소유 하 고 있음을 의미 합니다.

MFC 확장 DLL이 각 응용 프로그램에 대 한 추가 데이터를 유지 해야 하는 경우에서 새 클래스를 파생 하 `CDynLinkLibrary` 고 `InitXxxDLL` 위의 루틴 설명에 만들 수 있습니다. DLL은 실행 하는 동안 현재 응용 프로그램의 개체 목록을 검사 `CDynLinkLibrary` 하 여 특정 MFC 확장명 DLL에 대 한 개체를 찾을 수 있습니다.

### <a name="using-resources-in-your-dll-implementation"></a>DLL 구현에서 리소스 사용

위에서 설명한 것 처럼 기본 리소스 로드는 `CDynLinkLibrary` 요청 된 리소스를 포함 하는 첫 번째 EXE 또는 DLL을 찾는 개체 목록을 살펴봅니다. 모든 MFC Api 및 모든 내부 코드는를 사용 하 여 리소스 `AfxFindResourceHandle` 목록을 탐색 하 여 어디에 있든 관계 없이 리소스를 찾습니다.

특정 위치 에서만 리소스를 로드 하려는 경우에는 Api를 사용 하 여 `AfxGetResourceHandle` `AfxSetResourceHandle` 이전 핸들을 저장 하 고 새 핸들을 설정 합니다. 클라이언트 애플리케이션으로 돌아가기 전에 이전 리소스 핸들을 복원해야 합니다. 샘플 TESTDLL2는이 방법을 사용 하 여 명시적으로 메뉴를 로드 합니다.

이 목록에는 몇 가지 단점이 있습니다 .이는 약간 느리고 리소스 ID 범위를 관리 해야 합니다. 여러 MFC 확장 DLL에 연결하는 클라이언트 애플리케이션이 DLL 인스턴스 핸들을 지정하지 않고도 모든 DLL 제공 리소스를 사용할 수 있다는 장점도 있습니다. `AfxFindResourceHandle`은 리소스 목록을 검색하여 지정된 일치 항목을 찾는 데 사용되는 API입니다. 리소스의 이름 및 형식을 사용 하 여 먼저 리소스를 찾는 리소스 핸들이 나 NULL을 반환 합니다.

## <a name="writing-an-application-that-uses-the-dll-version"></a><a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a> DLL 버전을 사용 하는 응용 프로그램 작성

### <a name="application-requirements"></a>응용 프로그램 요구 사항

공유 버전의 MFC를 사용 하는 응용 프로그램은 몇 가지 기본 규칙을 따라야 합니다.

- 개체를 포함 하 `CWinApp` 고 메시지 펌프에 대 한 표준 규칙을 따라야 합니다.

- 필요한 컴파일러 플래그 집합을 사용 하 여 컴파일해야 합니다 (아래 참조).

- Mfcxx.dll 가져오기 라이브러리와 연결 해야 합니다. MFC 헤더는 필요한 컴파일러 플래그를 설정 하 여 응용 프로그램을 연결 해야 하는 라이브러리를 링크 타임에 결정 합니다.

- 실행 파일을 실행 하려면이 *`MFCxx.DLL`* 경로 또는 Windows 시스템 디렉터리에 있어야 합니다.

### <a name="building-with-the-development-environment"></a>개발 환경으로 빌드

대부분의 표준 기본값을 사용 하 여 내부 메이크파일을 사용 하는 경우 프로젝트를 쉽게 변경 하 여 DLL 버전을 빌드할 수 있습니다.

다음 단계에서는 *`NAFXCWD.LIB`* (디버그의 경우) 및 (릴리스)로 연결 된 mfc 응용 프로그램이 올바르게 작동 하 *`NAFXCW.LIB`* 고 있고이를 변환 하 여 mfc 라이브러리의 공유 버전을 사용 하도록 하는 것으로 가정 합니다. Visual Studio 환경을 실행 하 고 있고 내부 프로젝트 파일이 있습니다.

1. **프로젝트** 메뉴에서 **속성** 을 선택 합니다. **프로젝트 기본값** 의 **일반** 페이지에서 공유 DLL (mfcxx.dll (d) .dll) **의 MFC를 사용** 하도록 Microsoft Foundation Classes를 설정 합니다.

### <a name="building-with-nmake"></a>NMAKE를 사용 하 여 빌드

컴파일러의 외부 메이크파일 기능을 사용 하 고 있거나 NMAKE를 직접 사용 하는 경우 필수 컴파일러 및 링커 옵션을 지원 하도록 메이크파일을 편집 해야 합니다.

필요한 컴파일러 플래그:

- **`/D_AFXDLL /MD`**
  **`/D_AFXDLL`**

표준 MFC 헤더에는 기호를 정의 해야 합니다 `_AFXDLL` .

- **`/MD`** 응용 프로그램은 C 런타임 라이브러리의 DLL 버전을 사용 해야 합니다.

다른 모든 컴파일러 플래그는 MFC 기본값 (예: `_DEBUG` 디버그)을 따릅니다.

라이브러리의 링커 목록을 편집 합니다. *`NAFXCWD.LIB`* 을로 변경 하 *`MFCxxD.LIB`* 고 *`NAFXCW.LIB`* 을로 변경 *`MFCxx.LIB`* 합니다. *`LIBC.LIB`* 을로 바꿉니다 *`MSVCRT.LIB`* . 다른 MFC 라이브러리와 마찬가지로 *`MFCxxD.LIB`* 모든 C 런타임 라이브러리 **앞** 에 배치 하는 것이 중요 합니다.

선택적으로 **`/D_AFXDLL`** 릴리스 및 디버그 리소스 컴파일러 옵션 (실제로 리소스를 컴파일하는 옵션)에 추가 **`/R`** 합니다. 이 옵션을 사용 하면 MFC Dll에 있는 리소스를 공유 하 여 최종 실행 파일의 크기를 줄일 수 있습니다.

이러한 변경을 수행한 후에는 전체 다시 작성이 필요 합니다.

### <a name="building-the-samples"></a>예제 빌드

대부분의 MFC 샘플 프로그램은 명령줄에서 Visual C++ 또는 공유 NMAKE 호환 메이크파일의에서 빌드할 수 있습니다.

이러한 샘플 중 하나를 사용 하도록 변환 하려면 *`MFCxx.DLL`* MAK 파일을 Visual C++에 로드 하 고 위에서 설명한 대로 프로젝트 옵션을 설정할 수 있습니다. NMAKE 빌드를 사용 하는 경우 `AFXDLL=1` nmake 명령줄에을 지정 하 고 공유 MFC 라이브러리를 사용 하 여 샘플을 빌드할 수 있습니다.

MFC 고급 개념 샘플 [DLLHUSK](../overview/visual-cpp-samples.md) 는 MFC의 DLL 버전을 사용 하 여 빌드됩니다. 이 샘플에서는로 연결 된 응용 프로그램을 빌드하는 방법을 보여 *`MFCxx.DLL`* 주지만이 기술 정보 뒷부분에서 설명 하는 mfc 확장명 dll과 같은 MFC DLL 패키징 옵션의 다른 기능도 설명 합니다.

### <a name="packaging-notes"></a>패키징 정보

Dll (및)의 릴리스 버전 *`MFCxx.DLL`* 은 *`MFCxxU.DLL`* 자유롭게 재배포할 수 있습니다. Dll의 디버그 버전은 자유롭게 재배포할 수 없으며 응용 프로그램을 개발 하는 동안에만 사용 해야 합니다.

디버그 Dll은 디버깅 정보와 함께 제공 됩니다. Visual C++ 디버거를 사용 하 여 응용 프로그램과 DLL의 실행을 추적할 수 있습니다. 릴리스 Dll ( *`MFCxx.DLL`* 및 *`MFCxxU.DLL`* )에 디버깅 정보가 포함 되어 있지 않습니다.

Dll을 사용자 지정 하거나 다시 작성 하는 경우 "Mfcxx.dll" 이외의 항목을 호출 해야 합니다. MFC SRC 파일은 *`MFCDLL.MAK`* 빌드 옵션을 설명 하 고 DLL의 이름을 바꾸기 위한 논리를 포함 합니다. 이러한 Dll은 여러 MFC 응용 프로그램에서 공유할 수 있으므로 파일의 이름을 변경 해야 합니다. 사용자 지정 버전의 MFC Dll이 시스템에 설치 된 버전을 바꾸면 공유 MFC Dll을 사용 하 여 다른 MFC 응용 프로그램이 손상 될 수 있습니다.

MFC Dll을 다시 빌드하는 것은 권장 되지 않습니다.

## <a name="how-the-mfcxxdll-is-implemented"></a><a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a> MFCxx.DLL 구현 방법

다음 섹션에서는 MFC DLL ( *`MFCxx.DLL`* 및 *`MFCxxD.DLL`* )이 구현 되는 방법에 대해 설명 합니다. 여기서 설명 하는 세부 정보는 응용 프로그램에서 MFC DLL을 사용 하는 경우에도 중요 하지 않습니다. 여기에 나와 있는 세부 정보는 MFC 확장명 DLL을 작성 하는 방법을 이해 하는 데 반드시 필요 하지는 않지만이 구현을 이해 하면 사용자 고유의 DLL을 작성 하는 데 도움이 될 수

### <a name="implementation-overview"></a>구현 개요

MFC DLL은 위에서 설명한 대로 MFC 확장명 DLL의 특별 한 경우입니다. 많은 수의 클래스에 대해 많은 내보내기를 포함 합니다. MFC DLL에서 몇 가지 추가 작업을 수행 하 여 일반 MFC 확장명 DLL 보다 훨씬 더 특수 하 게 만들 수 있습니다.

### <a name="win32-does-most-of-the-work"></a>Win32는 대부분의 작업을 수행 합니다.

16 비트 버전의 MFC에는 스택 세그먼트에 앱 별 데이터, 일부 80x86 어셈블리 코드에서 만든 특수 세그먼트, 프로세스별 예외 컨텍스트 및 기타 기법을 비롯 한 다양 한 특수 기술이 필요 합니다. Win32는 DLL에서 프로세스별 데이터를 직접 지원 합니다 .이는 대부분의 시간을 원하는 것입니다. 대부분의 경우에는 *`MFCxx.DLL`* DLL로만 *`NAFXCW.LIB`* 패키지 됩니다. MFC 소스 코드를 살펴보면 몇 가지 특수 한 사례가 발생 하지 않기 때문에 몇 가지 사례를 찾을 수 있습니다 `#ifdef _AFXDLL` . 특별 한 경우는 Windows 3.1 (Win32s 라고도 함)에서 Win32를 처리 하는 것입니다. Win32s는 프로세스별 DLL 데이터를 직접 지원 하지 않습니다. MFC DLL은 TLS (스레드 로컬 저장소) Win32 Api를 사용 하 여 프로세스 로컬 데이터를 가져와야 합니다.

### <a name="impact-on-library-sources-additional-files"></a>라이브러리 소스에 미치는 영향, 추가 파일

`_AFXDLL`일반 MFC 클래스 라이브러리 소스 및 헤더에 대 한 버전의 영향은 비교적 적습니다. 특수 버전 파일 ( *`AFXV_DLL.H`* )과 주 헤더에 포함 된 추가 헤더 파일 ()이 있습니다 *`AFXDLL_.H`* *`AFXWIN.H`* . 헤더에는 *`AFXDLL_.H`* `CDynLinkLibrary` `_AFXDLL` 응용 프로그램과 MFC 확장 dll의 클래스 및 기타 구현 정보가 포함 되어 있습니다. *`AFXDLLX.H`* MFC 확장 dll을 빌드하기 위한 헤더가 제공 됩니다 (자세한 내용은 위 참조).

MFC SRC의 MFC 라이브러리에 대 한 일반 소스에는 #ifdef 아래에 몇 가지 추가 조건부 코드가 있습니다 `_AFXDLL` . 추가 소스 파일 ()에는 *`DLLINIT.CPP`* MFC의 공유 버전에 대 한 추가 DLL 초기화 코드 및 기타 붙이기가 포함 되어 있습니다.

공유 버전의 MFC를 빌드하기 위해 추가 파일이 제공 됩니다. DLL을 빌드하는 방법에 대 한 자세한 내용은 아래를 참조 하십시오.

- *`MFCxxD.DEF`* DLL의 디버그 () 및 릴리스 () 버전에 대 한 MFC DLL 진입점을 내보내는 데 두 개의 DEF 파일이 사용 됩니다 *`MFCxx.DEF`* .

- RC 파일 ()에는 *`MFCDLL.RC`* 모든 표준 MFC 리소스 및 `VERSIONINFO` DLL에 대 한 리소스가 포함 되어 있습니다.

- *`MFCDLL.CLW`* 클래스 마법사를 사용 하 여 MFC 클래스를 탐색할 수 있도록 CLW 파일 ()이 제공 됩니다. 이 기능은 MFC의 DLL 버전에는 해당 되지 않습니다.

### <a name="memory-management"></a>메모리 관리

를 사용 하는 응용 프로그램은 *`MFCxx.DLL`* 공유 C 런타임 DLL에서 제공 하는 공통 메모리 할당자를 사용 *`MSVCRTxx.DLL`* 합니다. 응용 프로그램, MFC 확장명 Dll 및 MFC Dll은이 공유 메모리 할당자를 사용 합니다. MFC Dll은 메모리 할당을 위해 공유 DLL을 사용 하 여 나중에 응용 프로그램에서 해제 하거나 그 반대로 메모리를 할당할 수 있습니다. 응용 프로그램과 DLL은 모두 동일한 할당자를 사용 해야 하므로 c + + 전역 또는를 재정의 하면 **`operator new`** 안 **`operator delete`** 됩니다. C 런타임 메모리 할당 루틴 (예:,, 및 기타)의 나머지 부분에도 동일한 규칙이 적용 `malloc` `realloc` `free` 됩니다.

### <a name="ordinals-and-class-__declspecdllexport-and-dll-naming"></a>서 수가 며 클래스 __declspec (dllexport) 및 DLL 이름 지정

`class` **`__declspec(dllexport)`** C + + 컴파일러의 기능은 사용 하지 않습니다. 대신, 내보내기 목록이 클래스 라이브러리 원본 (및)에 포함 됩니다 *`MFCxx.DEF`* *`MFCxxD.DEF`* . 진입점 (함수 및 데이터)의 선택 집합만 내보내집니다. 다른 기호 (예: MFC private 구현 함수 또는 클래스)는 내보내지 않습니다. 모든 내보내기는 상주 하거나 상주 하지 않는 이름 테이블에 문자열 이름이 없는 서 수로 수행 됩니다.

를 사용 하는 것은 `class` **`__declspec(dllexport)`** 작은 dll을 빌드하는 데 사용할 수 있는 대안이 될 수 있지만 MFC와 같은 대용량 dll에서는 기본 내보내기 메커니즘의 효율성과 용량 제한이 있습니다.

모든 것이 무엇을 의미 하는 것은 *`MFCxx.DLL`* 대부분의 실행 이나 로드 속도를 손상 시 키 지 않으면 서 800 KB에 불과합니다. *`MFCxx.DLL`* 100 KB가 더 많이 사용 되지 않았습니다. 이 기법을 사용 하면 DEF 파일의 끝에 진입점을 더 추가할 수 있습니다. 이를 통해 서 수로 내보내는 속도 및 크기 효율성을 손상 시 키 지 않고 단순한 버전 관리를 수행할 수 있습니다. MFC 클래스 라이브러리의 주 버전 수정 버전은 라이브러리 이름을 변경 합니다. 즉,는 *`MFC30.DLL`* MFC 클래스 라이브러리의 버전 3.0을 포함 하는 재배포 가능 DLL입니다. 이 DLL을 업그레이드 하는 경우 (예를 들어, 가상의 MFC 3.1) DLL의 이름이 대신 지정 됩니다 *`MFC31.DLL`* . Mfc DLL의 사용자 지정 버전을 생성 하도록 MFC 소스 코드를 수정 하는 경우에는 다른 이름 (이름에 "MFC"가 없는 경우)을 사용 합니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
