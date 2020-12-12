---
description: '자세한 정보: 컴파일러 오류 C2585'
title: 컴파일러 오류 C2585
ms.date: 11/04/2016
f1_keywords:
- C2585
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
ms.openlocfilehash: 568e5db1ca160b9fd13596d4f94f646cb4cf0bdd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177655"
---
# <a name="compiler-error-c2585"></a>컴파일러 오류 C2585

' t r u e '로의 명시적 변환이 모호 합니다.

형식 변환에는 두 개 이상의 결과가 생성 될 수 있습니다.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>다음과 같은 가능한 원인을 확인하여 수정하려면

1. 여러 상속을 기반으로 클래스 또는 구조체 형식에서 변환 형식이 동일한 기본 클래스를 두 번 이상 상속 하는 경우 변환 함수 또는 연산자는 범위 확인 ()을 사용 `::` 하 여 변환에 사용할 상속 된 클래스를 지정 해야 합니다.

1. 변환 연산자와 생성자가 동일한 변환을 수행 하 여 정의 되었습니다.
