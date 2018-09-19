---
title: NMAKE의 종료 코드 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b5a593e38efb5230630ed01e65f4bfb1f2ba92a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722620"
---
# <a name="exit-codes-from-nmake"></a>NMAKE의 종료 코드

NMAKE 다음 종료 코드를 반환합니다.

|코드|의미|
|----------|-------------|
|0|오류 없음 (가능한 경우 경고)|
|1|불완전 한 빌드 (/K을 사용한 경우에 발생)|
|2|다음 중 하나 때문일 프로그램 오류:|
||메이크파일의-구문 오류|
||명령에서-오류 또는 종료 코드|
||-사용자가 중단|
|4|시스템 오류-메모리가 부족 합니다.|
|255|대상 최신 상태가 아닙니다 (/Q를 사용한 경우에 발생)|

## <a name="see-also"></a>참고 항목

[NMAKE 실행](../build/running-nmake.md)