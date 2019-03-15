---
title: '@(컴파일러 지시 파일 지정)'
ms.date: 11/04/2016
f1_keywords:
- '@'
helpviewer_keywords:
- response files, C/C++ compiler
- '@ compiler option'
- cl.exe compiler, specifying response files
ms.assetid: 400fffee-909d-4f60-bf76-45833e822685
ms.openlocfilehash: c2b5578e1ce1db590bdf5abbff0c91e858803ad7
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808081"
---
# <a name="-specify-a-compiler-response-file"></a>@(컴파일러 지시 파일 지정)

컴파일러 지시 파일을 지정합니다.

## <a name="syntax"></a>구문

> **\@**<em>response_file</em>

## <a name="arguments"></a>인수

*response_file*<br/>
컴파일러 명령을 포함 하는 텍스트 파일입니다.

## <a name="remarks"></a>설명

지시 파일이 명령줄에서 지정할 수 있는 모든 명령을 포함할 수 있습니다. 이 파일은 명령줄 인수가 127자를 초과할 경우에 유용할 수 있습니다.

지정 불가능 합니다 **\@** 지시 파일 내에서 옵션입니다. 즉, 응답 파일을 다른 지시 파일을 포함할 수 없습니다.

명령줄에서 많은 지시 파일 옵션을 지정할 수 있습니다 (예를 들어 `@respfile.1 @respfile.2`) 원하는 만큼 합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

- 응답 파일을 개발 환경 내에서 지정할 수 없습니다 하 고 명령줄에서 지정 해야 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- 이 컴파일러 옵션을 프로그래밍 방식으로 변경할 수 없습니다.

## <a name="see-also"></a>참고자료

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 명령줄 구문](compiler-command-line-syntax.md)
