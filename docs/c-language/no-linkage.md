---
title: 링크 없음
ms.date: 11/04/2016
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
ms.openlocfilehash: 69ead5d12d6689370e9ae04a54d5f5a8db06eca5
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500751"
---
# <a name="no-linkage"></a>링크 없음

블록 내의 식별자 선언에 **`extern`** 스토리지 클래스 지정자가 포함되어 있지 않은 경우 식별자가 링크를 포함하지 않고 함수에 대해 고유한 것입니다.

다음 식별자에는 링크가 없습니다.

- 개체 또는 함수 이외의 항목으로 선언된 식별자

- 함수 매개 변수로 선언된 식별자

- **`extern`** 스토리지 클래스 지정자 없이 선언된 개체에 대한 블록 범위 식별자

식별자에 링크가 없는 경우 동일한 범위 수준에서 선언자 또는 형식 지정자에 동일한 이름을 다시 선언하면 기호 재정의 오류가 발생합니다.

## <a name="see-also"></a>참조

[extern을 사용하여 링크 지정](../cpp/extern-cpp.md)
