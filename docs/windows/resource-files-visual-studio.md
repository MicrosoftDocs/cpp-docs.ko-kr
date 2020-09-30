---
title: 리소스 파일(C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.resource
helpviewer_keywords:
- resources [C++]
- .rc files [C++]
- resource files [C++]
- resource script files [C++]
- resource script files [C++], Win-32 based applications
- resource script files [C++], files updated when editing resources
- resources [C++], types of resource files
- rct files [C++]
- rc files [C++]
- resource files [C++], types of
- .rct files [C++]
- resource script files [C++], unsupported types
- manifest resources [C++]
- resources [C++], manifest
- resources [C++], opening
- file types [C++], for resources
- resources [C++], editing
- files [C++], editable types
- resource editing
ms.assetid: 4d2b6fcc-07cf-4289-be87-83a60f69533c
ms.openlocfilehash: 463c27959b049436e29f872c966bc276c6ef5f2d
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507023"
---
# <a name="resource-files-c"></a>리소스 파일(C++)

> [!NOTE]
> 를 참조하세요. .NET 프로그래밍 언어의 프로젝트는 리소스 스크립트 파일을 사용하지 않으므로 **솔루션 탐색기**를 참조하세요. 관리 되는 프로젝트에서 리소스 파일로 작업 하려면 [이미지 편집기](../windows/image-editor-for-icons.md) 및 [바이너리 편집기](binary-editor.md) 를 사용 합니다.
>
> 편집할 관리되는 리소스는 연결된 리소스여야 합니다. Visual Studio 리소스 편집기에서는 포함된 리소스를 편집할 수 없습니다.

*리소스 파일* 이라는 용어는 다음과 같은 다양 한 파일 형식을 참조할 수 있습니다.

- 프로그램의 리소스 스크립트(.rc) 파일

- 리소스 템플릿(.rct) 파일

- 독립형 파일로 존재 하는 개별 리소스 이 형식에는 .rc 파일에서 참조 되는 비트맵, 아이콘 또는 커서 파일이 포함 됩니다.

- 개발 환경에서 생성 된 헤더 파일입니다. 이 형식에는 `Resource.h` .rc 파일에서 참조 되는이 포함 됩니다.

.Exe, .dll 및 .res 파일과 같은 다른 파일 형식에서 발견 된 리소스를 *리소스*라고 합니다.

프로젝트 내에서 *리소스 파일* 및 *리소스* 를 사용할 수 있습니다. 현재 프로젝트에 포함 되지 않거나 Visual Studio의 개발 환경 외부에서 만들어진 작업을 수행할 수도 있습니다. 예를 들어, 다음을 수행할 수 있습니다.

- 중첩되어 조건부로 포함된 리소스 파일에 대한 작업

- 기존 리소스를 업데이트 하거나 Visual C++로 변환 합니다.

- 현재 리소스 파일에서 그래픽 리소스 가져오기 또는 내보내기

- 개발 환경에서 수정할 수 없는 공유 또는 읽기 전용 식별자(기호) 포함

- 여러 프로젝트 간에 공유 리소스와 같이 편집이 필요 하지 않거나 편집 하지 않아도 되는 실행 파일 (.exe)의 리소스를 포함 합니다.

- 개발 환경에서 지원하지 않는 리소스 형식 포함

리소스에 대 한 자세한 내용은 [컴파일 시간에](../windows/how-to-include-resources-at-compile-time.md)리소스를 [만들고](../windows/how-to-create-a-resource-script-file.md) [리소스를 관리](../windows/how-to-copy-resources.md)하며 리소스를 포함 하는 방법을 참조 하세요.

## <a name="editable-resources"></a>편집 가능한 리소스

포함 된 리소스를 편집 하기 위해 열 수 있는 파일 형식은 다음과 같습니다.

| 파일 이름 | Description |
|---|---|
| .rc | 리소스 스크립트 파일 |
| .rct | 리소스 템플릿 파일 |
| .res | 리소스 파일 |
| .resx | 관리 되는 리소스 파일 |
| .exe | 실행 파일 |
| .dll | 동적 연결 라이브러리 파일 |
| .bmp, .ico, .dib, .cur | 비트맵, 아이콘, 도구 모음 및 커서 파일 |

리소스를 편집할 때 Visual Studio 환경은와 함께 작동 하며 다음 파일에 영향을 줍니다.

| 파일 이름 | Description |
|---|---|
| Resource.h | 기호 정의를 포함 하는 개발 환경에서 생성 된 헤더 파일입니다.<br/><br/>이 파일을 소스 제어에 포함 합니다. |
| Filename.aps | 빠른 로드에 사용 되는 현재 리소스 스크립트 파일의 이진 버전입니다.<br /><br /> 리소스 편집기는 .rc 또는 resource.h 파일을 직접 읽을 필요가 없습니다. 리소스 컴파일러는 리소스 편집기에서 사용 하는. p a x 파일로 컴파일합니다. 이 파일은 컴파일 단계이며 기호화된 데이터만 저장합니다.<br/><br/>일반적인 컴파일 프로세스와 마찬가지로 주석 달기와 같이 기호화 되지 않은 정보는 컴파일 프로세스 중에 삭제 됩니다.<br/><br/>. P a c 파일이 .rc 파일과 동기화 되지 않을 때마다 .rc 파일이 다시 생성 됩니다. 예를 들어를 **저장**하면 리소스 편집기에서 .rc 파일 및 resource.h 파일을 덮어씁니다. 리소스 자체에 대 한 모든 변경 내용은 .rc 파일에 통합 된 상태로 유지 되지만, .rc 파일을 덮어쓰면 주석이 항상 손실 됩니다. 주석을 유지 하는 방법에 대 한 자세한 내용은 [컴파일 타임에 리소스 포함](../windows/how-to-include-resources-at-compile-time.md)을 참조 하세요.<br/><br/>일반적으로 소스 제어에는 aps 파일을 포함 하면 안 됩니다. |
| .rc | 현재 프로젝트의 리소스에 대한 스크립트가 포함된 리소스 스크립트 파일입니다. 저장할 때마다 .aps 파일이 이 파일을 덮어씁니다.<br/><br/>이 파일을 소스 제어에 포함 합니다. |

## <a name="manifest-resources"></a>매니페스트 리소스

C + + 데스크톱 프로젝트에서 매니페스트 리소스는 응용 프로그램에서 사용 하는 종속성을 설명 하는 XML 파일입니다. 예를 들어 Visual Studio에서이 MFC 마법사 생성 매니페스트 파일은 응용 프로그램에서 사용 해야 하는 Windows 공용 컨트롤 Dll 버전을 정의 합니다.

```xml
<description>Your app description here</description>
<dependency>
    <dependentAssembly>
        <assemblyIdentity
            type="win32"
            name="Microsoft.Windows.Common-Controls"
            version="6.0.0.0"
            processorArchitecture="X86"
            publicKeyToken="6595b64144ccf1df"
            language="*"
        />
    </dependentAssembly>
</dependency>
```

Windows XP 또는 Windows Vista 응용 프로그램의 경우 매니페스트 리소스는 응용 프로그램에서 사용할 최신 버전의 Windows 공용 컨트롤을 지정 해야 합니다. 위의 예제에서는 `6.0.0.0` [syslink 컨트롤](/windows/win32/Controls/syslink-overview)을 지 원하는 버전을 사용 합니다.

> [!NOTE]
> 모듈별로 매니페스트 리소스를 하나만 사용할 수 있습니다.

매니페스트 리소스에 포함 된 버전 및 형식 정보를 보려면 XML 뷰어 또는 Visual Studio 텍스트 편집기에서 파일을 엽니다. [리소스 뷰](./how-to-create-a-resource-script-file.md)에서 매니페스트 리소스를 열면 리소스가 이진 형식으로 열립니다.

### <a name="to-open-a-manifest-resource"></a>매니페스트 리소스를 열려면

1. Visual Studio에서 프로젝트를 열고 **솔루션 탐색기**로 이동 합니다.

1. **리소스 파일** 폴더를 확장 하 고 다음을 수행 합니다.

   - 텍스트 편집기에서 열려면 *.manifest* 파일을 두 번 클릭 합니다.

   - 다른 편집기에서 열려면 *.manifest* 파일을 마우스 오른쪽 단추로 클릭 하 고 **연결 프로그램**을 선택 합니다. 사용할 편집기를 지정 하 고 **열기**를 선택 합니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[리소스 파일 작업](../windows/working-with-resource-files.md)<br/>
[리소스 식별자 (기호)](../windows/symbols-resource-identifiers.md)<br/>
[리소스 편집기](../windows/resource-editors.md)<br/>
