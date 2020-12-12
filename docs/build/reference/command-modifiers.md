---
description: '자세한 정보: 명령 한정자'
title: 명령 한정자
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, command modifiers
- command modifiers
ms.assetid: b661c432-210f-4f05-bc56-744a46e0fc0b
ms.openlocfilehash: d17d5f25719dfe5638ca6688105517d385bdf68e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182374"
---
# <a name="command-modifiers"></a>명령 한정자

명령 앞에 하나 이상의 명령 한정자를 지정 하 고 필요에 따라 공백이 나 탭으로 구분할 수 있습니다. 명령과 마찬가지로 한정자는 들여쓰기 되어야 합니다.

|한정자|목적|
|--------------|-------------|
|\@*명령*|명령의 표시를 방지 합니다. 명령으로 표시는 표시 되지 않습니다. 기본적으로 NMAKE는 실행 된 모든 명령을 에코 합니다. /S를 사용 하 여 전체 메이크파일의 표시를 표시 하지 않습니다. **를 사용 합니다.** 메이크파일의 일부가 표시 되지 않도록 하는 자동입니다.|
|**-**\[*number*] *명령*|*명령* 에 대 한 오류 검사를 끕니다. 기본적으로 명령에서 0이 아닌 종료 코드를 반환 하면 NMAKE가 중단 됩니다. -*Number* 를 사용 하는 경우 종료 코드가 *number* 를 초과 하면 NMAKE가 중지 됩니다. 대시와 숫자 사이에 공백이 나 탭을 표시할 수 없습니다 *.* 및 명령 사이에 하나 이상의 공백이 나 탭이 표시 되어야 합니다 `number` .  /I를 사용 하 여 전체 메이크파일의 오류 검사를 해제 합니다. **를 사용 합니다.** 메이크파일의 일부에 대 한 오류 검사를 해제 하려면 무시 합니다.|
|**!** *command*|*명령이*  <strong>$\*\*</strong> (종속성의 모든 종속 파일) 또는 **$?** 를 사용 하는 경우 각 종속 파일에 대해 명령을 실행 합니다. (대상 보다 늦은 타임 스탬프를 사용 하는 종속성의 모든 종속 파일).|

## <a name="see-also"></a>참고 항목

[메이크파일의 명령](commands-in-a-makefile.md)
