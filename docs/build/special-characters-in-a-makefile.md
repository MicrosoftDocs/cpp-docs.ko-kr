---
title: 메이크파일의 특수 문자
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, special characters
- makefiles, special characters
- special characters, in NMAKE macros
- macros, special characters
ms.assetid: 92c34ab5-ca6b-4fc0-bcf4-3172eaeda9f0
ms.openlocfilehash: e2703adbbdba392b1a317e2656c6f3dba30a36b6
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420760"
---
# <a name="special-characters-in-a-makefile"></a>메이크파일의 특수 문자

NMAKE 특수 문자를 리터럴 문자로 사용 하려면 앞에 캐럿 (^)를 배치 합니다. NMAKE 다른 문자 앞에 있는 캐럿을 무시 합니다. 특수 문자는 다음과 같습니다.

`:  ;  #  (  )  $  ^  \  {  }  !  @  —`

따옴표 붙은 문자열 안에 캐럿 (^)는 캐럿 리터럴 문자로 처리 됩니다. 줄의 끝에 캐럿 매크로 문자열에 리터럴 줄 바꿈 문자를 삽입합니다.

매크로, 백슬래시 (\\) 뒤에 줄 바꿈으로 문자가 공백으로 바뀝니다.

명령에서 백분율 기호 (%) 이 파일 지정자입니다. % 명령에 문자 그대로 나타내기 위해 두 개의 백분율 기호 (%)를 지정 합니다. 대신 단일 합니다. NMAKE 다른 상황에서는 단일 % 문자 그대로 해석 하지만 항상 double 값을 해석 % % 단일 %로 합니다. 따라서 리터럴을 나타내는 % %, 하거나 세 백분율 기호를 지정 합니다. %%%, 또는 네 개의 백분율 기호를 %%%.

명령에서 리터럴 문자로 달러 기호 ($)를 사용 하려면 두 개의 달러 기호 ($$)를 지정 합니다. 다른 상황에서는이 방법을 사용할 수도 있습니다는 ^ $ 작동 합니다.

## <a name="see-also"></a>참고자료

[메이크파일의 내용](../build/contents-of-a-makefile.md)
