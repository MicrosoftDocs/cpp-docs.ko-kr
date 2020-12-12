---
description: '자세히 알아보기: HLSL 컴파일러 속성 페이지'
title: HLSL 속성 페이지
ms.date: 07/24/2019
ms.assetid: 0c65f5ec-a2a5-4f5b-8d4c-fa57113a5a1d
f1_keywords:
- VC.Project.FXCompilerTool.AdditionalIncludeDirectories
- VC.Project.FXCompilerTool.SuppressStartupBanner
- VC.Project.FXCompilerTool.EntryPointName
- VC.Project.FXCompilerTool.TreatWarningAsError
- VC.Project.FXCompilerTool.DisableOptimizations
- VC.Project.FXCompilerTool.EnableDebuggingInformation
- VC.Project.FXCompilerTool.ShaderType
- VC.Project.FXCompilerTool.ShaderModel
- VC.Project.FXCompilerTool.AllResourcesBound
- VC.Project.FXCompilerTool.EnableUnboundedDescriptorTables
- VC.Project.FXCompilerTool.SetRootSignature
- VC.Project.FXCompilerTool.PreprocessorDefinitions
- VC.Project.FXCompilerTool.AdditionalOptionsPage
- VC.Project.FXCompilerTool.VariableName
- VC.Project.FXCompilerTool.HeaderFileOutput
- VC.Project.FXCompilerTool.ObjectFileOutput
- VC.Project.FXCompilerTool.AssemblerOutput
- VC.Project.FXCompilerTool.AssemblerOutputFile
- VC.Project.FXCompilerTool.CompileD2DCustomEffect
- VC.Project.FXCompilerTool.MultiProcFXC
ms.openlocfilehash: 3a374c36d87429fac9d9aee8dda2d1035da247c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199964"
---
# <a name="hlsl-compiler-property-pages"></a>HLSL 컴파일러 속성 페이지

HLSL 컴파일러(fxc.exe) 속성 페이지를 사용하여 개별 HLSL 셰이더 파일을 빌드하는 방법을 구성할 수 있습니다. **명령줄** 속성 페이지의 **추가 옵션** 속성을 사용 하 여 HLSL 컴파일러에 대 한 명령줄 인수를 지정할 수도 있습니다. 여기에는 HLSL 속성 페이지의 다른 속성을 사용 하 여 구성할 수 없는 인수가 포함 됩니다. HLSL 컴파일러에 대한 자세한 내용은 [효과-컴파일러 도구](/windows/win32/direct3dtools/fxc)를 참조하세요.

## <a name="hlsl-general-property-page"></a>HLSL 일반 속성 페이지

### <a name="additional-include-directories"></a>추가 포함 디렉터리

포함 경로에 추가할 디렉터리를 하나 이상 지정합니다. 항목이 여러 개인 경우 세미콜론으로 구분합니다. (/I [path])

### <a name="entrypoint-name"></a>진입점 이름

셰이더에 대 한 진입점의 이름을 지정 합니다 (/E [name]).

### <a name="disable-optimizations"></a>최적화 사용 안 함

최적화를 사용하지 않도록 설정하려면 **예(/Od)** 이고, 사용하도록 설정하려면 **아니요** 입니다. 기본적으로 **디버그** 구성에 대한 값은 **예(/Od)** 이고 **릴리스** 구성에 대한 값은 **아니요** 입니다.

HLSL 컴파일러에 대한 **/Od** 명령줄 인수가 암시적으로 **/Gfp** 명령줄 인수에 적용되지만 출력은 **/Od** 및 **/Gfp** 명령줄 인수 둘 다 명시적으로 전달하여 생성된 출력과 동일하지 않을 수 있습니다.

### <a name="enable-debugging-information"></a>디버깅 정보 사용

디버깅 정보를 사용하도록 설정 하려면 **예(/Zi)** 이고 사용하지 않도록 설정하려면 **아니요** 입니다. 기본적으로 **디버그** 구성에 대한 값은 **예(/Zi)** 이고 **릴리스** 구성에 대한 값은 **아니요** 입니다.

### <a name="shader-type"></a>셰이더 형식

셰이더 종류를 지정합니다. 다양한 종류의 셰이더는 그래픽 파이프라인의 다른 파트를 구현합니다. 특정 종류의 셰이더는 **Shader Model** 속성에서 지정하는 최신 셰이더 모델에서만 사용할 수 있습니다(예: 셰이더 모델 5에 컴퓨팅 셰이더가 도입됐습니다).

이 속성은 HLSL 컴파일러에 대 한 **/t \[ 유형] _ \[ 모델]** 명령줄 인수의 **\[ 유형]** 부분에 해당 합니다. **셰이더 모델** 속성은 인수의 **[model]** 부분을 지정합니다.

**Choices**

- **효과**
- **꼭 짓 점 셰이더**
- **픽셀 셰이더**
- **기하 도형 셰이더**
- **헐 셰이더**
- **도메인 셰이더**
- **셰이더 계산**
- **라이브러리**
- **루트 서명 개체 생성**

### <a name="shader-model"></a>셰이더 모델

셰이더 모델을 지정합니다. 다양한 셰이더 모델은 기능이 다양합니다. 일반적으로 최신 셰이더 모델은 기능을 확장했지만 셰이더 코드를 실행하려면 최신 그래픽 하드웨어를 필요로 합니다. **셰이더 형식** 속성에서 지정하는 특정 종류의 셰이더는 최신 셰이더 모델에서만 사용할 수 있습니다(예: 셰이더 모델 5에 컴퓨팅 셰이더가 도입됐습니다).

이 속성은 HLSL 컴파일러에 대 한 **/t \[ 유형] _ \[ 모델]** 명령줄 인수의 **\[ model]** 부분에 해당 합니다. **셰이더 형식** 속성은 인수의 **[type]** 부분을 지정합니다.

### <a name="all-resources-bound"></a>모든 리소스 바인딩

컴파일러는 셰이더가 참조할 수 있는 모든 리소스가 바인딩되고 셰이더 실행 (/all_resources_bound) 기간 동안 양호한 상태임을 가정 합니다. 셰이더 모델 5.1 이상에 사용할 수 있습니다.

### <a name="enable-unbounded-descriptor-tables"></a>제한 없는 설명자 테이블 사용

셰이더가 제한 없는 범위 (/enable_unbounded_descriptor_tables)를 사용 하 여 리소스 배열의 선언을 포함할 수 있음을 컴파일러에 알립니다. 셰이더 모델 5.1 이상에 사용할 수 있습니다.

### <a name="set-root-signature"></a>루트 서명 설정

셰이더 바이트 코드에 루트 시그니처를 연결 합니다 (/setrootsignature). 셰이더 모델 5.0 이상에 사용할 수 있습니다.

### <a name="preprocessor-definitions"></a>전처리기 정의

HLSL 소스 코드 파일에 적용할 하나 이상의 전처리기 기호 정의를 추가합니다. 기호 정의를 구분하려면 세미콜론을 사용합니다.

이 속성은 HLSL 컴파일러에 대한 **/D \[definitions]** 명령줄 인수에 해당합니다.

### <a name="compile-a-direct2d-custom-pixel-shader-effect"></a>Direct2D 사용자 지정 픽셀 셰이더 효과 컴파일

픽셀 셰이더가 포함된 Direct2D 사용자 지정 효과를 컴파일합니다. 꼭짓점 또는 컴퓨팅 사용자 지정 효과에는 사용하지 마세요.

### <a name="multi-processor-compilation"></a>다중 프로세서 컴파일

동시에 여러 인스턴스를 실행 합니다.

## <a name="advanced-property-page"></a>고급 속성 페이지

### <a name="suppress-startup-banner"></a>시작 배너 표시 안 함

시작 배너 및 정보 메시지를 표시하지 않습니다. /nologo

### <a name="treat-warnings-as-errors"></a>경고를 오류로 처리

모든 컴파일러 경고를 오류로 처리합니다. 새 프로젝트인 경우 모든 컴파일에서/WX를 사용하는 것이 좋습니다. 모든 경고를 해결하면 찾기 어려운 코드 오류를 최소화할 수 있습니다.

## <a name="output-files-property-page"></a>출력 파일 속성 페이지

### <a name="header-variable-name"></a>헤더 변수 이름

헤더 파일 (/Vn [name])의 변수 이름 이름을 지정 합니다.

### <a name="header-file-name"></a>헤더 파일 이름

개체 코드를 포함하는 헤더 파일의 이름을 지정합니다. (/Fh [name])

### <a name="object-file-name"></a>개체 파일 이름

개체 파일의 이름을 지정합니다. (/Fo [name])

### <a name="assembler-output"></a>어셈블러 출력

어셈블리 언어 출력 파일의 콘텐츠를 지정합니다. (/Fc,/Fx)

**Choices**

- **목록 없음-나열** 되지 않습니다.
- **어셈블리 전용 목록** -어셈블리 코드 파일
- **어셈블리 코드 및 16 진수** 어셈블리 코드 및 16 진수 목록 파일

### <a name="assembler-output-file"></a>어셈블러 출력 파일

어셈블리 코드 목록 파일의 파일 이름을 지정 합니다.

## <a name="see-also"></a>참조

[C++ 프로젝트 속성 페이지 참조](property-pages-visual-cpp.md)<br>
[명령줄 속성 페이지](command-line-property-pages.md)<br>
[셰이더 컴파일](/windows/win32/direct3dhlsl/dx-graphics-hlsl-part1)
