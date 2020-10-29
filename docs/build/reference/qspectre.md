---
title: /Qspectre
ms.date: 09/06/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.SpectreMitigation
helpviewer_keywords:
- /Qspectre
ms.openlocfilehash: a4872d18fed4523e235aee70839f1e482d78f345
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919113"
---
# <a name="qspectre"></a>/Qspectre

특정 스펙터 변형 1 보안 취약성을 완화하기 위한 컴파일러 생성 지침을 지정합니다.

## <a name="syntax"></a>구문

> **/Qspectre**

## <a name="remarks"></a>설명

**/Qspectre** 옵션은 Visual Studio 2017 버전 15.5.5 이상, 그리고 [KB 4338871](https://support.microsoft.com/help/4338871/visual-studio-2015-update-3-spectre-variant-1-toolset-qspectre)을 통해 Visual Studio 2015 Update 3에서 사용할 수 있습니다. 이 옵션을 사용하면 컴파일러가 특정 [스펙터 보안 취약성](https://spectreattack.com/spectre.pdf)을 완화하는 지침을 삽입합니다. 이러한 취약성을 *추론적 실행 측 채널 공격* 이라고 합니다. Intel, AMD 및 ARM의 프로세서를 비롯 한 많은 운영 체제 및 최신 프로세서에 영향을 줍니다.

**/Qspectre** 옵션은 기본적으로 해제되어 있습니다.

초기 릴리스에서는 **/Qspectre** 옵션이 최적화된 코드에만 작동했습니다. Visual Studio 2017 버전 15.7 이상에서는 **/Qspectre** 옵션이 모든 최적화 수준에서 지원됩니다.

Microsoft Visual C++ 라이브러리도 스펙터 완화를 사용하는 버전에서 사용할 수 있습니다. Visual Studio 2017 이상의 스펙터 완화 라이브러리는 Visual Studio 설치 관리자에서 다운로드할 수 있습니다. 이러한 **도구는 컴파일러, 빌드 도구 및 런타임** 의 **개별 구성 요소** 탭에서 찾을 수 있으며 이름에 "스펙터 용 라이브러리"가 있습니다. Vcruntime140, msvcp140, concrt140 및 vcamp140와 같은 완화 기능을 사용 하 여 DLL 및 정적 런타임 라이브러리를 모두 Visual C++ 사용할 수 있습니다. Dll은 응용 프로그램 로컬 배포에 대해서만 지원 됩니다. Visual C++ 2017 이상 런타임 라이브러리 재배포 가능 패키지의 콘텐츠가 수정 되지 않았습니다.

MFC 및 ATL에 대해 스펙터 완화 라이브러리를 설치할 수도 있습니다. 이러한 구성 요소는 **sdk, 라이브러리 및 프레임 워크** 의 **개별 구성 요소** 탭에 있습니다.

> [!NOTE]
> UWP (유니버설 Windows) 앱 또는 구성 요소에 대 한 스펙터 완화 라이브러리 버전이 없습니다. 이러한 라이브러리의 앱 로컬 배포는 가능 하지 않습니다.

### <a name="applicability"></a>적용 대상

코드가 신뢰 경계를 초과 하는 데이터에 대해 작동 하는 경우 **/Qspectre** 옵션을 사용 하 여 코드를 다시 빌드하고 다시 배포 하 여 가능한 한 빨리이 문제를 완화 하는 것이 좋습니다. 이러한 코드의 예로는 실행에 영향을 줄 수 있는 신뢰할 수 없는 입력을 로드 하는 코드가 있습니다. 예를 들어 원격 프로시저 호출을 수행 하거나, 신뢰할 수 없는 입력 또는 파일을 구문 분석 하거나, 다른 로컬 IPC (프로세스 간 통신) 인터페이스를 사용 하는 코드를 예로 들 수 있습니다. 표준 샌드박싱 기술로 충분하지 않을 수 있습니다. 코드가 신뢰 경계를 넘지 않도록 결정 하기 전에 샌드박스를 신중 하 게 조사 합니다.

### <a name="availability"></a>가용성

**/Qspectre** 옵션은 Visual Studio 2017 버전 15.5.5에서 사용할 수 있으며, MSVC (Microsoft c + + 컴파일러)에 대 한 모든 업데이트는 2018 년 1 월 23 일 이후에 수행 됩니다. Visual Studio 설치 관리자를 사용하여 컴파일러를 업데이트하고, 스펙터 완화 라이브러리를 개별 구성 요소로 설치하세요. **/Qspectre** 옵션은 패치를 통해 Visual Studio 2015 업데이트 3에서도 제공됩니다. 자세한 내용은 [KB 4338871](https://support.microsoft.com/help/4338871)을 참조하세요.

모든 버전의 Visual Studio 2017 버전 15.5 및 Visual Studio 2017 버전 15.6의 모든 미리 보기입니다. 문서화 되지 않은 옵션인 **/d2guardspecload** 를 포함 합니다. **/Qspectre** 의 초기 동작과 동일 합니다. 이러한 컴파일러 버전에서 **/d2guardspecload** 옵션을 사용하여 코드에 동일한 완화를 적용할 수 있습니다. 옵션을 지 원하는 컴파일러에서 **/Qspectre** 를 사용 하도록 빌드를 업데이트 하는 것이 좋습니다. **/Qspectre** 옵션은 이후 버전의 컴파일러에서 새로운 완화를 지원할 수도 있습니다.

### <a name="effect"></a>효과

**/Qspectre** 옵션은 스펙터 변형 1, 경계 검사 우회를 완화하는 [CVE 2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753) 코드를 출력합니다. 이 코드는 추측 코드 실행의 장벽 역할을 하는 지침을 삽입하는 방식으로 작동합니다. 프로세서 추측을 완화하기 위해 사용되는 지침은 프로세서 및 해당 마이크로 아키텍처에 따라 결정되며, 향후 컴파일러 버전에서 변경될 수 있습니다.

**/Qspectre** 옵션을 사용 하도록 설정 하면 컴파일러는 잘못 된 실행이 범위 검사를 무시할 수 있는 인스턴스를 식별 하려고 합니다. 그러면 장벽 명령이 삽입 됩니다. 컴파일러가 variant 1의 인스턴스를 식별 하기 위해 수행할 수 있는 분석에 대 한 제한 사항을 알고 있어야 합니다. 따라서 모든 가능한 variant 1 인스턴스가 **/Qspectre** 에서 계측 된다는 보장이 없습니다.

### <a name="performance-impact"></a>성능에 미치는 영향

**/Qspectre** 의 성능 영향은 몇 가지 조정 가능 코드 베이스에서 무시 되는 것으로 나타났습니다. 그러나 **/Qspectre** 아래에 있는 코드의 성능이 영향을 받지 않게 됩니다. 코드를 벤치마크하여 이 옵션이 성능에 미치는 영향을 확인해야 합니다. 성능이 중요 한 블록이 나 루프에서 완화가 필요 하지 않은 경우 [__declspec (nomitigation)](../../cpp/spectre.md) 지시어를 사용 하 여 완화를 선택적으로 사용 하지 않도록 설정할 수 있습니다. **/D2guardspecload** 옵션만 지 원하는 컴파일러에서는이 지시문을 사용할 수 없습니다.

### <a name="required-libraries"></a>필수 라이브러리

**/Qspectre** 컴파일러 옵션은 스펙터 완화를 제공 하기 위해 빌드된 런타임 라이브러리의 버전을 암시적으로 링크 하는 코드를 생성 합니다. 다음 라이브러리는 Visual Studio 설치 관리자를 사용하여 설치해야 하는 선택적 구성 요소입니다.

- \[(x86 및 x64) | (ARM) | (ARM64)]를 위한 MSVC 버전 *version_numbers* 스펙터용 라이브러리
- 스펙터 완화를 사용하는 \[(x86/x64) | ARM | ARM64]용 Visual C++ ATL
- 스펙터 완화를 사용하는 \[(x86/x64) | ARM | ARM64]용 Visual C++ MFC

**/Qspectre** 를 사용 하 여 코드를 빌드하는 경우 이러한 라이브러리가 설치 되어 있지 않으면 빌드 시스템에서 **경고 MSB8038: 스펙터 완화를 사용할 수 있지만 스펙터 완화 된 라이브러리를 찾을 수 없습니다** . MFC 또는 ATL 코드 빌드가 실패 하 고 링커가 심각한 오류 LNK1104 같은 오류를 보고 하는 경우 **: ' oldnames. n a m e '을 열 수 없습니다** . 이러한 누락 된 라이브러리는 원인일 수 있습니다.

### <a name="additional-information"></a>추가 정보

자세한 내용은 공식 [Microsoft Security ADVISE ADV180002에서 잘못 된 실행 측 채널 취약성을 완화 하기 위한 지침](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002)을 참조 하세요. 지침은 Intel의 [예측 실행 부채널 완화](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf) 및 ARM의 [캐시 예측 부채널](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf)에서도 확인할 수 있습니다. 스펙터 및 멜트다운 완화에 대 한 Windows 관련 개요는 [Windows 시스템에서 스펙터 및 멜트다운 완화의 성능 영향 이해](https://www.microsoft.com/security/blog/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/)를 참조 하세요. MSVC 완화에 의해 해결 된 스펙터 취약성의 개요는 c + + 팀 블로그에서 [MSVC의 스펙터 완화](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc./) 를 참조 하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

::: moniker range="msvc-160"

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성** > **C/c + +** > **코드 생성** 속성 페이지를 선택 합니다.

1. **스펙터 완화** 속성의 새 값을 선택 합니다. **확인** 을 선택하여 변경 내용을 적용합니다.

::: moniker-end

::: moniker range="<=msvc-150"

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성** > **C/C++** > **명령줄** 속성 페이지를 선택합니다.

1. **추가 옵션** 상자에 **/Qspectre** 컴파일러 옵션을 입력합니다. **확인** 을 선택하여 변경 내용을 적용합니다.

::: moniker-end

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/Q 옵션 (하위 수준 작업)](q-options-low-level-operations.md)<br/>
[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
