---
description: 컴파일러 경고 (수준 1) C4027에 대 한 자세한 정보
title: 컴파일러 경고(수준 1) C4027
ms.date: 12/16/2020
f1_keywords:
- C4027
helpviewer_keywords:
- C4027
ms.openlocfilehash: 1489ca32211854bcf1ef55d1a4ac806ab1611f43
ms.sourcegitcommit: 387ce22a3b0137f99cbb856a772b5a910c9eba99
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97645178"
---
# <a name="compiler-warning-level-1-c4027"></a>컴파일러 경고(수준 1) C4027

> 정식 매개 변수 목록을 사용하지 않고 함수를 선언했습니다.

함수 선언에 정식 매개 변수가 없지만 함수 정의에 정식 매개 변수가 있거나 호출에 실제 매개 변수가 있습니다.

컴파일러는 매개 변수 목록을 사용 하지 않고 함수 이름의 이전 C 스타일 전방 선언에서 수락 하지만 경고 합니다. 나중에이 함수를 호출 하는 경우 컴파일러는 함수가 함수 정의 또는 호출에 있는 형식의 실제 매개 변수를 사용 한다고 가정 합니다. 함수 정의의 시그니처와 일치 하도록 함수 선언을 수정 하는 것이 좋습니다.
