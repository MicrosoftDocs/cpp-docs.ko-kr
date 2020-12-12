---
description: '자세한 정보: 컴파일러 오류 C2731'
title: 컴파일러 오류 C2731
ms.date: 11/04/2016
f1_keywords:
- C2731
helpviewer_keywords:
- C2731
ms.assetid: 9b563999-febd-4582-9147-f355083c091e
ms.openlocfilehash: baae65ff1d09bafe37251b7593dc0d0c91c89f1b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123307"
---
# <a name="compiler-error-c2731"></a>컴파일러 오류 C2731

' identifier ': 함수를 오버 로드할 수 없습니다.

,, `main` 및 함수는 `WinMain` `DllMain` `LibMain` 오버 로드 될 수 없습니다.

다음 샘플에서는 C2731를 생성 합니다.

```cpp
// C2731.cpp
extern "C" void WinMain(int, char *, char *);
void WinMain(int, short, char *, char*);   // C2731
```
