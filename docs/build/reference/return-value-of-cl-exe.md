---
description: '자세한 정보: cl.exe 반환 값'
title: cl.exe의 반환 값
ms.date: 09/05/2018
helpviewer_keywords:
- cl.exe compiler, return value
ms.assetid: 7c2d7f33-ee0d-4199-8ef4-75fe2b007670
ms.openlocfilehash: 2d324488e0d83979824d1b0c9244070c974e65af
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225091"
---
# <a name="return-value-of-clexe"></a>cl.exe의 반환 값

성공한 경우(오류가 없는 경우) cl.exe는 0을 반환하고 그렇지 않은 경우 0이 아닌 값을 반환합니다.

cl.exe의 반환 값은 스크립트, powershell, .cmd 또는 .bat 파일에서 컴파일하는 경우 유용할 수 있습니다. 오류나 경고가 발생할 경우 해결할 수 있도록 이 경우에도 컴파일러의 출력을 캡처하기 위한 계획을 세우는 것이 좋습니다.

가능한 오류 종료 코드가 너무 많아 cl.exe가 모두 나열할 수 없습니다. % ProgramFiles (x86)% \ Windows 키트 \\ <em>버전</em>\Include\shared\ 디렉터리에서 Windows 소프트웨어 개발 키트에 포함 된 winerror.h 또는 ntstatus 파일의 오류 코드를 조회할 수 있습니다. 10진수로 반환된 오류 코드는 검색을 위해 16진수로 변환해야 합니다. 예를 들어 오류 코드 -1073741620를 16진수로 변환하면 0xC00000CC입니다. 이 오류는 ntstatus.h에서 찾을 수 있는데, 여기에서 해당 메시지는 "원격 서버에서 지정된 공유 이름을 찾을 수 없습니다."입니다. 다운로드 가능한 Windows 오류 코드 목록은 [&#91;MS-ERREF&#93;: Windows 오류 코드](/openspecs/windows_protocols/MS-ERREF)를 참조 하세요.

Visual Studio의 오류 조회 유틸리티를 사용하여 컴파일러 오류 메시지의 의미를 찾을 수도 있습니다. Visual Studio 명령 셸에서 **errlook.exe** 를 입력 하 여 유틸리티를 시작 합니다. 또는 Visual Studio IDE의 메뉴 모음에서 **도구**, **오류 조회** 를 선택 합니다. 오류와 연결된 설명 텍스트를 찾으려면 오류 값을 입력합니다. 자세한 내용은 [ERRLOOK 참조](errlook-reference.md)를 참조 하세요.

## <a name="remarks"></a>설명

아래의 예제 .bat 파일에서는 cl.exe의 반환 값을 사용합니다.

```cmd
echo off
cl /W4 t.cpp
@if ERRORLEVEL == 0 (
   goto good
)

@if ERRORLEVEL != 0 (
   goto bad
)

:good
   echo "clean compile"
   echo %ERRORLEVEL%
   goto end

:bad
   echo "error or warning"
   echo %ERRORLEVEL%
   goto end

:end
```

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
