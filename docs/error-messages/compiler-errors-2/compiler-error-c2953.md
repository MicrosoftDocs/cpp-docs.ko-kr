---
description: '자세한 정보: 컴파일러 오류 C2953'
title: 컴파일러 오류 C2953
ms.date: 11/04/2016
f1_keywords:
- C2953
helpviewer_keywords:
- C2953
ms.assetid: 8dbcfa24-8296-4e40-bdc4-5526c07d8892
ms.openlocfilehash: 3bfc51d08318a4870f993a1d0cfe86eb1a38929e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210598"
---
# <a name="compiler-error-c2953"></a>컴파일러 오류 C2953

'identifier': 클래스 템플릿이 이미 정의되었습니다.

소스 파일을 확인하고 다른 정의에 대한 파일을 포함합니다.

다음 샘플에서는 C2953을 생성합니다.

```cpp
// C2953.cpp
// compile with: /c
template <class T>  class A {};
template <class T>  class A {};   // C2953
template <class T>  class B {};   // OK
```
