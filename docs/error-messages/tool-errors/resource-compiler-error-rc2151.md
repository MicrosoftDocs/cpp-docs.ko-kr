---
title: 리소스 컴파일러 오류 RC2151 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2151
dev_langs:
- C++
helpviewer_keywords:
- RC2151
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a15f3f1237df9e4b706a2c2048dddd6d5db395d5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109784"
---
# <a name="resource-compiler-error-rc2151"></a>리소스 컴파일러 오류 RC2151

문자열 상수를 다시 사용할 수 없습니다.

두 번에 같은 값을 사용 하는 한 **STRINGTABLE** 문입니다. 겹치는 10 진수 및 16 진수 값을 함께 사용 하지 있는지 확인 합니다.

각 ID는 **STRINGTABLE** 고유 해야 합니다. 연속적인 상수를 사용 하 여 효율성을 극대화 하는 16의 배수로 시작합니다.