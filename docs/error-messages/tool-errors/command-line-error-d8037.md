---
title: 명령줄 오류 D8037
ms.date: 11/04/2016
f1_keywords:
- D8037
helpviewer_keywords:
- D8037
ms.assetid: acddaaa0-bd84-426f-a37b-8f680b379c9d
ms.openlocfilehash: ed6778861c89bb9755087c4d58f094a57d5f760f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196861"
---
# <a name="command-line-error-d8037"></a>명령줄 오류 D8037

임시 il 파일을 만들 수 없습니다. 이전 il 파일의 임시 디렉터리 정리

공간이 부족 하 여 임시 컴파일러 중간 파일을 만들 수 없습니다. 이 오류를 해결 하려면 **TMP** 환경 변수로 지정 된 디렉터리에서 모든 이전 MSIL 파일을 제거 합니다. 이러한 파일은 _CL_hhhhhhhh. ss 형식입니다. 여기서 h는 임의의 16 진수를 나타내고 ss는 IL 파일의 유형을 나타냅니다. 또한 최신 운영 체제 패치를 사용 하 여 컴퓨터를 업데이트 해야 합니다.

## <a name="see-also"></a>참고 항목

[명령줄 오류(D8000 ~ D9999)](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[MSVC 컴파일러 옵션](../../build/reference/compiler-options.md)
