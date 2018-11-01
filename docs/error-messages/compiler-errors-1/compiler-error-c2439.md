---
title: 컴파일러 오류 C2439
ms.date: 11/04/2016
f1_keywords:
- C2439
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
ms.openlocfilehash: f71112d3f37f3e4d1a4f41bade95726d7aa0a0bc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644362"
---
# <a name="compiler-error-c2439"></a>컴파일러 오류 C2439

'identifier': 멤버를 초기화할 수 없습니다

클래스, 구조체 또는 공용 구조체 멤버를 초기화할 수 없습니다.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>다음과 같은 가능한 원인을 확인하여 수정하려면

1. 간접 기본 클래스 또는 구조체를 초기화 하려고 합니다.

1. 클래스 또는 구조체의 상속 된 멤버를 초기화 하려고 합니다. 상속된 된 멤버는 클래스 또는 구조체의 생성자에서 초기화 되어야 합니다.