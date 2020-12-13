---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4718'
title: 컴파일러 경고(수준 4) C4718
ms.date: 11/04/2016
f1_keywords:
- C4718
helpviewer_keywords:
- C4718
ms.assetid: 29507f8a-b024-42c1-a3b8-f35d1f2641f3
ms.openlocfilehash: 9c0a24bbec0ae0cf902d905cc2dcecc492efc44b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330551"
---
# <a name="compiler-warning-level-4-c4718"></a>컴파일러 경고(수준 4) C4718

'function call': 재귀 호출에 파생 작업이 없습니다. 삭제하고 있습니다.

함수가 재귀 호출을 포함하지만 그렇지 않은 경우 부수적인 효과가 없습니다. 이 함수에 대한 호출을 삭제하는 중입니다. 프로그램의 정확성에는 영향을 주지 않지만 동작에는 영향을 줍니다. 호출을 그대로 유지하면 런타임 스택 오버플로 예외가 발생할 수 있지만 호출을 삭제하면 이 가능성을 제거합니다.
