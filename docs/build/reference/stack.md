---
title: -STACK | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /stack
dev_langs:
- C++
helpviewer_keywords:
- -STACK editbin option
- STACK editbin option
- stack, setting size
- /STACK editbin option
ms.assetid: a39bcff0-c945-4355-80cc-8e4f24a5f142
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8deb3e3bedcb773aa01ae5f1c3ff66ce9d509f2
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716668"
---
# <a name="stack"></a>/STACK

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>설명

이 옵션 스택의 크기를 바이트 단위로 설정 하 고 10 진수 또는 C 언어 표기법으로 인수를 사용 합니다. /STACK 옵션 실행 파일에만 적용 됩니다.

합니다 *예약할* 인수 가상 메모리의 총 스택 할당을 지정 합니다. EDITBIN 가장 가까운 4 바이트에 지정된 된 값으로 반올림합니다.

선택적 `commit` 인수가 운영 체제에 의해 해석 될 수 있습니다. Windows NT, Windows 95 및 Windows 98 `commit` 한 번에 할당할 실제 메모리 양을 지정 합니다. 커밋된 가상 메모리 페이징 파일에 예약 될 공간을 하면 됩니다. 더 높은 `commit` 값 시간 응용 프로그램의 스택 공간이 더 필요할 경우 있지만 메모리 요구량과 시작 시간을 절약할 수 있습니다.

## <a name="see-also"></a>참고 항목

[EDITBIN 옵션](../../build/reference/editbin-options.md)