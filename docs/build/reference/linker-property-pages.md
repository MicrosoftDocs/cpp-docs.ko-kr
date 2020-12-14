---
description: '자세한 정보: 링커 속성 페이지'
title: 링커 속성 페이지
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
ms.openlocfilehash: 308b5d27eda497f196479b063388c33d1c4eddc8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199430"
---
# <a name="linker-property-pages"></a>링커 속성 페이지

**프로젝트**  >  **속성**  >  **구성 속성**  >  **링커** 에는 다음 속성이 있습니다. 링커에 대 한 자세한 내용은 [CL에서 링커](cl-invokes-the-linker.md) 및 [링커 옵션](linker-options.md)호출을 참조 하세요.

## <a name="general-property-page"></a>일반 속성 페이지

### <a name="output-file"></a>출력 파일

[/Out](out-output-file-name.md) 옵션은 링커가 만드는 프로그램의 기본 이름과 위치를 재정의 합니다.

### <a name="show-progress"></a>진행률 표시

링커 진행 메시지를 출력 합니다.

**Choices**

- **설정 되지 않음** -자세한 정도 없음
- **모든 진행 메시지 표시** -모든 진행 메시지를 표시 합니다.
- **라이브러리 검색** -검색 된 라이브러리만 표시 하는 진행률 메시지를 표시 합니다.
- **최적화 된 링크 중 comdat 정리** 정보-최적화 된 링크 중에 comdat 정리에 대 한 정보를 표시 합니다.
- **최적화 된 링크 중 제거 된 데이터** 정보-최적화 된 링크 중 제거 된 함수 및 데이터에 대 한 정보를 표시 합니다.
- **SEH와 호환 되지 않는 모듈** 정보-안전 예외 처리와 호환 되지 않는 모듈에 대 한 정보를 표시 합니다.
- **관리 코드와 관련 된 링커 작업** 정보-관리 코드와 관련 된 링커 작업에 대 한 정보를 표시 합니다.

### <a name="version"></a>버전

[/VERSION](version-version-information.md) 옵션은 .exe 또는 .dll 파일의 헤더에 버전 번호를 삽입 하도록 링커에 지시 합니다. DUMPBIN/HEADERS를 사용 하 여 선택적 헤더 값의 이미지 버전 필드를 확인 하 고 **/VERSION** 효과를 확인 합니다.

### <a name="enable-incremental-linking"></a>증분 링크 사용

증분 링크를 사용 하도록 설정 합니다. ([/INCREMENTAL](incremental-link-incrementally.md),/INCREMENTAL: NO)

### <a name="suppress-startup-banner"></a>시작 배너 표시 안 함

[/Nologo](nologo-suppress-startup-banner-linker.md) 옵션을 선택 하면 저작권 메시지와 버전 번호가 표시 되지 않습니다.

### <a name="ignore-import-library"></a>가져오기 라이브러리 무시

이 속성은 이 빌드에서 생성된 .lib 출력을 종속 프로젝트에 연결하지 않도록 링커에 지시합니다. 프로젝트 시스템에서 빌드할 때 .lib 파일을 생성 하지 않는 .dll 파일을 처리할 수 있습니다. 프로젝트가 DLL을 생성하는 다른 프로젝트에 종속되는 경우 프로젝트 시스템은 해당 하위 프로젝트에서 생성한 .lib 파일을 자동으로 연결합니다. COM Dll 또는 리소스 전용 Dll을 생성 하는 프로젝트에서는 이러한 Dll이 의미 있는 내보내기를 포함 하지 않으므로이 속성은 필요 하지 않을 수 있습니다. DLL에 내보내기가 없는 경우 링커는 .lib 파일을 생성 하지 않습니다. 내보내기 .lib 파일이 없고 프로젝트 시스템에서 링커가 누락 된 DLL과 연결 하도록 지시 하면 링크가 실패 합니다. 이 문제를 해결하려면 **가져오기 라이브러리 무시** 속성을 사용하세요. **예** 로 설정 되 면 프로젝트 시스템은 .lib 파일이 있는지 여부를 무시 하 고이 프로젝트에 종속 된 모든 프로젝트가 존재 하지 않는 .lib 파일에 연결 되지 않도록 합니다.

프로그래밍 방식으로 이 속성에 액세스하려면 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>을 참조하세요.

### <a name="register-output"></a>출력 등록

.dll 프로젝트에서만 유효한 빌드 출력에서 `regsvr32.exe /s $(TargetPath)`를 실행합니다. .exe 프로젝트의 경우 이 속성은 무시됩니다. .exe 출력을 등록하려면 구성에 postbuild 이벤트를 설정하여, 등록된 .exe 파일에 항상 필요한 사용자 지정 등록을 수행합니다.

프로그래밍 방식으로 이 속성에 액세스하려면 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>을 참조하세요.

### <a name="per-user-redirection"></a>사용자별 리디렉션

Visual Studio의 등록은 일반적으로 HKEY_CLASSES_ROOT(HKCR)에서 수행되었습니다. Windows Vista 이상의 운영 체제에서 HKCR에 액세스하려면 Visual Studio를 승격된 모드로 실행해야 합니다. 개발자는 항상 관리자 모드에서 실행 하는 것은 아니지만 등록을 계속 사용 해야 합니다. 사용자 단위 리디렉션은 관리자 모드로 실행 하지 않고도 등록할 수 있습니다.

사용자별 리디렉션은 HKCR에 대한 모든 쓰기가 HKEY\_CURRENT\_USER(HKCU)로 리디렉션되도록 합니다. 사용자별 리디렉션이 해제되어 있는 경우 프로그램이 HKCR에 쓰려고 할 때 [프로젝트 빌드 오류 PRJ0050](../../error-messages/tool-errors/project-build-error-prj0050.md)이 발생할 수 있습니다.

### <a name="additional-library-directories"></a>추가 라이브러리 디렉터리

사용자가 환경의 라이브러리 경로를 재정의할 수 있습니다. ([/Libpath](libpath-additional-libpath.md): 폴더)

### <a name="link-library-dependencies"></a>라이브러리 종속성 링크

종속 프로젝트에서 생성한 .lib 파일을 연결할지 여부를 지정합니다. 일반적으로 .lib 파일에 연결 하려고 하지만 특정 Dll의 경우가 아닐 수 있습니다.

파일 이름과 상대 경로를 제공하여 .obj 파일을 지정할 수도 있습니다(예: "..\\..\MyLibProject\MyObjFile.obj"). .Obj 파일의 소스 코드에서 미리 컴파일된 헤더 (예: .pch. h)를 #includes 하는 경우 pch .obj 파일은 MyObjFile .obj와 동일한 폴더에 있습니다. 또한 추가 종속성으로 .pch .obj를 추가 해야 합니다.

### <a name="use-library-dependency-inputs"></a>라이브러리 종속성 입력 사용

프로젝트 종속성의 라이브러리 출력에 링크할 때 라이브러리 파일 자체가 아닌 라이브러리 관리자 도구에 대 한 입력을 사용할지 여부를 지정 합니다. 대규모 프로젝트에서 종속 프로젝트가 .lib 파일을 생성하면 증분 연결은 사용할 수 없습니다. .lib 파일을 생성하는 많은 종속 프로젝트가 있는 경우 애플리케이션을 빌드하는 데 오랜 시간이 걸릴 수 있습니다. 이 속성이 **예** 로 설정 되 면 프로젝트 시스템이 종속 프로젝트에서 생성 한 .lib 파일의 .obj 파일에 연결 되므로 증분 링크를 사용할 수 있습니다.

**일반** 링커 속성 페이지에 액세스 하는 방법에 대 한 자세한 내용은 [Visual Studio에서 c + + 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조 하세요.

### <a name="link-status"></a>연결 상태

링커가 완료 된 링크 비율을 표시 하는 진행률 표시기를 표시 해야 하는지 여부를 지정 합니다. 기본적으로이 상태 정보는 표시 되지 않습니다. ([/LTCG](ltcg-link-time-code-generation.md): STATUS | LTCG: NOSTATUS)

### <a name="prevent-dll-binding"></a>DLL 바인딩 방지

[/Allowbind](allowbind-prevent-dll-binding.md): NO는 이미지를 바인딩할 수 없음을 Bind.exe를 나타내는 DLL의 헤더에 비트를 설정 합니다. 바인딩이 서명을 무효화하므로 디지털 서명된 경우 DLL을 바인딩하지 않으려고 할 수 있습니다.

### <a name="treat-linker-warning-as-errors"></a>링커 경고를 오류로 처리

[/Wx](wx-treat-linker-warnings-as-errors.md) 를 설정 하면 링커에서 경고가 생성 될 경우 출력 파일이 생성 되지 않습니다.

### <a name="force-file-output"></a>강제 파일 출력

[/Force](force-force-file-output.md) 옵션을 지정 하면 기호가 참조 되었지만 정의 되지 않았거나 여러 번 정의 된 경우에도 .exe 파일이 나 DLL을 만들도록 링커에 지시 합니다. 잘못 된 .exe 파일을 만들 수 있습니다.

**Choices**

- **사용** -/force 인수 없이 multiple 및 확인 되지 않음을 모두 의미 합니다.
- **정의 된 기호만 곱하기** -LINK에서 기호에 대 한 정의를 둘 이상 발견 하는 경우에도/FORCE: MULTIPLE을 사용 하 여 출력 파일을 만듭니다.
- **정의 되지 않은 기호만** 해당-/FORCE: 확인할 수 없음을 사용 하 여 출력 파일을 만듭니다. LINK에서 정의 되지 않은 기호를 찾는 지 여부입니다. /FORCE: 진입점 기호를 확인할 수 없는 경우 확인 되지 않은가 무시 됩니다.

### <a name="create-hot-patchable-image"></a>핫 패치 가능한 이미지 만들기

핫 패치를 위한 이미지를 준비 합니다.

**Choices**

- **사용** -핫 패치를 위한 이미지를 준비 합니다.
- **X86 이미지만** -핫 패치를 위한 x86 이미지를 준비 합니다.
- **X64 이미지만** -핫 패치를 위한 x64 이미지를 준비 합니다.
- **Itanium 이미지만** -핫 패치를 위한 itanium 이미지를 준비 합니다.

### <a name="specify-section-attributes"></a>섹션 특성 지정

[/SECTION](section-specify-section-attributes.md) 옵션은 섹션의 .obj 파일을 컴파일할 때 설정한 특성을 재정의 하 여 섹션의 특성을 변경 합니다.

## <a name="input-property-page"></a>입력 속성 페이지

### <a name="additional-dependencies"></a>추가 종속성

링크 명령줄에 추가할 추가 항목을 지정 합니다 (예: *kernel32.dll*).

### <a name="ignore-all-default-libraries"></a>모든 기본 라이브러리 무시

[/Nodefaultlib](nodefaultlib-ignore-libraries.md) 옵션은 외부 참조를 확인할 때 검색 하는 라이브러리 목록에서 하나 이상의 기본 라이브러리를 제거 하도록 링커에 지시 합니다.

### <a name="ignore-specific-default-libraries"></a>특정 기본 라이브러리 무시

무시할 하나 이상의 기본 라이브러리 이름을 지정합니다. 여러 라이브러리를 세미콜론으로 구분 합니다. (/NODEFAULTLIB: [name, name, ...])

### <a name="module-definition-file"></a>모듈 정의 파일

[/Def](def-specify-module-definition-file.md) 옵션은 모듈 정의 파일 (.def)을 링커에 전달 합니다. 하나의 .def 파일만 연결 하도록 지정할 수 있습니다.

### <a name="add-module-to-assembly"></a>어셈블리에 모듈 추가

[/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md) 옵션을 사용 하면 어셈블리에 모듈 참조를 추가할 수 있습니다. 모듈의 형식 정보는 모듈 참조를 추가한 어셈블리 프로그램에서 사용할 수 없습니다. 그러나 모듈의 형식 정보는 어셈블리를 참조 하는 모든 프로그램에서 사용할 수 있습니다.

### <a name="embed-managed-resource-file"></a>관리 되는 리소스 파일 포함

[/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md) 는 출력 파일에 리소스 파일을 포함 합니다.

### <a name="force-symbol-references"></a>강제 기호 참조

[/INCLUDE](include-force-symbol-references.md) 옵션은 지정 된 기호를 기호 테이블에 추가 하도록 링커에 지시 합니다.

### <a name="delay-loaded-dlls"></a>지연 로드 된 Dll

[/DELAYLOAD](delayload-delay-load-import.md) 옵션을 선택 하면 dll이 지연 로드 됩니다. Dll 이름은 로드를 지연 하는 DLL을 지정 합니다.

### <a name="assembly-link-resource"></a>어셈블리 링크 리소스

[/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md) 옵션은 출력 파일에 .NET Framework 리소스에 대 한 링크를 만듭니다. 리소스 파일은 출력 파일에 배치 되지 않습니다.

## <a name="manifest-file-property-page"></a>매니페스트 파일 속성 페이지

### <a name="generate-manifest"></a>매니페스트 생성

[/Sd](manifest-create-side-by-side-assembly-manifest.md) 는 링커가 side-by-side 매니페스트 파일을 만들도록 지정 합니다.

### <a name="manifest-file"></a>매니페스트 파일

[/MANIFESTFILE](manifestfile-name-manifest-file.md) 를 사용 하면 매니페스트 파일의 기본 이름을 변경할 수 있습니다. 매니페스트 파일의 기본 이름은 .manifest가 추가 된 파일 이름입니다.

### <a name="additional-manifest-dependencies"></a>추가 매니페스트 종속성

[/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md) 를 사용 하면 매니페스트 파일의 종속성 섹션에 배치 되는 특성을 지정할 수 있습니다.

### <a name="allow-isolation"></a>격리 허용

매니페스트 조회 동작을 지정합니다. ([/ALLOWISOLATION](allowisolation-manifest-lookup.md): NO)

### <a name="enable-user-account-control-uac"></a>UAC (사용자 계정 컨트롤) 사용

사용자 계정 컨트롤을 사용할 수 있는지 여부를 지정 합니다.  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md),/MANIFESTUAC: NO)

### <a name="uac-execution-level"></a>UAC 실행 수준

사용자 계정 컨트롤을 사용 하 여 실행할 때 응용 프로그램에 대해 요청 된 실행 수준을 지정 합니다.  (/MANIFESTUAC: level = [value])

**Choices**

- **asInvoker** -UAC 실행 수준: 호출자입니다.
- **highestAvailable** -UAC 실행 수준: 사용 가능한 가장 높은 수준입니다.
- **requireAdministrator** -UAC 실행 수준: 관리자가 필요 합니다.

### <a name="uac-bypass-ui-protection"></a>UAC UI 보호 건너뛰기

바탕 화면의 다른 창에 대해 사용자 인터페이스 보호 수준을 건너뛸지 여부를 지정 합니다.  내게 필요한 옵션 지원 응용 프로그램의 경우이 속성을 ' y e s '로 설정 합니다.  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md): uiAccess = [true | false])

## <a name="debugging-property-page"></a>디버깅 속성 페이지

### <a name="generate-debug-info"></a>디버그 정보 생성

이 옵션을 사용 하면 .exe 파일 또는 DLL에 대 한 디버깅 정보를 만들 수 있습니다.

**Choices**

- **아니요** -디버깅 정보를 생성 하지 않습니다.
- **디버그 정보 생성** -Microsoft 기호 서버에 배포 하는 데 이상적인 완전 한 PDB (프로그램 데이터베이스)를 만듭니다.
- **빠른 링크를 위해 최적화 된 디버그 정보 생성** -링크 편집-디버그 주기에 이상적인 PDB (프로그램 데이터베이스)를 생성 합니다.
- **공유 및 게시를 위해 최적화 된 디버그 정보 생성** -링크 편집-디버그 주기에 이상적인 PDB (프로그램 데이터베이스)를 생성 합니다.

### <a name="generate-program-database-file"></a>프로그램 데이터베이스 파일 생성

기본적으로 [/debug](debug-generate-debug-info.md) 를 지정 하면 링커에서 디버깅 정보를 포함 하는 PDB (프로그램 데이터베이스)를 만듭니다. PDB의 기본 파일 이름에는 프로그램의 기본 이름과 확장명 .pdb가 있습니다.

### <a name="strip-private-symbols"></a>전용 기호 제거

[/PDBSTRIPPED](pdbstripped-strip-private-symbols.md) 옵션은 pdb 파일을 생성 하는 컴파일러 또는 링커 옵션 (/Debug,/z7,/Zd 또는/zi)을 사용 하 여 프로그램 이미지를 빌드할 때 두 번째 pdb (프로그램 데이터베이스) 파일을 만듭니다.

### <a name="generate-map-file"></a>맵 파일 생성

[/Map](map-generate-mapfile.md) 옵션을 통해 링커가 맵 파일을 만들도록 지시 합니다.

### <a name="map-file-name"></a>맵 파일 이름

맵 파일의 사용자 지정 이름입니다. 기본 이름을 대체 합니다.

### <a name="map-exports"></a>맵 내보내기

[/MAPINFO](mapinfo-include-information-in-mapfile.md) 옵션을 지정 하면 지정 된 정보를 맵 파일에 포함 하도록 링커에 지시 합니다 .이 옵션은/map 옵션을 지정 하면 생성 됩니다. 내보내기는 내보낸 함수를 포함 하도록 링커에 지시 합니다.

### <a name="debuggable-assembly"></a>디버깅 가능한 어셈블리

[/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md) 는 디버그 정보 추적을 사용 하 여 DebuggableAttribute 특성을 내보내고 JIT 최적화를 사용 하지 않도록 설정 합니다.

## <a name="system-property-page"></a>시스템 속성 페이지

### <a name="subsystem"></a>SubSystem

[/SUBSYSTEM](subsystem-specify-subsystem.md) 옵션을 통해 운영 체제에서 .exe 파일을 실행 하는 방법을 알 수 있습니다. 선택 하는 하위 시스템은 링커에서 선택할 진입점 기호 (또는 진입점 함수)에 영향을 줍니다.

**Choices**

- **설정 되지 않음** -하위 시스템 집합이 없습니다.
- **콘솔** -Win32 문자 모드 응용 프로그램입니다. 콘솔 응용 프로그램에는 운영 체제에 의해 콘솔이 제공 됩니다. Main 또는 wmain이 정의 되어 있으면 CONSOLE이 기본값입니다.
- **Windows** -응용 프로그램은 사용자와의 상호 작용을 위해 자체 창을 만들기 때문에 콘솔이 필요 하지 않습니다. WinMain 또는 wWinMain이 정의 된 경우 WINDOWS가 기본값입니다.
- Windows NT 용 **네이티브** 장치 드라이버입니다. /DRIVER: WDM을 지정 하면 NATIVE가 기본값입니다.
- **Efi 응용** 프로그램-Efi 응용 프로그램입니다.
- **Efi 부트 서비스 드라이버** -Efi 부트 서비스 드라이버입니다.
- **EFI ROM** -EFI ROM.
- **Efi 런타임** -efi 런타임
- **Posix** -Windows NT의 posix 하위 시스템에서 실행 되는 응용 프로그램입니다.

### <a name="minimum-required-version"></a>필요한 최소 버전

하위 시스템의 최소 필수 버전을 지정 합니다. 인수는 0에서 65535 사이의 10 진수입니다.

### <a name="heap-reserve-size"></a>힙 예약 크기

가상 메모리의 총 힙 할당 크기를 지정 합니다. 기본값은 1mb입니다.    ([/힙](heap-set-heap-size.md): 예약)

### <a name="heap-commit-size"></a>힙 커밋 크기

실제 메모리의 총 힙 할당 크기를 지정 합니다. 기본값은 4kb입니다.    ([/힙](heap-set-heap-size.md): 예약, 커밋)

### <a name="stack-reserve-size"></a>스택 예약 크기

가상 메모리의 총 스택 할당 크기를 지정합니다. 기본값은 1mb입니다.     ([/STACK](stack-stack-allocations.md): reserve)

### <a name="stack-commit-size"></a>스택 커밋 크기

실제 메모리의 총 스택 할당 크기를 지정 합니다. 기본값은 4kb입니다.     ([/STACK](stack-stack-allocations.md): reserve, commit)

### <a name="enable-large-addresses"></a>대량 주소 사용

[/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md) 옵션은 응용 프로그램이 2gb를 초과 하는 주소를 처리할 수 있음을 링커에 지시 합니다. 기본적으로/LARGEADDRESSAWARE: NO는 링커 줄에/LARGEADDRESSAWARE가 지정 되지 않은 경우에 사용할 수 있습니다.

### <a name="terminal-server"></a>터미널 서버

[/TSAWARE](tsaware-create-terminal-server-aware-application.md) 옵션은 프로그램 이미지의 선택적 헤더에 있는 IMAGE_OPTIONAL_HEADER DllCharacteristics 필드에 플래그를 설정 합니다. 이 플래그를 설정하면 터미널 서버가 애플리케이션에서 특정 변경 작업을 수행할 수 없습니다.

### <a name="swap-run-from-cd"></a>CD에서 스왑 실행

[/Swrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrap](swaprun-load-linker-output-to-swap-file.md) 이 옵션은 Windows NT 4.0 이상 버전의 기능입니다. **CD** 를 지정 하면 운영 체제에서 이동식 디스크의 이미지를 페이지 파일로 복사한 다음 로드 합니다.

### <a name="swap-run-from-network"></a>네트워크에서 스왑 실행

[/Swrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrap](swaprun-load-linker-output-to-swap-file.md) 이 옵션은 Windows NT 4.0 이상 버전의 기능입니다. **NET** 이 지정 된 경우 운영 체제는 먼저 네트워크에서 스왑 파일로 이진 이미지를 복사 하 고 여기에서 로드 합니다. 이 옵션은 네트워크를 통해 응용 프로그램을 실행 하는 데 유용 합니다.

### <a name="driver"></a>드라이버

[/DRIVER](driver-windows-nt-kernel-mode-driver.md) 링커 옵션을 사용 하 여 Windows NT 커널 모드 드라이버를 빌드할 수 있습니다.

**Choices**

- **설정 되지 않음** -기본 드라이버 설정입니다.
- **드라이버** -드라이버
- **Up only** -/DRIVER: uponly를 지정 하면 링커가 출력 헤더의 특성에 IMAGE_FILE_UP_SYSTEM_ONLY 비트를 추가 하 여이 드라이버가 단일 프로세서 (UP) 드라이버 임을 지정 합니다. 운영 체제는 다중 프로세서 (MP) 시스템에서 UP 드라이버 로드를 거부 합니다.
- /DRIVER **: wdm를** 지정 하면 링커가 선택적 헤더의 DLLCHARACTERISTICS 필드에 IMAGE_DLLCHARACTERISTICS_WDM_DRIVER 비트를 설정 합니다.

## <a name="optimization-property-page"></a>최적화 속성 페이지

### <a name="references"></a>참조

[/Opt](opt-optimizations.md): REF는 참조 되지 않는 함수 및/또는 데이터를 참조 하지 않는 반면/opt: 없음 ef는 참조 되지 않는 함수 및/또는 데이터를 유지 합니다.

### <a name="enable-comdat-folding"></a>COMDAT 정리 사용

[/Opt](opt-optimizations.md): ICF \[ = 반복]을 사용 하 여 동일한 COMDAT 정리를 수행 합니다.

### <a name="function-order"></a>함수 순서

[/Order](order-put-functions-in-order.md)옵션은 특정 comdat를 미리 결정 된 순서로 이미지에 배치 하 여 프로그램을 최적화 하도록 링크에 지시 합니다. LINK는 이미지의 각 섹션 내에 지정 된 순서로 함수를 배치 합니다.

### <a name="profile-guided-database"></a>프로필 기반 데이터베이스

프로필 기반 최적화를 위한 .pgd 파일을 지정 합니다. ([/PGD](pgd-specify-database-for-profile-guided-optimizations.md))

### <a name="link-time-code-generation"></a>링크 타임 코드 생성

링크 타임 코드 생성을 지정합니다. ([/Ltcg](ltcg-link-time-code-generation.md))

**Choices**

- **기본** -기본 LTCG 설정입니다.
- **빠른 링크 타임 코드 생성 사용** - [/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)에서 링크 타임 코드 생성을 사용 합니다.
- **링크 타임 코드 생성 사용** - [링크 타임 코드 생성](ltcg-link-time-code-generation.md)을 사용 합니다.
- **프로필 기반 최적화-계측** -:P ginstrument [프로필 기반 최적화](../profile-guided-optimizations.md) 를 사용 합니다.
- **프로필 기반 최적화-최적화** -링커에서 계측 된 이진 파일을 실행 한 후 생성 된 프로필 데이터를 사용 하 여 최적화 된 이미지를 만들도록 지정 합니다.
- **프로필 기반 최적화-업데이트** -:P ginstrument 단계에서 지정 된 것에서 추가 하거나 수정할 입력 파일 목록을 허용 하 고 추적 합니다.

## <a name="embedded-idl-property-page"></a>포함 IDL 속성 페이지

### <a name="midl-commands"></a>MIDL 명령

MIDL 명령줄 옵션을 지정 하십시오. ([/MIDL](midl-specify-midl-command-line-options.md) :@responsefile )

### <a name="ignore-embedded-idl"></a>포함 IDL 무시

[/IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md) 옵션은 소스 코드의 모든 idl 특성이 .idl 파일에서 처리 되지 않도록 지정 합니다.

### <a name="merged-idl-base-file-name"></a>병합 된 IDL 기본 파일 이름

[/IDLOUT](idlout-name-midl-output-files.md) 옵션은 .idl 파일의 이름과 확장명을 지정 합니다.

### <a name="type-library"></a>형식 라이브러리

[/TLBOUT](tlbout-name-dot-tlb-file.md) 옵션은 .tlb 파일의 이름과 확장명을 지정 합니다.

### <a name="typelib-resource-id"></a>TypeLib 리소스 ID

링커에서 생성 된 형식 라이브러리의 리소스 ID를 지정할 수 있습니다. ([/TLBID](tlbid-specify-resource-id-for-typelib.md): id)

## <a name="windows-metadata-property-page"></a>Windows 메타 데이터 속성 페이지

### <a name="generate-windows-metadata"></a>Windows 메타 데이터 생성

Windows 메타 데이터 생성을 사용 하거나 사용 하지 않도록 설정 합니다.

**Choices**

- **예** -Windows 메타 데이터 파일을 생성 하도록 설정 합니다.
- **아니요** -Windows 메타 데이터 파일을 생성 하지 않습니다.

### <a name="windows-metadata-file"></a>Windows 메타 데이터 파일

[/WINMDFILE](winmdfile-specify-winmd-file.md) 옵션 스위치입니다.

### <a name="windows-metadata-key-file"></a>Windows 메타 데이터 키 파일

Windows 메타 데이터에 서명할 키 또는 키 쌍을 지정 하십시오. ([/WINMDKEYFILE](winmdkeyfile-specify-winmd-key-file.md): filename)

### <a name="windows-metadata-key-container"></a>Windows 메타 데이터 키 컨테이너

Windows 메타 데이터에 서명할 키 컨테이너를 지정 합니다. ([/WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md): name)

### <a name="windows-metadata-delay-sign"></a>Windows 메타 데이터 지연 서명

Windows 메타 데이터에 부분적으로 서명 합니다. Windows 메타 데이터에 공개 키를 저장 하려는 경우에만 [/WINMDDELAYSIGN](winmddelaysign-partially-sign-a-winmd.md) 를 사용 합니다. 기본값은/WINMDDELAYSIGN: NO입니다.

## <a name="advanced-property-page"></a>고급 속성 페이지

### <a name="entry-point"></a>진입점

[/Entry](entry-entry-point-symbol.md) 옵션은 진입점 함수를 .exe 파일이 나 DLL의 시작 주소로 지정 합니다.

### <a name="no-entry-point"></a>진입점 없음

리소스 전용 DLL을 만들려면 [/NOENTRY](noentry-no-entry-point.md)옵션을 사용 해야 합니다 .이 옵션을 사용 하 여 연결에서 dll에 대 한 참조를 연결 하지 않도록 합니다. `_main`

### <a name="set-checksum"></a>체크섬 설정

[/RELEASE](release-set-the-checksum.md) 옵션은 .exe 파일의 헤더에 체크섬을 설정 합니다.

### <a name="base-address"></a>기준 주소

프로그램의 기준 주소를 설정합니다. ([/Base](base-base-address.md): {address \[ , size] | @filename , key})

### <a name="randomized-base-address"></a>임의 기준 주소

임의 기준 주소입니다. ([/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md) \[ : NO])

### <a name="fixed-base-address"></a>고정 기준 주소

기본 설정 기준 주소에서만 로드할 수 있는 프로그램을 만듭니다. ([/FIXED](fixed-fixed-base-address.md) \[ : NO])

### <a name="data-execution-prevention-dep"></a>DEP(데이터 실행 방지) 

실행 파일이 Windows 데이터 실행 방지 기능과 호환 되는지 테스트 한 것으로 표시 합니다. ([/NXCOMPAT](nxcompat-compatible-with-data-execution-prevention.md) \[ : NO])

### <a name="turn-off-assembly-generation"></a>어셈블리 생성 해제

[/Noassembly](noassembly-create-a-msil-module.md) 옵션은 .NET Framework 어셈블리 없이 현재 출력 파일에 대 한 이미지를 만들도록 링커에 지시 합니다.

### <a name="unload-delay-loaded-dll"></a>지연 로드 된 DLL 언로드

**UNLOAD** 한정자는 지연 로드 도우미 함수에 DLL의 명시적 언로드를 지원 하도록 지시 합니다. ([/DELAY](delay-delay-load-import-settings.md): UNLOAD)

### <a name="nobind-delay-loaded-dll"></a>Nobind 지연 로드 된 DLL

**NOBIND** 한정자는 런타임에 바인딩 가능한 IAT를 최종 이미지에 포함 하지 않도록 링커에 지시 합니다. 기본값은 지연 로드된 DLL에 대해 바인딩할 수 있는 IAT를 만드는 것입니다. ([/DELAY](delay-delay-load-import-settings.md): NOBIND)

### <a name="import-library"></a>가져오기 라이브러리

기존 가져오기 라이브러리 이름을 재정의합니다. ([/IMPLIB](implib-name-import-library.md): filename)

### <a name="merge-sections"></a>섹션 병합

[/Merge](merge-combine-sections.md) 옵션은 첫 번째 섹션 (에서)을 두 번째 섹션 ()으로 결합 하 여 결과 섹션의 이름을로 지정 합니다. 예:/merge:. .rdata =. text.

### <a name="target-machine"></a>대상 컴퓨터

[/MACHINE](machine-specify-target-platform.md) 옵션은 프로그램의 대상 플랫폼을 지정 합니다.

**Choices**

- **설정 안 함**
- **MachineARM**
- **MachineARM64**
- **MachineEBC**
- **MachineIA64**
- **MachineMIPS**
- **MachineMIPS16**
- **MachineMIPSFPU**
- **MachineMIPSFPU16**
- **MachineSH4**
- **MachineTHUMB**
- **MachineX64**
- **MachineX86**

### <a name="profile"></a>프로필

성능 도구 프로파일러와 함께 사용할 수 있는 출력 파일을 생성합니다. GenerateDebugInformation (/[/debug](debug-generate-debug-info.md))을 설정 해야 합니다. ([/PROFILE](profile-performance-tools-profiler.md))

### <a name="clr-thread-attribute"></a>CLR 스레드 특성

CLR 프로그램의 진입점에 대 한 스레딩 특성을 명시적으로 지정 합니다.

**Choices**

- **MTA 스레딩 특성** -프로그램의 진입점에 MTAThreadAttribute 특성을 적용 합니다.
- **STA 스레딩 특성** -프로그램의 진입점에 STAThreadAttribute 특성을 적용 합니다.
- **기본 스레딩 특성** - [/CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md)를 지정 하지 않는 것과 같습니다. CLR (공용 언어 런타임)에서 기본 스레딩 특성을 설정할 수 있도록 합니다.

### <a name="clr-image-type"></a>CLR 이미지 형식

CLR 이미지의 형식(IJW, 순수 또는 안전)을 설정합니다.

**Choices**

- **IJW 이미지 강제**
- **순수 IL 이미지 강제**
- **안전 IL 이미지 강제**
- **기본 이미지 형식**

### <a name="key-file"></a>키 파일

어셈블리에 서명할 키 또는 키 쌍을 지정 하십시오. ([/Keyfile](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md): filename)

### <a name="key-container"></a>키 컨테이너

어셈블리에 서명할 키 컨테이너를 지정 합니다. ([/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md): name)

### <a name="delay-sign"></a>서명 연기

어셈블리를 부분적으로 서명 합니다. 어셈블리에 공개 키를 저장 하려는 경우에만 [/delaysign](delaysign-partially-sign-an-assembly.md) 을 사용 합니다. 기본값은/DELAYSIGN: NO입니다.

### <a name="clr-unmanaged-code-check"></a>CLR 비관리 코드 검사

[/CLRUNMANAGEDCODECHECK](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md) 링커에서는 관리 코드에서 네이티브 dll로의 링커 생성 PInvoke 호출에 SuppressUnmanagedCodeSecurityAttribute를 적용할지 여부를 지정 합니다.

### <a name="error-reporting"></a>오류 보고

ICE(내부 컴파일러 오류) 정보를 Visual C++ 팀에 직접 제공할 수 있습니다.

**Choices**

- **PromptImmediately** -즉시 프롬프트를 표시 합니다.
- 다음 로그인 **에 대 한 큐를 대기** 합니다.
- **오류 보고서 보내기** -오류 보고서를 보냅니다.
- **오류 보고서 없음** -오류 보고서가 없습니다.

### <a name="sectionalignment"></a>SectionAlignment

[/Align](align-section-alignment.md) 옵션은 프로그램의 선형 주소 공간 내에서 각 섹션의 맞춤을 지정 합니다. Number 인수는 바이트 단위 이며 2의 거듭제곱 이어야 합니다.

### <a name="preserve-last-error-code-for-pinvoke-calls"></a>PInvoke 호출의 마지막 오류 코드 유지

기본적으로 설정 된 [/CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md)는 P/Invoke 메커니즘을 통해 호출 된 함수의 마지막 오류 코드를 유지 합니다 .이를 통해/clr을 사용 하 여 컴파일된 코드에서 dll의 네이티브 함수를 호출할 수 있습니다.

**Choices**

- **사용** -CLRSupportLastError를 사용 하도록 설정 합니다.
- **Disabled** -CLRSupportLastError를 사용 하지 않도록 설정 합니다.
- **시스템 Dll만** -시스템 dll에만 CLRSupportLastError을 사용 하도록 설정 합니다.

### <a name="image-has-safe-exception-handlers"></a>이미지에 안전한 예외 처리기 포함

[/Safeseh](safeseh-image-has-safe-exception-handlers.md) 를 지정 하는 경우 링커에서는 이미지의 안전한 예외 처리기 테이블을 생성할 수 있는 경우에만 이미지를 생성 합니다. 이 테이블은 운영 체제에서 이미지에 대해 유효한 예외 처리기를 지정 합니다.
