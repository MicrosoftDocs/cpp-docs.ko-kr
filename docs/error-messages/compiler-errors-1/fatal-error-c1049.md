---
title: 심각한 오류 C1049
description: 컴파일러 심각한 오류 C1049 및 잘못 된 숫자 인수에 대해 설명 하 고이를 해결 하는 방법을 설명 합니다.
ms.date: 11/04/2019
f1_keywords:
- C1049
helpviewer_keywords:
- C1049
ms.openlocfilehash: 9b3cbe5d081e32680e5408fc4a6ddcd932db77a2
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503269"
---
# <a name="fatal-error-c1049"></a>심각한 오류 C1049

> '*value*' 숫자 인수가 잘못되었습니다.

CL.EXE 명령줄 파서가 숫자 인수를 기대 하는 *값* 을 발견 했습니다.

컴파일러가 다음 컴파일러 옵션 중 하나에 대 한 숫자 인수를 찾을 수 없는 경우 C1049 오류가 발생할 수 있습니다.

[/cerx: depth](../../build/reference/constexpr-control-constexpr-evaluation.md)\
[/constexpr: backtrace](../../build/reference/constexpr-control-constexpr-evaluation.md)\
[/cers: 단계](../../build/reference/constexpr-control-constexpr-evaluation.md)

숫자 인수를 필요로 하는 명령줄 컴파일러 옵션은,,, 또는를 보고할 수도 있습니다 `Command line error D8004` `Command line error D8021` `Command line warning D9002` `Command line warning D9014` `Command line warning D9024` .

이 오류를 해결 하려면 명령 줄에서 위치가 잘못 되었거나 누락 된 인수를 확인 합니다. 옵션과 인수 사이에 예기치 않은 공백이 없는지 확인 합니다. 매크로, 환경 변수 또는 기타 빌드 시스템 작업을 통해 최종 명령줄이 생성 될 수 있습니다. 따라서 컴파일러에 전달 되는 실제 명령줄을 확인 하는 것이 중요 합니다.

- 명령 파일 또는 메이크파일에서 **echo** 명령을 사용 하 여 실제 명령줄을 보고할 수 있습니다.

- Visual Studio에서 프로젝트의 **속성 페이지** 대화 상자를 엽니다. **구성 속성**  >  **C/c + +**  >  **일반** 페이지에서 **시작 배너 표시 안 함** 속성을 **아니요**로 변경 합니다. **확인**을 선택하여 변경 내용을 저장합니다. 이제 **출력** 창에는 빌드하는 동안 저작권 줄 바로 뒤에 명령줄이 표시 됩니다.

다른 빌드 시스템에는 사용 되는 실제 명령을 볼 수 있는 로그 파일 또는 자세한 정보 옵션이 있을 수 있습니다. 자세한 내용은 빌드 시스템 설명서를 참조 하세요.
