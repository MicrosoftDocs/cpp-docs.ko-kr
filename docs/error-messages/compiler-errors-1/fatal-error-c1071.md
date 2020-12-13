---
description: '자세한 정보: 심각한 오류 C1071'
title: 심각한 오류 C1071
ms.date: 11/04/2016
f1_keywords:
- C1071
helpviewer_keywords:
- C1071
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
ms.openlocfilehash: c4a6734dcb515b6d495eac720f83ba39be3c3677
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344382"
---
# <a name="fatal-error-c1071"></a>심각한 오류 C1071

주석에서 예기치 않은 파일의 끝이 나타났습니다.

컴파일러가 주석을 검색 하는 동안 파일의 끝에 도달 했습니다.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>다음과 같은 가능한 원인을 확인하여 수정하려면

1. 주석 종결자 (*/)가 없습니다.

1. 소스 파일의 마지막 줄에서 주석 뒤에 줄 바꿈 문자가 없습니다.

다음 샘플에서는 C1071를 생성 합니다.

```cpp
// C1071.cpp
int main() {
}

/* this comment is fine */
/* forgot the closing tag        // C1071
```
