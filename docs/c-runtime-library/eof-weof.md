---
title: EOF, WEOF
ms.date: 11/04/2016
f1_keywords:
- EOF
helpviewer_keywords:
- EOF function
- WEOF function
- end of file
ms.assetid: a7150563-cdae-4cdf-9798-ad509990e505
ms.openlocfilehash: 9317fdad16121374b31e0862f3326f4150c71579
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667391"
---
# <a name="eof-weof"></a>EOF, WEOF

## <a name="syntax"></a>구문

```

#include <stdio.h>
```

## <a name="remarks"></a>설명

파일 끝(또는 경우에 따라 오류)이 발견되면 I/O 루틴에 의해 EOF가 반환됩니다.

WEOF는 **wint_t** 형식의 반환 값을 전달하고 와이드 스트림의 끝을 알리거나 오류 조건을 보고하는 데 사용됩니다.

## <a name="see-also"></a>참고 항목

[putc, putwc](../c-runtime-library/reference/putc-putwc.md)<br/>
[ungetc, ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[fflush](../c-runtime-library/reference/fflush.md)<br/>
[fclose, _fcloseall](../c-runtime-library/reference/fclose-fcloseall.md)<br/>
[_ungetch, _ungetwch, _ungetch_nolock, _ungetwch_nolock](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)<br/>
[_putch, _putwch](../c-runtime-library/reference/putch-putwch.md)<br/>
[isascii, __isascii, iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)<br/>
[전역 상수](../c-runtime-library/global-constants.md)