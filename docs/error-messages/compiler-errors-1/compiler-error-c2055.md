---
title: 컴파일러 오류 C2055
ms.date: 11/04/2016
f1_keywords:
- C2055
helpviewer_keywords:
- C2055
ms.assetid: 6cec79cc-6bec-443f-9897-fbf5452718c7
ms.openlocfilehash: 9cb6e4d5891c5aefc9d66e7d70a5cd7685ccd393
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302044"
---
# <a name="compiler-error-c2055"></a>컴파일러 오류 C2055

형식 목록이 아니라 정식 매개 변수 목록이 필요 합니다.

함수 정의에는 정식 매개 변수 목록 대신 매개 변수 형식 목록이 포함 되어 있습니다. ANSI C에서는 void 또는 줄임표 (`...`)가 아닌 경우 정식 매개 변수 이름을 지정 해야 합니다.

다음 샘플에서는 C2055를 생성 합니다.

```c
// C2055.c
// compile with: /c
void func(int, char) {}  // C2055
void func (int i, char c) {}   // OK
```
