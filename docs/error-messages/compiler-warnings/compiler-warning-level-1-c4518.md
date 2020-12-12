---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4518'
title: 컴파일러 경고(수준 1) C4518
ms.date: 11/04/2016
f1_keywords:
- C4518
helpviewer_keywords:
- C4518
ms.assetid: 4ad21004-f076-43fd-99f4-4bf1f9be4c0b
ms.openlocfilehash: 1a04dbcdc62e6758e2b65c6b0ef5aa99a1823ef0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212300"
---
# <a name="compiler-warning-level-1-c4518"></a>컴파일러 경고(수준 1) C4518

' 지정자 ': 예기치 않은 저장소 클래스 또는 형식 지정자입니다. 무시

다음 샘플에서는 C4518를 생성 합니다.

```cpp
// C4518.cpp
// compile with: /c /W1
_declspec(dllexport) extern "C" void MyFunction();   // C4518

extern "C" void MyFunction();   // OK
```
