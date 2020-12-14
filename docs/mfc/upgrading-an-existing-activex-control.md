---
description: '자세한 정보: 기존 ActiveX 컨트롤 업그레이드'
title: 기존 ActiveX 컨트롤 업그레이드
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX controls [MFC], Internet
- LPK files for Internet controls
- safe for scripting and initialization (controls)
- OLE controls [MFC], upgrading to ActiveX
- CAB files, for ActiveX controls
- Internet applications [MFC], ActiveX controls
- Internet applications [MFC], packaging code for download
- upgrading ActiveX controls
- licensing ActiveX controls
ms.assetid: 4d12ddfa-b491-4f9f-a0b7-b51458e05651
ms.openlocfilehash: aeff78eca2c88bea9bcceb7ac6f79e907c141350
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263688"
---
# <a name="upgrading-an-existing-activex-control"></a>기존 ActiveX 컨트롤 업그레이드

기존 ActiveX 컨트롤 (이전의 OLE 컨트롤)은 수정 없이 인터넷에서 사용할 수 있습니다. 그러나 컨트롤을 수정 하 여 성능을 향상 시킬 수 있습니다.

> [!IMPORTANT]
> ActiveX는 새로운 개발에 사용 하지 않아야 하는 레거시 기술입니다. ActiveX를 대체 하는 최신 기술에 대 한 자세한 내용은 [Activex Controls](activex-controls.md)을 참조 하세요.

웹 페이지에서 컨트롤을 사용 하는 경우 추가로 고려해 야 할 사항이 있습니다. .Ocx 파일 및 모든 지원 파일은 대상 컴퓨터에 있거나 인터넷을 통해 다운로드 해야 합니다. 이렇게 하면 코드 크기와 다운로드 시간을 중요 하 게 고려해 야 합니다. 다운로드는 서명 된 .cab 파일에 패키지할 수 있습니다. 컨트롤을 스크립팅에 안전한 것으로 표시 하 고 초기화 하는 것이 안전 합니다.

이 문서에서는 다음 토픽을 설명합니다.

- [다운로드를 위한 코드 패키징](#_core_packaging_code_for_downloading)

- [스크립팅 및 초기화를 위한 컨트롤 안전 표시](#_core_marking_a_control_safe_for_scripting_and_initializing)

- [라이선스 문제](#_core_licensing_issues)

- [서명 코드](#_core_signing_code)

- [색상표 관리](#_core_managing_the_palette)

- [Internet Explorer 브라우저 보안 수준 및 제어 동작](#_core_internet_explorer_browser_safety_levels_and_control_behavior)

[ActiveX 컨트롤: 최적화](../mfc/mfc-activex-controls-optimization.md)에 설명 된 대로 최적화를 추가할 수도 있습니다. [인터넷의 ActiveX 컨트롤](../mfc/activex-controls-on-the-internet.md)에 설명 된 대로 모니커를 사용 하 여 속성 및 대량 blob을 비동기식으로 다운로드할 수 있습니다.

## <a name="packaging-code-for-downloading"></a><a name="_core_packaging_code_for_downloading"></a> 다운로드를 위한 코드 패키징

이 주제에 대 한 자세한 내용은 [ActiveX 컨트롤 패키징](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa751974%28v%3dvs.85%29)을 참조 하세요.

### <a name="the-codebase-tag"></a>CODEBASE 태그

ActiveX 컨트롤은 태그를 사용 하 여 웹 페이지에 포함 됩니다 `<OBJECT>` . `CODEBASE`태그의 매개 변수는 `<OBJECT>` 컨트롤을 다운로드할 위치를 지정 합니다. `CODEBASE` 는 여러 다른 파일 형식을 가리킬 수 있습니다.

### <a name="using-the-codebase-tag-with-an-ocx-file"></a>OCX 파일에 CODEBASE 태그 사용

```
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,
    70,
    0,
    1086"
```

이 솔루션은 컨트롤의 .ocx 파일만 다운로드 하며 클라이언트 컴퓨터에 이미 설치 되어 있는 지원 Dll이 있어야 합니다. Internet Explorer는 Visual C++ 컨트롤용 지원 Dll과 함께 제공 되므로 Visual C++로 빌드된 Internet Explorer 및 MFC ActiveX 컨트롤에 대해 작동 합니다. ActiveX 컨트롤을 사용할 수 있는 다른 인터넷 브라우저를 사용 하 여이 컨트롤을 볼 수 있는 경우이 솔루션은 작동 하지 않습니다.

### <a name="using-the-codebase-tag-with-an-inf-file"></a>INF 파일과 함께 CODEBASE 태그 사용

```
CODEBASE="http://example.microsoft.com/trustme.inf"
```

.Inf 파일은 .ocx 및 해당 지원 파일의 설치를 제어 합니다. 이 메서드는 .inf 파일에 서명할 수 없으므로 권장 되지 않습니다 (코드 서명에 대 한 포인터에 대 한 [코드 서명](#_core_signing_code) 참조).

### <a name="using-the-codebase-tag-with-a-cab-file"></a>CAB 파일과 함께 CODEBASE 태그 사용

```
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,
    2,
    0,
    0"
```

캐비닛 파일은 MFC를 사용 하는 ActiveX 컨트롤을 패키지 하는 데 권장 되는 방법입니다. 캐비닛 파일에서 MFC ActiveX 컨트롤을 패키지 하면 ActiveX 컨트롤 및 모든 종속 Dll (예: MFC Dll)의 설치를 제어 하는 .inf 파일을 포함할 수 있습니다. CAB 파일을 사용 하면 다운로드 속도를 단축 하기 위해 코드가 자동으로 압축 됩니다. 구성 요소 다운로드를 위해 .cab 파일을 사용 하는 경우 각 개별 구성 요소 보다 전체 .cab 파일에 서명 하는 것이 더 빠릅니다.

### <a name="creating-cab-files"></a>CAB 파일 만들기

캐비닛 파일을 만드는 도구는 이제 [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)에 포함 되어 있습니다.

에서 가리키는 캐비닛 파일에는 `CODEBASE` ActiveX 컨트롤의 .ocx 파일 및 해당 설치를 제어 하는 .inf 파일이 포함 되어야 합니다. 컨트롤 파일의 이름과 .inf 파일을 지정 하 여 캐비닛 파일을 만듭니다. 이 캐비닛 파일의 시스템에 이미 있을 수 있는 종속 Dll은 포함 하지 마세요. 예를 들어, MFC Dll은 별도의 캐비닛 파일에 패키지 되 고 제어 .inf 파일에 의해 참조 됩니다.

CAB 파일을 만드는 방법에 대 한 자세한 내용은 [Cab 파일 만들기](/windows/win32/devnotes/cabinet-api-functions)를 참조 하세요.

### <a name="the-inf-file"></a>INF 파일

다음 예제 spindial는 MFC Spindial 컨트롤에 필요한 지원 파일 및 버전 정보를 나열 합니다. MFC Dll의 위치는 Microsoft 웹 사이트입니다. mfc42.cab은 Microsoft에서 제공 하 고 서명 합니다.

```
Contents of spindial.inf:
[mfc42installer]
file-win32-x86=http://activex.microsoft.com/controls/vc/mfc42.cab
[Olepro32.dll] - FileVersion=5,
    0,
    4261,
    0
[Mfc42.dll] - FileVersion=6,
    0,
    8168,
    0
[Msvcrt.dll] - FileVersion=6,
    0,
    8168,
    0
```

### <a name="the-object-tag"></a>\<OBJECT>태그

다음 예제에서는 태그를 사용 하 여 `<OBJECT>` MFC Spindial 샘플 컨트롤을 패키징하는 방법을 보여 줍니다.

```
<OBJECT ID="Spindial1" WIDTH=100 HEIGHT=51
    CLASSID="CLSID:06889605-B8D0-101A-91F1-00608CEAD5B3"
    CODEBASE="http://example.microsoft.com/spindial.cab#Version=1,0,0,001">
<PARAM NAME="_Version" VALUE="65536">
<PARAM NAME="_ExtentX" VALUE="2646">
<PARAM NAME="_ExtentY" VALUE="1323">
<PARAM NAME="_StockProps" VALUE="0">
<PARAM NAME="NeedlePosition" VALUE="2">
</OBJECT>
```

이 경우 spindial.cab에는 spindial 및 spindial 라는 두 개의 파일이 포함 됩니다. 다음 명령은 캐비닛 파일을 빌드합니다.

```
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf
```

`-s 6144`매개 변수는 코드 서명을 위해 캐비닛에 공간을 예약 합니다.

### <a name="the-version-tag"></a>버전 태그

여기서 `#Version` CAB 파일로 지정 된 정보는 태그의 *CLASSID* 매개 변수로 지정 된 컨트롤에 적용 됩니다 `<OBJECT>` .

지정 된 버전에 따라 컨트롤을 강제로 다운로드할 수 있습니다. `OBJECT` *CODEBASE* 매개 변수를 포함 한 태그의 전체 사양은 W3C 참조를 참조 하세요.

## <a name="marking-a-control-safe-for-scripting-and-initializing"></a><a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a> 스크립팅 및 초기화를 위한 컨트롤 안전 표시

웹 페이지에 사용 되는 ActiveX 컨트롤은 스크립트를 안전 하 게 보호 하 고 실제로 안전 하 게 초기화 하기 위해 안전 하 게 표시 되어야 합니다. 안전 컨트롤은 디스크 IO를 수행 하거나 메모리 또는 컴퓨터의 레지스터에 직접 액세스 하지 않습니다.

컨트롤은 스크립트를 안전 하 게 안전 하 게 표시 하 고 레지스트리를 통해 초기화를 안전 하 게 수행할 수 있습니다. `DllRegisterServer`다음과 유사한 항목을 추가 하 여 레지스트리의 스크립팅 및 지 속성에 대해 제어를 안전 하 게 표시 하려면를 수정 합니다. 다른 방법은을 구현 하는 것입니다 `IObjectSafety` .

컨트롤에 대 한 Guid (Globally Unique Identifier)를 정의 하 여 스크립팅과 지 속성에 안전 하 게 표시 합니다. 안전 하 게 스크립팅할 수 있는 컨트롤에는 다음과 같은 레지스트리 항목이 포함 됩니다.

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
```

영구 데이터에서 안전 하 게 초기화 될 수 있는 컨트롤은 다음과 유사한 레지스트리 항목을 사용 하 여 지 속성을 위해 안전 하 게 표시 됩니다.

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

다음과 유사한 항목을 추가 `{06889605-B8D0-101A-91F1-00608CEAD5B3}` 하 여 키를 다음 클래스 id와 연결 합니다 (대신 컨트롤의 클래스 id로 대체).

```
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

## <a name="licensing-issues"></a><a name="_core_licensing_issues"></a> 라이선스 문제

웹 페이지에서 사용이 허가 된 컨트롤을 사용 하려면 사용권 계약에 따라 인터넷에서 사용이 허용 되는지 확인 하 고이에 대 한 LPK (라이선스 패키지 파일)를 만들어야 합니다.

Internet Explorer를 실행 하는 컴퓨터에 컨트롤을 사용할 수 있는 권한이 없으면 사용이 허가 된 ActiveX 컨트롤이 HTML 페이지에 제대로 로드 되지 않습니다. 예를 들어 Visual C++를 사용 하 여 사용이 허가 된 컨트롤이 빌드된 경우 컨트롤을 사용 하는 HTML 페이지가 컨트롤이 빌드된 컴퓨터에서 제대로 로드 되지만 라이선스 정보가 포함 되지 않은 경우에는 다른 컴퓨터에 로드 되지 않습니다.

Internet Explorer에서 사용이 허가 된 ActiveX 컨트롤을 사용 하려면 공급 업체의 사용권 계약을 확인 하 여 컨트롤에 대 한 라이선스가 다음을 허용 하는지 확인 해야 합니다.

- 재배포

- 인터넷에서 컨트롤 사용

- Codebase 매개 변수 사용

사용이 허가 되지 않은 컴퓨터의 HTML 페이지에서 사용이 허가 된 컨트롤을 사용 하려면 LPK (라이선스 패키지 파일)를 생성 해야 합니다. LPK 파일은 HTML 페이지에서 사용이 허가 된 컨트롤에 대 한 런타임 라이선스를 포함 합니다. 이 파일은 ActiveX SDK와 함께 제공 되는 LPK_TOOL.EXE를 통해 생성 됩니다.

#### <a name="to-create-an-lpk-file"></a>LPK 파일을 만들려면

1. 컨트롤을 사용 하도록 허가 된 컴퓨터에서 LPK_TOOL.EXE를 실행 합니다.

1. **라이선스 패키지 제작 도구** 대화 상자의 **사용 가능한 컨트롤** 목록 상자에서 HTML 페이지에 사용할 사용이 허가 된 각 ActiveX 컨트롤을 선택 하 고 **추가** 를 클릭 합니다.

1. **저장 & 끝내기** 를 클릭 하 고 LPK 파일의 이름을 입력 합니다. 그러면 LPK 파일이 생성 되 고 응용 프로그램이 닫힙니다.

#### <a name="to-embed-a-licensed-control-on-an-html-page"></a>HTML 페이지에 사용이 허가 된 컨트롤을 포함 하려면

1. HTML 페이지를 편집 합니다. HTML 페이지에서 \<OBJECT> 다른 태그 앞에 라이선스 관리자 개체에 대 한 태그를 삽입 \<OBJECT> 합니다. 라이선스 관리자는 Internet Explorer와 함께 설치 되는 ActiveX 컨트롤입니다. 해당 클래스 ID는 다음과 같습니다. 라이선스 관리자 개체의 LPKPath 속성을 LPK 파일의 경로 및 이름으로 설정 합니다. HTML 페이지당 하나의 LPK 파일만 사용할 수 있습니다.

```
<OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">
</OBJECT>
```

1. \<OBJECT>라이선스 관리자 태그 뒤에 사용이 허가 된 컨트롤에 대 한 태그를 삽입 합니다.

   예를 들어 Microsoft 마스킹된 편집 컨트롤을 표시 하는 HTML 페이지는 다음과 같습니다. 첫 번째 클래스 ID는 라이선스 관리자 컨트롤에 대 한 것이 고, 두 번째 클래스 id는 마스킹된 편집 컨트롤에 대 한 것입니다. 이전에 만든 .lpk 파일의 상대 경로를 가리키도록 태그를 변경 하 고 컨트롤의 클래스 ID를 포함 하는 개체 태그를 추가 합니다.

1. \<EMBED>NCompass ActiveX 플러그 인을 사용 하는 경우 LPK 파일의 특성을 삽입 합니다.

   ActiveX (NCompass ActiveX 플러그 인을 사용 하는 Netscape)와 같은 다른 활성 사용 브라우저에서 컨트롤이 표시 될 수 있는 경우 아래와 같이 구문을 추가 해야 합니다 \<EMBED> .

```
<OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="maskedit.lpk">

<EMBED SRC = "maskedit.LPK">

</OBJECT>
<OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>
</OBJECT>
```

컨트롤 라이선스에 대 한 자세한 내용은 [Activex 컨트롤: Activex 컨트롤 라이선스](../mfc/mfc-activex-controls-licensing-an-activex-control.md)를 참조 하세요.

## <a name="signing-code"></a><a name="_core_signing_code"></a> 서명 코드

코드 서명은 코드의 소스를 식별 하 고 코드가 서명 된 후 변경 되지 않도록 보장 하기 위한 것입니다. 브라우저 보안 설정에 따라 코드를 다운로드 하기 전에 사용자에 게 경고가 표시 될 수 있습니다. 사용자는 특정 인증서 소유자 또는 회사를 신뢰 하도록 선택할 수 있습니다 .이 경우 신뢰할 수 있는 인증서로 서명 된 코드는 경고 없이 다운로드 됩니다. 변조를 방지 하기 위해 코드는 디지털로 서명 됩니다.

신뢰 경고 메시지를 표시 하지 않고 컨트롤을 자동으로 다운로드할 수 있도록 최종 코드가 서명 되었는지 확인 합니다. 코드에 서명 하는 방법에 대 한 자세한 내용은 ActiveX SDK에서 Authenticode에 대 한 설명서를 확인 하 고 [CAB 파일에 서명](/windows/win32/devnotes/cabinet-api-functions)을 참조 하세요.

신뢰 및 브라우저 보안 수준 설정에 따라 서명 사용자 또는 회사를 식별 하는 인증서가 표시 될 수 있습니다. 안전 수준이 none 이거나 서명 된 컨트롤의 인증서 소유자를 신뢰할 수 있는 경우 인증서가 표시 되지 않습니다. 브라우저 보안 설정에서 컨트롤이 다운로드 되 고 인증서가 표시 되는지 여부를 확인 하는 방법에 대 한 자세한 내용은 [Internet Explorer 브라우저 보안 수준 및 제어 동작](#_core_internet_explorer_browser_safety_levels_and_control_behavior) 을 참조 하십시오.

디지털 서명은 코드가 서명 된 후 변경 되지 않았음을 보장 합니다. 코드의 해시가 인증서에 포함 되 고 포함 됩니다. 이 해시는 나중에 코드를 다운로드 한 후 실행 되기 전에 수행 된 코드의 해시와 비교 됩니다. Verisign과 같은 회사는 코드에 서명 하는 데 필요한 개인 및 공개 키를 제공할 수 있습니다. ActiveX SDK는 테스트 인증서를 만들기 위한 유틸리티인 Makecert.exe와 함께 제공 됩니다.

## <a name="managing-the-palette"></a><a name="_core_managing_the_palette"></a> 색상표 관리

컨테이너는 색상표를 결정 하 고 **DISPID_AMBIENT_PALETTE** 앰비언트 속성으로 사용할 수 있도록 합니다. 컨테이너 (예: Internet Explorer)는 페이지의 모든 ActiveX 컨트롤에서 고유한 색상표를 결정 하는 데 사용 되는 색상표를 선택 합니다. 이렇게 하면 깜박임이 표시 되지 않고 일관 된 모양이 표시 됩니다.

컨트롤이를 재정의 `OnAmbientPropertyChange` 하 여 색상표의 변경 내용에 대 한 알림을 처리할 수 있습니다.

컨트롤은 색상표를 `OnGetColorSet` 그리기 위해 색 집합을 반환 하도록를 재정의할 수 있습니다. 컨테이너는 반환 값을 사용 하 여 컨트롤이 팔레트를 인식 하는지 여부를 확인 합니다.

OCX 96 지침에서 컨트롤은 항상 배경에서 색상표를 인식 해야 합니다.

앰비언트 색상표 속성을 사용 하지 않는 이전 컨테이너는 WM_QUERYNEWPALETTE 및 WM_PALETTECHANGED 메시지를 보냅니다. 컨트롤은 `OnQueryNewPalette` `OnPaletteChanged` 이러한 메시지를 재정의 하 고 처리할 수 있습니다.

## <a name="internet-explorer-browser-safety-levels-and-control-behavior"></a><a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a> Internet Explorer 브라우저 보안 수준 및 제어 동작

브라우저에는 사용자가 구성할 수 있는 안전 수준 옵션이 있습니다. 웹 페이지에는 잠재적으로 사용자 컴퓨터를 손상 시킬 수 있는 활성 콘텐츠가 포함 될 수 있기 때문에 브라우저에서 보안 수준에 대 한 옵션을 선택할 수 있습니다. 브라우저에서 보안 수준을 구현 하는 방법에 따라 컨트롤을 전혀 다운로드 하지 못할 수도 있고, 사용자가 런타임에 컨트롤을 다운로드할지 여부를 선택할 수 있도록 인증서 또는 경고 메시지를 표시 합니다. Internet Explorer에서 높음, 보통 및 낮음 보안 수준 아래의 ActiveX 컨트롤의 동작은 아래에 나열 되어 있습니다.

### <a name="high-safety-mode"></a>보안 우선 모드

- 서명 되지 않은 컨트롤은 다운로드 되지 않습니다.

- 서명 된 컨트롤에는 신뢰할 수 없는 경우 인증서가 표시 됩니다. 사용자가 현재이 인증서 소유자의 코드를 항상 신뢰 하는 옵션을 선택할 수 있습니다.

- Safe로 표시 된 컨트롤만 영구적 데이터를 포함 하거나 스크립팅할 수 있습니다.

### <a name="medium-safety-mode"></a>보통 보안 모드

- 서명 되지 않은 컨트롤을 다운로드 하기 전에 경고를 표시 합니다.

- 서명 되지 않은 경우 서명 된 컨트롤은 인증서를 표시 합니다.

- Safe로 표시 되지 않은 컨트롤은 경고를 표시 합니다.

### <a name="low-safety-mode"></a>낮은 보안 모드

- 컨트롤은 경고 없이 다운로드 됩니다.

- 스크립팅 및 지 속성은 경고 없이 발생 합니다.

## <a name="see-also"></a>참고 항목

[MFC 인터넷 프로그래밍 작업](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC 인터넷 프로그래밍 기본 사항](../mfc/mfc-internet-programming-basics.md)<br/>
[MFC ActiveX 컨트롤: ActiveX 컨트롤 라이선스](../mfc/mfc-activex-controls-licensing-an-activex-control.md)
