---
description: '자세한 정보: 콘솔 및 포트 i/o'
title: 콘솔 및 포트 I/O
ms.date: 11/04/2016
helpviewer_keywords:
- routines, console and port I/O
- routines
- ports, I/O routines
- I/O [CRT], console
- I/O [CRT], port
- I/O routines, console and port I/O
ms.assetid: 0eee1c92-9b3d-41e0-a43a-257e546eeec8
ms.openlocfilehash: 99419db614d4b4493f0fc5de3febb522c8bbb3dd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195790"
---
# <a name="console-and-port-io"></a>콘솔 및 포트 I/O

이러한 루틴은 콘솔 또는 지정된 포트에서 읽고 씁니다. 콘솔 I/O 루틴은 스트림 I/O 또는 하위 수준 I/O 라이브러리 루틴과 호환되지 않습니다. I/O가 수행되기 전에 콘솔 또는 포트를 열거나 닫지 않아야 합니다. 따라서 이 범주에 열기 또는 닫기 루틴이 없습니다. Windows 운영 체제에서 이러한 함수의 출력은 항상 콘솔로 보내지고 리디렉션될 수 없습니다.

## <a name="console-and-port-io-routines"></a>콘솔 및 포트 I/O 루틴

|루틴에서 반환된 값|기능|
|-------------|---------|
|[_cgets, _cgetws](../c-runtime-library/cgets-cgetws.md), [_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|콘솔에서 문자열을 읽습니다.|
|[_cprintf, _cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md), [_cprintf_s, _cprintf_s_l, _cwprintf_s, _cwprintf_s_l](../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)|형식이 지정된 데이터를 콘솔에 씁니다.|
|[_cputs](../c-runtime-library/reference/cputs-cputws.md)|문자열을 콘솔에 씁니다.|
|[_cscanf, _cwscanf](../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md), [_cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l](../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)|콘솔에서 형식이 지정된 데이터를 읽습니다.|
|[_getch, _getwch](../c-runtime-library/reference/getch-getwch.md)|콘솔에서 문자를 읽습니다.|
|[_getche, _getwche](../c-runtime-library/reference/getch-getwch.md)|콘솔에서 문자를 읽고 표시합니다.|
|[_inp](../c-runtime-library/inp-inpw-inpd.md)|지정된 I/O 포트에서 1바이트를 읽습니다.|
|[_inpd](../c-runtime-library/inp-inpw-inpd.md)|지정된 I/O 포트에서 2배 워드를 읽습니다.|
|[_inpw](../c-runtime-library/inp-inpw-inpd.md)|지정된 I/O 포트에서 2바이트 워드를 읽습니다.|
|[_kbhit](../c-runtime-library/reference/kbhit.md)|콘솔에서 키 입력을 확인하고 콘솔에서 읽기를 시도하기 전에 사용합니다.|
|[_outp](../c-runtime-library/outp-outpw-outpd.md)|1바이트를 지정된 I/O 포트에 씁니다.|
|[_outpd](../c-runtime-library/outp-outpw-outpd.md)|2배 워드를 지정된 I/O 포트에 씁니다.|
|[_outpw](../c-runtime-library/outp-outpw-outpd.md)|워드를 지정된 I/O 포트에 씁니다.|
|[_putch, _putwch](../c-runtime-library/reference/putch-putwch.md)|문자를 콘솔에 씁니다.|
|[_ungetch, _ungetwch](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)|콘솔에서 마지막 문자 읽기에 "문자를 다시 집어 넣으므로" 다음 문자 읽기가 됩니다.|

## <a name="see-also"></a>참고 항목

[입력 및 출력](../c-runtime-library/input-and-output.md)<br/>
[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)<br/>
