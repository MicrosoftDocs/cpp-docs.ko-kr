---
description: '자세한 정보: 메이크파일의 주석'
title: 메이크파일의 주석
ms.date: 11/04/2016
helpviewer_keywords:
- makefiles, comments
ms.assetid: 76fd9e3d-5966-47f4-a091-c9e80b232b49
ms.openlocfilehash: 9edee594c0299d8e93928c1284b7244af71f61e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182296"
---
# <a name="comments-in-a-makefile"></a>메이크파일의 주석

주석 앞에 숫자 기호 (#)를 붙입니다. NMAKE는 숫자 기호에서 다음 줄 바꿈 문자로의 텍스트를 무시 합니다. 예제:

```
# Comment on line by itself
OPTIONS = /MAP  # Comment on macro definition line

all.exe : one.obj two.obj  # Comment on dependency line
    link one.obj two.obj
# Comment in commands block
#   copy *.obj \objects  # Command turned into comment
    copy one.exe \release

.obj.exe:  # Comment on inference rule line
    link $<

my.exe : my.obj ; link my.obj  # Err: cannot comment this
# Error: # must be the first character
.obj.exe: ; link $<  # Error: cannot comment this
```

리터럴 숫자 기호를 지정 하려면 다음과 같이 캐럿 () 앞에와 야 합니다 **^** .

```
DEF = ^#define  #Macro for a C preprocessing directive
```

## <a name="see-also"></a>참고 항목

[메이크파일의 내용](contents-of-a-makefile.md)
