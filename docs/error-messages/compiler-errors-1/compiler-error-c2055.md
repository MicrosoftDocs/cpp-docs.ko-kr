---
description: '자세한 정보: 컴파일러 오류 C2055'
title: 컴파일러 오류 C2055
ms.date: 11/04/2016
f1_keywords:
- C2055
helpviewer_keywords:
- C2055
ms.assetid: 6cec79cc-6bec-443f-9897-fbf5452718c7
ms.openlocfilehash: 0692488b8e1ea91fe235ade512c5fbe5094cdaef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174938"
---
# <a name="compiler-error-c2055"></a>컴파일러 오류 C2055

형식 목록이 아니라 정식 매개 변수 목록이 필요 합니다.

함수 정의에는 정식 매개 변수 목록 대신 매개 변수 형식 목록이 포함 되어 있습니다. ANSI C에서는 void 또는 줄임표 ()가 아닌 정식 매개 변수 이름을 지정 해야 합니다 `...` .

다음 샘플에서는 C2055를 생성 합니다.

```c
// C2055.c
// compile with: /c
void func(int, char) {}  // C2055
void func (int i, char c) {}   // OK
```
