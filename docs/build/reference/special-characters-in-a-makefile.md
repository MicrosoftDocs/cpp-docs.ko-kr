---
description: '자세한 정보: 메이크파일의 특수 문자'
title: 메이크파일의 특수 문자
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, special characters
- makefiles, special characters
- special characters, in NMAKE macros
- macros, special characters
ms.assetid: 92c34ab5-ca6b-4fc0-bcf4-3172eaeda9f0
ms.openlocfilehash: 22b8f6dd82191c88a23eaf1dabb551d468293a42
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224675"
---
# <a name="special-characters-in-a-makefile"></a>메이크파일의 특수 문자

NMAKE 특수 문자를 리터럴 문자로 사용 하려면 앞에 캐럿 (^)을 추가 합니다. NMAKE는 다른 문자 앞에 오는 캐럿를 무시 합니다. 특수 문자는 다음과 같습니다.

`:  ;  #  (  )  $  ^  \  {  }  !  @  —`

따옴표 붙은 문자열 내의 캐럿 (^)은 리터럴 캐럿 문자로 처리 됩니다. 줄의 끝에 있는 캐럿은 문자열 또는 매크로에 리터럴 줄 바꿈 문자를 삽입 합니다.

매크로에서 \\ 줄 바꿈 문자가 뒤에 오는 백슬래시 ()가 공백으로 바뀝니다.

명령에 백분율 기호 (%)가 있습니다. 는 파일 지정자입니다. 명령 에서% 문자 그대로 표시 하려면 이중 백분율 기호 (%%)를 지정 합니다. 단일 항목 대신. 다른 경우 NMAKE는 단일%를 그대로 해석 하지만 항상 double%%를 단일%로 해석 합니다. 따라서 리터럴%%를 나타내려면 3% 기호,%%% 또는 4% 기호 (%%%%)를 지정 합니다.

명령에서 달러 기호 ($)를 리터럴 문자로 사용 하려면 두 개의 달러 기호 ($ $)를 지정 합니다. 이 메서드는 ^ $가 작동 하는 다른 경우에도 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[메이크파일의 내용](contents-of-a-makefile.md)
