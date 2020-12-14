---
description: '자세한 정보: 부동 소수점 보조 프로세서 및 호출 규칙'
title: 부동 소수점 보조 프로세서 및 호출 규칙
ms.date: 11/04/2016
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
ms.openlocfilehash: 2f68671783b8a556e787aa6637b9b5c2e5799485
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242550"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>부동 소수점 보조 프로세서 및 호출 규칙

부동 소수점 보조 프로세서에 대 한 어셈블리 루틴을 작성 하는 경우 **`float`** **`double`** 함수에서 ST (0)로 반환 해야 하는 또는 값을 반환 하지 않는 한 부동 소수점 제어 단어를 유지 하 고 보조 프로세서 스택을 정리 해야 합니다.

## <a name="see-also"></a>참조

[호출 규칙](../cpp/calling-conventions.md)
