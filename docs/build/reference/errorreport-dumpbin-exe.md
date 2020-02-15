---
title: /ERRORREPORT(dumpbin.exe)
description: Microsoft DUMPBIN 유틸리티/ERRORREPORT 명령줄 옵션에 대 한 참조입니다.
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT
helpviewer_keywords:
- -ERRORREPORT dumpbin option
- ERRORREPORT dumpbin option
- /ERRORREPORT dumpbin option
ms.assetid: 51178c43-4f95-4fda-8f97-50a257d1c948
ms.openlocfilehash: 665b4b1e7c01de4a1fcd848a9e6b36ddbf2944c9
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257678"
---
# <a name="errorreport-dumpbinexe"></a>/ERRORREPORT(dumpbin.exe)

> [!NOTE]
> /ERRORREPORT 옵션은 사용 되지 않습니다. Windows Vista부터 오류 보고는 [WER (Windows 오류 보고)](/windows/win32/wer/windows-error-reporting) 설정에 의해 제어 됩니다.

## <a name="syntax"></a>구문

> **/ERRORREPORT**\[**NONE** \| **프롬프트** \| **QUEUE** \| **SEND** ]

## <a name="remarks"></a>주의

**/ERRORREPORT** 인수는 Windows 오류 보고 서비스 설정에 의해 재정의 됩니다. Windows 오류 보고에서 보고를 사용 하도록 설정한 경우 DUMPBIN은 Microsoft에 내부 오류 보고서를 자동으로 보냅니다. Windows 오류 보고에서 사용 하지 않도록 설정한 경우 보고서가 전송 되지 않습니다.

## <a name="see-also"></a>참고 항목

[DUMPBIN 옵션](dumpbin-options.md)
