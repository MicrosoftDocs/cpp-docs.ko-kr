---
description: 자세히 알아보기:/STACK
title: /STACK
ms.date: 11/04/2016
f1_keywords:
- /stack_editbin
helpviewer_keywords:
- -STACK editbin option
- STACK editbin option
- stack, setting size
- /STACK editbin option
ms.assetid: a39bcff0-c945-4355-80cc-8e4f24a5f142
ms.openlocfilehash: 253aec1d760a85f1ebe5dbf7596353b46744cd57
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224454"
---
# <a name="stack"></a>/STACK

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>설명

이 옵션은 스택의 크기 (바이트)를 설정 하 고 10 진수 또는 C 언어 표기법으로 인수를 사용 합니다. /STACK 옵션은 실행 파일에만 적용 됩니다.

*Reserve* 인수는 가상 메모리의 총 스택 할당을 지정 합니다. EDITBIN은 지정 된 값을 가장 가까운 4 바이트로 반올림 합니다.

선택적 `commit` 인수는 운영 체제에서 해석할 수 있습니다. Windows NT, Windows 95 및 Windows 98에서 `commit` 한 번에 할당할 실제 메모리의 양을 지정 합니다. 커밋된 가상 메모리를 설정 하면 페이징 파일에 공간이 예약 됩니다. 값이 클수록 `commit` 응용 프로그램에 더 많은 스택 공간이 필요할 때 시간이 절약 되지만 메모리 요구 사항과 시작 시간이 늘어날 수 있습니다.

## <a name="see-also"></a>참고 항목

[EDITBIN 옵션](editbin-options.md)
