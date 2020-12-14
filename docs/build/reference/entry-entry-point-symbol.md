---
description: 자세히 알아보기:/ENTRY (진입점 기호)
title: /ENTRY(진입점 기호)
ms.date: 11/04/2016
f1_keywords:
- /entry
- VC.Project.VCLinkerTool.EntryPointSymbol
helpviewer_keywords:
- starting address
- -ENTRY linker option
- /ENTRY linker option
- ENTRY linker option
ms.assetid: 26c62ba2-4f52-4882-a7bd-7046a0abf445
ms.openlocfilehash: e4966ef44922a3a90d5abb5a7ac23460d4155f92
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201016"
---
# <a name="entry-entry-point-symbol"></a>/ENTRY(진입점 기호)

```
/ENTRY:function
```

## <a name="arguments"></a>인수

*function*<br/>
.Exe 파일 또는 DLL에 대 한 사용자 정의 시작 주소를 지정 하는 함수입니다.

## <a name="remarks"></a>설명

/ENTRY 옵션은 진입점 함수를 .exe 파일이 나 DLL의 시작 주소로 지정 합니다.

호출 규칙을 사용 하려면 함수를 정의 해야 합니다 **`__stdcall`** . 매개 변수와 반환 값은 프로그램이 콘솔 응용 프로그램, windows 응용 프로그램 또는 DLL 인지에 따라 달라 집니다. 링커가 진입점을 설정 하 여 C 런타임 라이브러리가 올바르게 초기화 되 고 정적 개체에 대 한 c + + 생성자가 실행 되도록 하는 것이 좋습니다.

기본적으로 시작 주소는 C 런타임 라이브러리의 함수 이름입니다. 링커는 다음 표에 나와 있는 것 처럼 프로그램의 특성에 따라이를 선택 합니다.

|함수 이름|기본|
|-------------------|-----------------|
|**mainCRTStartup** (또는 **wmainCRTStartup**)|/SUBSYSTEM: CONSOLE;를 사용 하는 응용 프로그램 호출 `main` (또는 `wmain` )|
|**WinMainCRTStartup** (또는 **wWinMainCRTStartup**)|/SUBSYSTEM:**WINDOWS**;를 사용 하는 응용 프로그램 `WinMain` `wWinMain` 를 사용 하도록 정의 해야 하는 (또는)를 호출 합니다. **`__stdcall`**|
|**_DllMainCRTStartup**|DLL, `DllMain` 가 있는 경우를 호출 합니다 .이 경우에는를 사용 하도록 정의 해야 합니다. **`__stdcall`**|

[/Dll](dll-build-a-dll.md) 또는 [/SUBSYSTEM](subsystem-specify-subsystem.md) 옵션을 지정 하지 않으면 링커가 정의 되었는지 여부에 따라 하위 시스템 및 진입점을 선택 `main` `WinMain` 합니다.

`main`, 및 함수는 `WinMain` `DllMain` 사용자 정의 진입점의 세 가지 형태입니다.

관리 되는 이미지를 만들 때/ENTRY에 지정 된 함수에는 (LPVOID *var1*, DWORD *var2*, LPVOID *var3*)의 서명이 있어야 합니다.

진입점을 정의 하는 방법에 대 한 자세한 내용은 `DllMain` [dll 및 Visual C++ 런타임 라이브러리 동작](../run-time-library-behavior.md) 을 참조 하세요.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **고급** 속성 페이지를 클릭 합니다.

1. **진입점** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EntryPointSymbol%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
