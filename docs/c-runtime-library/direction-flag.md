---
title: 방향 플래그
description: Microsoft C 런타임 함수에 대 한 CPU 방향 플래그의 효과를 설명 합니다.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- direction flag
ms.assetid: 0836b4af-dbbb-4ab8-a4b2-156f2e2099e2
ms.openlocfilehash: ce4198abd944d538261b9d89bfa9ecea6129a991
ms.sourcegitcommit: 90c300b74f6556cb5d989802d2e80d79542f55e7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102514709"
---
# <a name="direction-flag"></a>방향 플래그

방향 플래그(Direction Flag)는 모든 Intel x86 호환 CPU의 고유한 CPU 플래그입니다. 이 플래그는 MOVS, MOVSD, MOVSW 등과 같은 REP(반복) 접두사를 사용하는 모든 어셈블리 명령에 적용됩니다. 방향 플래그가 0으로 설정되어 있다면 해당되는 어셈블리 명령에 제공되는 주소가 증가합니다.

C 런타임 루틴은 방향 플래그가 지워졌다고 가정합니다. C 런타임 함수와 함께 다른 함수를 사용하는 경우 다른 함수에서 방향 플래그를 그대로 두거나 원래 상태로 복원해야 합니다. 진입시 방향 플래그가 0으로 설정될 것으로 예상하면 보다 빠르고 효율적인 런타임 코드가 생성됩니다.

문자열 조작 및 버퍼 조작 루틴과 같은 C 런타임 라이브러리 함수는 방향 플래그가 명확해야 합니다.

## <a name="see-also"></a>추가 정보

[CRT (c 런타임) 및 STL (c + + 표준 라이브러리) `.lib` 파일](../c-runtime-library/crt-library-features.md)
