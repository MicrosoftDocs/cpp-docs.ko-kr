---
description: 자세한 내용은 Command-Line Warning D9043을 (를) 확인 하세요.
title: 명령줄 경고 D9043
ms.date: 11/04/2016
f1_keywords:
- D9043
helpviewer_keywords:
- D9043
ms.assetid: 9263e28d-217b-414c-bfb6-86efd3c27a77
ms.openlocfilehash: ac61626f21465056ea96efe784e19405481f1b0f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119751"
---
# <a name="command-line-warning-d9043"></a>명령줄 경고 D9043

' compiler_option '의 ' warning_level ' 값이 잘못 되었습니다. ' 4999 '로 가정 합니다. 코드 분석 경고가 경고 수준과 연결 되어 있지 않습니다.

## <a name="example"></a>예제

다음 샘플에서는 C9043를 생성 합니다.

```cpp
// D9043.cpp
// compile with: /analyze /w16001
// D9043 warning expected
int main() {}
```
