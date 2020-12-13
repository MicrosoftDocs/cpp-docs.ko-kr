---
description: '자세한 정보: 컴파일러 경고 C4962'
title: 컴파일러 경고 C4962
ms.date: 11/04/2016
f1_keywords:
- C4962
helpviewer_keywords:
- C4962
ms.assetid: 62b156fe-04e5-4a6e-9339-6ab148185f87
ms.openlocfilehash: a263f89c0b57eca07f0ab27758163052586eda03
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336075"
---
# <a name="compiler-warning-c4962"></a>컴파일러 경고 C4962

'function': 최적화를 하면 프로필 데이터가 일관성이 없어지므로 프로필 기반 최적화를 사용하지 않습니다.

함수의 개수(프로필) 데이터를 신뢰할 수 없기 때문에 함수가 /LTCG:PGO로 컴파일되지 않았습니다. 해당 함수에 대한 신뢰할 수 없는 프로필 데이터가 포함된 .pgc 파일을 다시 생성하려면 프로파일링을 다시 실행합니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)을 참조하세요.
