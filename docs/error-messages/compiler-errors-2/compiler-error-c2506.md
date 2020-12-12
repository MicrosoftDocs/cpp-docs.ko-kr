---
description: '자세한 정보: 컴파일러 오류 C2506'
title: 컴파일러 오류 C2506
ms.date: 11/04/2016
f1_keywords:
- C2506
helpviewer_keywords:
- C2506
ms.assetid: cfed21cd-2404-46f2-985e-d0c2c3820830
ms.openlocfilehash: 28af99e418d8c058fa9b28b5fd581a44c0180065
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212989"
---
# <a name="compiler-error-c2506"></a>컴파일러 오류 C2506

' member ': ' __declspec (한정자) '는이 기호에 적용할 수 없습니다.

관리 되는 클래스의 정적 멤버에 대해서는 프로세스별 또는 appdomain 별을 선언할 수 없습니다.

자세한 내용은 [appdomain](../../cpp/appdomain.md) 를 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C2506를 생성 합니다.

```cpp
// C2506.cpp
// compile with: /clr /c
ref struct R {
   __declspec(process) static int n;   // C2506
   int o;   // OK
};
```
