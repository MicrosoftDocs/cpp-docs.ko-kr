---
description: '자세히 알아보기: @ (컴파일러 지시 파일 지정)'
title: '@(컴파일러 지시 파일 지정)'
ms.date: 11/04/2016
f1_keywords:
- '@'
helpviewer_keywords:
- response files, C/C++ compiler
- '@ compiler option'
- cl.exe compiler, specifying response files
ms.assetid: 400fffee-909d-4f60-bf76-45833e822685
ms.openlocfilehash: bd2859f7973723d93594693902e92ac3530d73ff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182894"
---
# <a name="-specify-a-compiler-response-file"></a>@(컴파일러 지시 파일 지정)

컴파일러 지시 파일을 지정 합니다.

## <a name="syntax"></a>Syntax

> **\@**<em>response_file</em>

## <a name="arguments"></a>인수

*response_file*<br/>
컴파일러 명령을 포함 하는 텍스트 파일입니다.

## <a name="remarks"></a>설명

지시 파일은 명령줄에서 지정 하는 모든 명령을 포함할 수 있습니다. 이 파일은 명령줄 인수가 127자를 초과할 경우에 유용할 수 있습니다.

지시 파일에서 옵션을 지정할 수 없습니다 **\@** . 즉, 지시 파일은 다른 지시 파일을 포함할 수 없습니다.

명령줄에서 원하는 수 만큼의 지시 파일 옵션 (예:)을 지정할 수 있습니다 `@respfile.1 @respfile.2` .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

- 개발 환경에서 지시 파일을 지정할 수 없으며 명령줄에서 지정 해야 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- 이 컴파일러 옵션은 프로그래밍 방식으로 변경할 수 없습니다.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
