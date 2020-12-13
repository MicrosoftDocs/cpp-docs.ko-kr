---
description: '자세한 정보: NMAKE 심각한 오류 U1099'
title: NMAKE 심각한 오류 U1099
ms.date: 11/04/2016
f1_keywords:
- U1099
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
ms.openlocfilehash: 8044010cf967e4fe27b2235968022023d66ae1c3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345318"
---
# <a name="nmake-fatal-error-u1099"></a>NMAKE 심각한 오류 U1099

스택 오버플로

처리 중인 메이크파일이 NMAKE의 현재 스택 할당에 대해 너무 복잡 합니다. NMAKE는 0x3000 (12K)를 할당 합니다.

NMAKE의 스택 할당을 늘리려면 더 큰 스택 옵션을 사용 하 여 [editbin/stack](../../build/reference/stack.md) 유틸리티를 실행 합니다.

**editbin/STACK: reserve NMAKE.EXE**

여기서 *reserve* 는 NMAKE의 현재 스택 할당 보다 큰 숫자입니다.
