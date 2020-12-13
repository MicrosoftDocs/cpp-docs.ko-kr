---
description: '자세한 정보: 컴파일러 오류 C2414'
title: 컴파일러 오류 C2414
ms.date: 11/04/2016
f1_keywords:
- C2414
helpviewer_keywords:
- C2414
ms.assetid: bbe94e03-862e-4990-b15e-544ae464727d
ms.openlocfilehash: 5bf2d017ac0018fe092b5a003dee021dd13370b9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340335"
---
# <a name="compiler-error-c2414"></a>컴파일러 오류 C2414

피연산자 수가 잘못 되었습니다.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>다음과 같은 가능한 원인을 확인하여 수정하려면

1. Opcode는 사용 되는 피연산자 수를 지원 하지 않습니다. 어셈블리 언어 참조 설명서를 확인 하 여 올바른 피연산자 수를 확인 합니다.

1. 최신 프로세서는 피연산자 수가 다른 명령을 지원 합니다. 최신 프로세서를 사용 하도록 [/arch (최소 CPU 아키텍처)](../../build/reference/arch-minimum-cpu-architecture.md) 옵션을 조정 합니다.
