---
description: '자세한 정보: 컴파일러 오류 C3141'
title: 컴파일러 오류 C3141
ms.date: 11/04/2016
f1_keywords:
- C3141
helpviewer_keywords:
- C3141
ms.assetid: b4fd65c3-50cc-46cd-8de0-6a6d24cb9cda
ms.openlocfilehash: bc5ebc1376d17cead4697987e35b4733e8ab0a22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304209"
---
# <a name="compiler-error-c3141"></a>컴파일러 오류 C3141

' interface_name ': 인터페이스는 공용 상속만 지원 합니다.

[Interface (또는 __interface)](../../cpp/interface.md) 키워드로 정의 된 인터페이스는 공용 상속만 지원 합니다.

다음 샘플에서는 C3141를 생성 합니다.

```cpp
// C3141.cpp
__interface IBase {};
__interface IDerived1 : protected IBase {};  // C3141
__interface IDerived2 : private IBase {};    // C3141
```
