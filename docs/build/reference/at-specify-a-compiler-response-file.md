---
title: '@ (컴파일러 지시 파일 지정) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '@'
dev_langs:
- C++
helpviewer_keywords:
- response files, C/C++ compiler
- '@ compiler option'
- cl.exe compiler, specifying response files
ms.assetid: 400fffee-909d-4f60-bf76-45833e822685
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 430e6372c1ca26e946c2ff26bfcfe9180dfb0dba
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894461"
---
# <a name="-specify-a-compiler-response-file"></a>@(컴파일러 지시 파일 지정)

컴파일러 지시 파일을 지정합니다.

## <a name="syntax"></a>구문

> **\@**<em>response_file</em>

## <a name="arguments"></a>인수

*response_file*  
컴파일러 명령을 포함 하는 텍스트 파일입니다.

## <a name="remarks"></a>설명

지시 파일이 명령줄에서 지정할 수 있는 모든 명령을 포함할 수 있습니다. 이 파일은 명령줄 인수가 127자를 초과할 경우에 유용할 수 있습니다.

지정 불가능 합니다 **\@** 지시 파일 내에서 옵션입니다. 즉, 응답 파일을 다른 지시 파일을 포함할 수 없습니다.

명령줄에서 많은 지시 파일 옵션을 지정할 수 있습니다 (예를 들어 `@respfile.1 @respfile.2`) 원하는 만큼 합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

- 응답 파일을 개발 환경 내에서 지정할 수 없습니다 하 고 명령줄에서 지정 해야 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- 이 컴파일러 옵션을 프로그래밍 방식으로 변경할 수 없습니다.

## <a name="see-also"></a>참고 항목

[컴파일러 옵션](../../build/reference/compiler-options.md)  
[컴파일러 옵션 설정](../../build/reference/setting-compiler-options.md)  
