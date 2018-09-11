---
title: NMAKE 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, options
ms.assetid: 00ba1aec-ef27-44cf-8d82-c5c095e45bae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89f71bff1d8f64da2ad029e300fe2427235eac0a
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894527"
---
# <a name="nmake-options"></a>NMAKE 옵션

NMAKE 옵션은 다음 표에 설명 되어 있습니다. 옵션 대시 (-) 또는 슬래시 (/)가 앞에 오고 대/소문자 구분 하지 않습니다. 사용 하 여 [! CMDSWITCHES](../build/makefile-preprocessing-directives.md) Tools.ini 또는 메이크파일의 옵션 설정을 변경 합니다.

|옵션|용도|
|------------|-------------|
|/ A|종속 항목에 대해 오래 되지 않은 경우에 모든 계산된 대상에 빌드. 관련 없는 대상의 빌드를 강제 적용 되지 않습니다.|
|/ B|타임 스탬프가 같은 경우에 빌드합니다. 매우 빠르게 시스템 (해결 방법 2 초 이하의)에 권장 합니다.|
|/C|심각 하지 않은 NMAKE 오류 또는 경고, 타임 스탬프 및 NMAKE 저작권 메시지를 비롯 한 기본을 출력을 표시 하지 않습니다. /K.에서 발생 된 경고를 표시 하지 않습니다.|
|/D|각각의 타임 스탬프를 표시 합니다. 대상이 존재 하지 않을 경우 대상 및 종속 및 메시지를 평가 합니다. 메이크파일 디버깅에 대 한/P를 사용 하 여 유용 합니다. 사용 하 여 **! CMDSWITCHES** 설정 또는 /D 메이크파일의 부분에 대 한 선택을 취소 합니다.|
|/E|메이크파일 매크로 정의 재정의 하도록 환경 변수를 하면 됩니다.|
|/ERRORREPORT [NONE &AMP;#124; 프롬프트 &AMP;#124; 큐 &AMP;#124; 송신]|Nmake.exe 런타임에 실패 하는 경우 이러한 내부 오류에 대 한 정보가 Microsoft로 보낼 /ERRORREPORT를 사용할 수 있습니다.<br /><br /> /ERRORREPORT에 대 한 자세한 내용은 참조 하세요. [/errorReport (내부 컴파일러 오류 보고)](../build/reference/errorreport-report-internal-compiler-errors.md)합니다.|
|/F *파일 이름*|지정 *filename* 메이크파일을으로 합니다. 공백 또는 탭 앞 *filename*합니다. 각 메이크파일 /F를 한 번만 지정 합니다. 표준 입력에서 메이크파일을 제공 하려면 대시 (-)를 지정 *filename*, F6 또는 CTRL + Z를 사용 하 여 키보드 입력을 종료 하 고 있습니다.|
|/G|포함 된 메이크파일을 표시 합니다. 지시문을 포함 합니다.  참조 [메이크파일 전처리 지시문](../build/makefile-preprocessing-directives.md) 자세한 내용은 합니다.|
|/HELP, /?|NMAKE 명령줄 구문의 간단한 요약을 표시합니다.|
|/I|모든 명령에서 종료 코드를 무시합니다. 을 설정 하거나 /I 메이크파일의 부분에 대 한 선택을 취소 하려면 사용 하 여 **! CMDSWITCHES**합니다. 메이크파일의 부분에 대 한 종료 코드를 무시 하려면 대시 (-) 명령 한정자를 사용 하거나 [합니다. 무시](../build/dot-directives.md)합니다. 둘 다 지정 하는 경우 /K을 재정의 합니다.|
|/K|명령이 오류를 반환 하는 경우 관련 되지 않은 종속성 빌드를 계속 합니다. 또한 경고가 발생 하 고 1의 종료 코드를 반환 합니다. NMAKE에는 기본적으로 모든 명령이 0이 아닌 종료 코드를 반환 하면 중지 됩니다. /C; 여 /K에서 발생 한 경고는 표시 되지 않습니다. /I 둘 다 지정 /K을 재정의 합니다.|
|/N|표시 되지만; 명령을 실행 하지 않습니다. 전처리 명령이 실행 됩니다. 재귀 NMAKE 호출에서 명령을 표시 하지 않습니다. 메이크파일 디버깅 및 타임 스탬프를 확인 하는 데 유용 합니다. 을 설정 하거나 일부 메이크파일의 /N을 선택을 취소 하려면 사용 하 여 **! CMDSWITCHES**합니다.|
|/NOLOGO|NMAKE 저작권 메시지를 표시 하지 않습니다.|
|/P|정보가 표시 됩니다 (매크로 정의 유추 규칙 대상 [합니다. 접미사가](../build/dot-directives.md) 목록)을 표준 출력에 다음 빌드를 실행 합니다. 명령줄 대상 없거나 메이크파일 있으면 정보만 표시 됩니다. /D 메이크파일을 디버깅을 사용 합니다.|
|/Q|대상; 검사 타임 스탬프 빌드가 실행 되지 않습니다. 이 아닌 경우 모든 대상을 최신 상태로 유지 하는 경우 종료 코드 0을 하 고 0이 아닌 종료 코드를 반환 합니다. 전처리 명령이 실행 됩니다. NMAKE는 배치 파일에서 실행 하는 경우 유용 합니다.|
|/R|지웁니다는 **합니다. 접미사** 나열 하 고 유추 규칙 및 Tools.ini 파일에 정의 된 또는 미리 정의 된 매크로 무시 합니다.|
|/S|실행 된 명령 표시를 하지 않습니다. 메이크파일 일부를 표시 하지 않으려면 사용 합니다 **\@** 명령 한정자 또는 [합니다. 자동](../build/dot-directives.md)합니다. 을 설정 하거나 /S 메이크파일의 부분에 대 한 선택을 취소 하려면 사용 하 여 **! CMDSWITCHES**합니다.|
|/T|명령줄 대상 (또는 첫 번째 메이크파일 대상)의 타임 스탬프를 업데이트 하 고 전처리 명령을 실행 하지만 빌드를 실행 하지 않습니다.|
|/U|/N.와 함께 사용 해야 합니다. /N 출력 일괄 처리 파일로 사용할 수 있도록 인라인 NMAKE 파일을 덤프 합니다.|
|/X *파일 이름*|NMAKE 오류 출력을 보냅니다 *filename* 표준 오류 대신 합니다. 공백 또는 탭 앞 *filename*합니다. 오류 출력을 표준 출력으로 보내려면를 대시 (-)를 지정 *filename*합니다. 명령에서 표준 오류 출력을 주지 않습니다.|
|/Y|일괄 처리 모드 유추 규칙을 사용 하지 않도록 설정 합니다. 이 옵션을 선택 하면 모든 일괄 처리 모드 유추 규칙 일반 유추 규칙으로 처리 됩니다.|

## <a name="see-also"></a>참고 항목

[NMAKE 실행](../build/running-nmake.md)
