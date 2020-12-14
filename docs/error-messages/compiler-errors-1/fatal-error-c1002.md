---
description: '자세한 정보: 심각한 오류 C1002'
title: 심각한 오류 C1002
ms.date: 11/04/2016
f1_keywords:
- C1002
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
ms.openlocfilehash: edd4ffbd6ce4c8a7f70640619d8dc52775dd0195
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262713"
---
# <a name="fatal-error-c1002"></a>심각한 오류 C1002

2번 패스에서 컴파일러의 힙 공간이 부족합니다.

기호 또는 복잡 한 식이 너무 많은 프로그램 때문에 두 번째 단계에서 컴파일러에 동적 메모리 공간이 부족 합니다.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>아래의 해결 방법 따라 수정합니다.

1. 소스 파일을 여러 개의 작은 파일로 나눕니다.

1. 식을 더 작은 하위 식으로 나눕니다.

1. 메모리를 사용 하는 다른 프로그램 또는 드라이버를 제거 합니다.
