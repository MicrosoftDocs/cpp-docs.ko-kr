---
description: 자세히 알아보기:/STUB (MS-DOS 스텁 파일 이름)
title: /STUB(MS-DOS 스텁 파일 이름)
ms.date: 11/04/2016
f1_keywords:
- /stub
- VC.Project.VCLinkerTool.DosStub
helpviewer_keywords:
- Win32 [C++], attaching MS-DOS stub program
- STUB linker option
- MS-DOS stub file name linker option
- /STUB linker option
- Windows API [C++], attaching MS-DOS stub program
- -STUB linker option
ms.assetid: 65221ffe-4f9a-4a14-ac69-3cfb79b40b5f
ms.openlocfilehash: 34f3cd71ce66cb6695a58707fd84de79f7a14b1d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230304"
---
# <a name="stub-ms-dos-stub-file-name"></a>/STUB(MS-DOS 스텁 파일 이름)

```
/STUB:filename
```

## <a name="arguments"></a>인수

*filename*<br/>
MS-DOS 응용 프로그램입니다.

## <a name="remarks"></a>설명

/STUB 옵션은 MS-DOS 스텁 프로그램을 Win32 프로그램에 연결 합니다.

파일이 MS-DOS에서 실행 되는 경우 스텁 프로그램이 호출 됩니다. 일반적으로 적절 한 메시지를 표시 합니다. 그러나 유효한 모든 MS-DOS 응용 프로그램은 스텁 프로그램 일 수 있습니다.

스텁 프로그램의 *파일 이름을* 콜론 뒤에 지정 합니다 (:) 명령줄에서 링커는 파일 *이름을* 확인 하 고 파일이 실행 파일이 아닌 경우 오류 메시지를 발행 합니다. 프로그램은 .exe 파일 이어야 합니다. .com 파일은 스텁 프로그램에 사용할 수 없습니다.

이 옵션을 사용 하지 않으면 링커가 다음 메시지를 발급 하는 기본 스텁 프로그램을 연결 합니다.

```
This program cannot be run in MS-DOS mode.
```

가상 장치 드라이버를 빌드할 때 *파일* 이름을 사용 하면 사용자가 WINNT에 정의 된 IMAGE_DOS_HEADER 구조를 포함 하는 파일 이름을 지정할 수 있습니다. H)를 사용 하 여 기본 헤더가 아니라 VXD에서 사용할 수 있습니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **명령줄** 속성 페이지를 클릭합니다.

1. **추가 옵션** 상자에 옵션을 입력 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
