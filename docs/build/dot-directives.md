---
title: 점 지시문
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, dot directives
- dot directives in NMAKE
ms.assetid: ab35da65-30b6-48b7-87d6-61503d7faf9f
ms.openlocfilehash: 18688afedfe076ea2e4485471ffbe92dc2e09a2d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542872"
---
# <a name="dot-directives"></a>점 지시문

줄의 시작 부분에 대 한 설명 블록 외부 점 지시문을 지정 합니다. 점 지시문 마침표로 시작 (합니다. ) 고 뒤에 콜론 (:). 공백 및 탭 허용 됩니다. 점 지시문 이름은 대/소문자 및 대문자입니다.

|지시문|용도|
|---------------|-------------|
|**. 무시:**|메이크파일의 끝에 지정 된 위치에서 명령에 의해 반환 되는 0이 아닌 종료 코드를 무시 합니다. 기본적으로 NMAKE 명령을 0이 아닌 종료 코드를 반환 하는 경우 중지 됩니다. 오류 검사를 복원 하려면 사용 하 여 **! CMDSWITCHES**합니다. 단일 명령에 대 한 종료 코드를 무시 하려면 대시 (-) 한정자를 사용 합니다. 전체 파일에 대 한 종료 코드를 무시 하려면 사용 하 여 / I.|
|**. : 귀중** *대상*|유지 *대상* 디스크에서 업데이트 하는 명령을 중단은; 영향을 주지 않습니다 명령 파일을 삭제 하 여 인터럽트를 처리 하는 경우. 하나 이상의 공백이 나 탭을 사용 하 여 대상 이름을 구분 합니다. 기본적으로 NMAKE 빌드 중단 되는 경우 CTRL + C 또는 CTRL + BREAK 대상을 삭제 합니다. 각 사용 **합니다. 귀중 한** 전체 메이크파일; 적용할 여러 사양은 누적 합니다.|
|**. 자동:**|메이크파일의 끝에 지정 된 위치에서 실행 된 명령 표시를 하지 않습니다. 기본적으로 NMAKE 명령을 호출을 표시 합니다. 에코를 복원 하려면 사용 하 여 **! CMDSWITCHES**합니다. 단일 명령을 에코를 표시 하지 않으려면 사용 합니다 **@** 한정자입니다. 파일의 전체 에코를 표시 하지 않으려면 사용/s.|
|**. 접미사:** `list`|유추 규칙 일치;에 대 한 확장 나열 다음 확장을 포함 하는 미리 정의 된:.exe.obj.asm.c.cpp.cxx.bas.cbl 자세한.pas.res.rc.f.f90|

변경 된 **합니다. 접미사** 목록 순서 또는 새 목록을 지정 하 여 목록을 지우고 새 설정을 지정 합니다. 목록을 지우려면 콜론 없는 확장을 지정 합니다.

```
.SUFFIXES :
```

목록의 끝에 추가 접미사를 추가 하려면 지정

```
.SUFFIXES : suffixlist
```

여기서 *suffixlist* 은 목록 하나 이상의 공백이 나 탭으로 구분 된 추가 된 접미사입니다. 현재 설정을 확인 하려면 **합니다. 접미사**를 사용 하십시오.를 사용 하 여 NMAKE 실행

## <a name="see-also"></a>참고 항목

[NMAKE 참조](../build/nmake-reference.md)