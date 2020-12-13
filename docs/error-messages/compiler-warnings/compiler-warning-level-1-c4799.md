---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4799'
title: 컴파일러 경고(수준 1) C4799
ms.date: 11/04/2016
f1_keywords:
- C4799
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
ms.openlocfilehash: 9bfa84791a713d5ed5c0382402b958c255e30521
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334937"
---
# <a name="compiler-warning-level-1-c4799"></a>컴파일러 경고(수준 1) C4799

> '*Function*' 함수의 끝에 emms 명령이가 없습니다.

함수에 하나 이상의 MMX 명령이 있지만 `EMMS` 명령이 없습니다. 멀티미디어 명령이 사용 되는 경우에는 `EMMS` `_mm_empty` MMX 코드의 끝에서 멀티미디어 태그 단어를 지워야 하는 명령 또는 내장 함수도 사용 해야 합니다.

Ivec. h를 사용 하는 경우 코드에서를 반환 하기 전에 EMMS 명령이 명령을 올바르게 실행 하지 C4799을 나타낼 수 있습니다. 이는 이러한 헤더에 대해 거짓 경고입니다. Ivec. h에서 _SILENCE_IVEC_C4799를 정의 하 여이 기능을 해제할 수 있습니다. 그러나이로 인해 컴파일러가이 형식의 올바른 경고를 제공 하지 않도록 주의 해야 합니다.

관련 정보는 [Intel의 MMX 명령 집합](../../assembler/inline/intel-s-mmx-instruction-set.md)을 참조 하세요.
