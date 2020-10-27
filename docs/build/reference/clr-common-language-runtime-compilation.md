---
title: /clr(공용 언어 런타임 컴파일)
description: Microsoft c + + 컴파일러 옵션/clr을 사용 하 여 c + +/CLI 및 c + + 코드를 관리 코드로 컴파일합니다.
ms.date: 10/25/2020
f1_keywords:
- /CLR
- VC.Project.VCNMakeTool.CompileAsManaged
- VC.Project.VCCLCompilerTool.CompileAsManaged
helpviewer_keywords:
- cl.exe compiler, common language runtime option
- -clr compiler option [C++]
- clr compiler option [C++]
- /clr compiler option [C++]
- Managed Extensions for C++, compiling
- common language runtime, /clr compiler option
ms.assetid: fec5a8c0-40ec-484c-a213-8dec918c1d6c
ms.openlocfilehash: b4634b63e58344893d99e2217e57693a2c169f66
ms.sourcegitcommit: faecabcdd12ff53eb79dc0df193fc3567f2f037c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92639096"
---
# <a name="clr-common-language-runtime-compilation"></a>`/clr` (공용 언어 런타임 컴파일)

애플리케이션 및 구성 요소가 CLR(공용 언어 런타임)의 기능을 사용할 수 있게 합니다.

## <a name="syntax"></a>구문

> **`/clr`**\[**`:`**_옵션_ ]

## <a name="arguments"></a>인수

*옵션*\
쉼표로 구분 된 다음 인수 중 하나 이상입니다.

- 없음

   옵션을 사용 하지 않으면에서 **`/clr`** 응용 프로그램에 대 한 메타 데이터를 만듭니다. 메타데이터는 다른 CLR 애플리케이션에서 사용될 수 있으며 애플리케이션이 다른 CLR 구성 요소의 메타데이터에 있는 형식과 데이터를 사용할 수 있게 합니다. 자세한 정보는 [혼합형(네이티브 및 관리) 어셈블리](../../dotnet/mixed-native-and-managed-assemblies.md)를 참조하세요.

- **`pure`**

   **`/clr:pure` 는 사용 되지 않습니다** . 이 옵션은 Visual Studio 2017 이상에서 제거되었습니다. C#에 대한 순수형 MSIL이어야 하는 코드를 포팅하는 것이 좋습니다.

- **`safe`**

   **`/clr:safe` 는 사용 되지 않습니다** . 이 옵션은 Visual Studio 2017 이상에서 제거되었습니다. C#에 대한 안전 MSIL이어야 하는 코드를 포팅하는 것이 좋습니다.

- **`noAssembly`**

   **`/clr:noAssembly` 는 사용 되지 않습니다** . 대신 [ `/LN` (MSIL 모듈 만들기)를](ln-create-msil-module.md) 사용 합니다.

   컴파일러에 어셈블리 매니페스트를 출력 파일에 삽입 하지 않도록 지시 합니다. 기본적으로이 **`noAssembly`** 옵션은 적용 되지 않습니다.

   매니페스트에 어셈블리 메타 데이터가 없는 관리 되는 프로그램을 *모듈* 이라고 합니다. **`noAssembly`** 옵션은 모듈을 생성 하는 데만 사용할 수 있습니다. 및를 사용 하 여 컴파일하는 경우 [`/c`](c-compile-without-linking.md) **`/clr:noAssembly`** [`/NOASSEMBLY`](noassembly-create-a-msil-module.md) 링커 단계에서 옵션을 지정 하 여 모듈을 만듭니다.

   Visual Studio 2005 이전에는 **`/clr:noAssembly`** 필수 항목 **`/LD`** 입니다. **`/LD`** 는 이제을 지정할 때 암시 됩니다 **`/clr:noAssembly`** .

- **`initialAppDomain`**

   CLR 버전 1에서 c + +/CLI 응용 프로그램을 실행할 수 있도록 합니다.  를 사용 하 여 컴파일된 응용 프로그램은 **`initialAppDomain`** CLR 버전 1에서 지원 되지 않으므로 ASP.NET를 사용 하는 응용 프로그램에서 사용 하면 안 됩니다.

- **`nostdlib`**

   기본 디렉터리를 무시 하도록 컴파일러에 지시 합니다 *`\clr`* . System.dll와 같이 여러 버전의 DLL을 포함 하는 경우 컴파일러에서 오류를 생성 합니다. 이 옵션을 사용 하면 컴파일하는 동안 사용할 특정 프레임 워크를 지정할 수 있습니다.

## <a name="remarks"></a>설명

관리 코드는 CLR에서 검사 및 관리할 수 있는 코드입니다. 관리 코드는 관리되는 개체에 액세스할 수 있습니다. 자세한 내용은 [ `/clr ` 제한 사항](clr-restrictions.md)을 참조 하세요.

C + +에서 관리 되는 형식을 정의 및 사용 하는 응용 프로그램을 개발 하는 방법에 대 한 자세한 내용은 [런타임 플랫폼용 구성 요소 확장](../../extensions/component-extensions-for-runtime-platforms.md)을 참조 하세요.

를 사용 하 여 컴파일된 응용 프로그램은 **`/clr`** 관리 되는 데이터를 포함 하거나 포함 하지 않을 수 있습니다.

관리 되는 응용 프로그램에서 디버깅을 사용 하도록 설정 하려면 [ `/ASSEMBLYDEBUG` (DebuggableAttribute 추가)](assemblydebug-add-debuggableattribute.md)를 참조 하세요.

CLR 형식만 가비지 수집 힙에 인스턴스화됩니다. 자세한 내용은 [클래스 및 구조체](../../extensions/classes-and-structs-cpp-component-extensions.md)를 참조하세요. 함수를 네이티브 코드로 컴파일하려면 `unmanaged` pragma를 사용합니다. 자세한 내용은 [ `managed` ,을 `unmanaged` ](../../preprocessor/managed-unmanaged.md)참조 하십시오.

기본적으로는 **`/clr`** 적용 되지 않습니다. **`/clr`** 이 적용 되 면 **`/MD`** 도 적용 됩니다. 자세한 내용은 [ `/MD` , `/MT` , `/LD` (Run-Time 라이브러리 사용)](md-mt-ld-use-run-time-library.md)를 참조 하세요. **`/MD`** 표준 헤더 파일에서 동적으로 연결 된 다중 스레드 버전의 런타임 루틴이 선택 되도록 합니다. CLR 가비지 수집기는 보조 스레드에서 종료자를 실행하므로 관리되는 프로그래밍에 다중 스레딩이 필요합니다.

를 사용 하 여 컴파일하는 경우 **`/c`** 링커 옵션을 사용 하 여 결과 출력 파일의 CLR 형식을 지정할 수 있습니다 [`/CLRIMAGETYPE`](clrimagetype-specify-type-of-clr-image.md) .

**`/clr`** 는 **`/EHa`** 를 암시 하며 다른 **`/EH`** 옵션은에 대해 지원 되지 않습니다 **`/clr`** . 자세한 내용은 [ `/EH` (예외 처리 모델)](eh-exception-handling-model.md)를 참조 하세요.

파일의 CLR 이미지 형식을 결정 하는 방법에 대 한 자세한 내용은을 참조 하십시오 [`/CLRHEADER`](clrheader.md) .

지정 된 링커 호출에 전달 되는 모든 모듈은 동일한 런타임 라이브러리 컴파일러 옵션 (또는)을 사용 하 여 컴파일해야 **`/MD`** 합니다 **`/LD`** .

[`/ASSEMBLYRESOURCE`](assemblyresource-embed-a-managed-resource.md)링커 옵션을 사용 하 여 어셈블리에 리소스를 포함 합니다. [`/DELAYSIGN`](delaysign-partially-sign-an-assembly.md), [`/KEYCONTAINER`](keycontainer-specify-a-key-container-to-sign-an-assembly.md) 및 [`/KEYFILE`](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) 링커 옵션을 사용 하 여 어셈블리를 만드는 방법을 사용자 지정할 수도 있습니다.

을 **`/clr`** 사용 하는 경우 `_MANAGED` 기호가 1로 정의 됩니다. 자세한 내용은 [미리 정의 된 매크로](../../preprocessor/predefined-macros.md)를 참조 하세요.

네이티브 개체 파일의 전역 변수는 먼저 초기화 된 `DllMain` 다음 (실행 파일이 DLL 인 경우) 관리 되는 섹션의 전역 변수가 초기화 됩니다 (관리 코드를 실행 하기 전에). [`#pragma init_seg`](../../preprocessor/init-seg.md) 는 관리 되는 범주와 관리 되지 않는 범주의 초기화 순서에만 영향을 줍니다.

### <a name="metadata-and-unnamed-classes"></a>메타데이터 및 명명되지 않은 클래스

명명 되지 않은 클래스는와 같은 이름의 메타 데이터에 표시  `$UnnamedClass$<crc-of-current-file-name>$<index>$` `<index>` 됩니다. 여기서는 컴파일에 명명 되지 않은 클래스의 순차적 개수입니다. 예를 들어 다음 코드 샘플은 메타데이터에 명명되지 않은 클래스를 생성합니다.

```cpp
// clr_unnamed_class.cpp
// compile by using: /clr /LD
class {} x;
```

메타데이터를 보려면 Ildasm.exe를 사용합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성** 드롭다운을 **모든 구성** 으로 설정 하 고 **플랫폼** 드롭다운을 **모든 플랫폼** 으로 설정 합니다.

1. **구성 속성**  >  **고급** 페이지를 선택 합니다.

1. **공용 언어 런타임 지원** 속성을 수정 합니다. **확인** 을 선택하여 변경 내용을 저장합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAsManaged>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)\
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
