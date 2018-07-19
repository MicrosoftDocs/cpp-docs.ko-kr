---
title: -J (부호 형식은 기본 문자) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.DefaultCharIsUnsigned
- VC.Project.VCCLWCECompilerTool.DefaultCharIsUnsigned
- /j
dev_langs:
- C++
helpviewer_keywords:
- defaults, char type
- char data type
- -J compiler option [C++]
- /J compiler option [C++]
- J compiler option [C++]
- default char type is unsigned
ms.assetid: 50973667-6638-491e-9c41-bff73acae19f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a93172296b0e2e6d54dc428ffc62812ad979b160
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374468"
---
# <a name="j-default-char-type-is-unsigned"></a>/J(부호 없는 기본 문자 형식)
기본 `char` 형식을 `signed char`에서 `unsigned char`로 변경하고, `char` 형식은 `int` 형식으로 확장될 때 제로 확장됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
/J  
```  
  
## <a name="remarks"></a>설명  
 경우는 `char` 값으로 명시적 선언 된 `signed`, **/J** 옵션은, 및 때 값이 부호 확장 확장 되는 `int` 유형입니다.  
  
 **/J** 옵션 정의 `_CHAR_UNSIGNED`,으로 사용 되는 `#ifndef` LIMITS.h 파일의 기본 범위를 정의에 `char` 유형입니다.  
  
 ANSI C 전처리기와 c + +의 특정 구현 필요 하지 않습니다는 `char` 유형입니다. 이 옵션은 영어 이외의 언어로 번역 될 결국 문자 데이터를 사용 하 여 작업할 때 유용 합니다.  
  
> [!NOTE]
>  ATL/MFC에 이 컴파일러 옵션을 사용하면 오류가 생성될 수 있습니다. `_ATL_ALLOW_CHAR_UNSIGNED`를 정의해서 이 오류를 비활성화할 수도 있지만 이 해결 방법은 지원되지 않으며, 항상 작동하지 않을 수도 있습니다.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면  
  
1.  **솔루션 탐색기**에서 프로젝트의 바로 가기 메뉴를 열고 **속성**을 선택합니다.  
  
2.  프로젝트에서 **속성 페이지** 아래 왼쪽된 창에서 대화 상자에서 **구성 속성**를 확장 하 고 **C/c + +** 선택한 후 **명령줄**.  
  
3.  에 **추가 옵션** 창에서 지정 된 **/J** 컴파일러 옵션입니다.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면  
  
-   <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [컴파일러 옵션](../../build/reference/compiler-options.md)   
 [컴파일러 옵션 설정](../../build/reference/setting-compiler-options.md)   
 [프로젝트 속성 사용](../../ide/working-with-project-properties.md)