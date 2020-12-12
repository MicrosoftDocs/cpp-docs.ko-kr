---
description: '자세한 정보: 컴파일러 오류 C3077'
title: 컴파일러 오류 C3077
ms.date: 11/04/2016
f1_keywords:
- C3077
helpviewer_keywords:
- C3077
ms.assetid: d9f3c619-d1e2-4656-81a5-a35a9586a7d4
ms.openlocfilehash: a8e6a15f38427727939fbaabb0bfcf4d9e315d77
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320169"
---
# <a name="compiler-error-c3077"></a>컴파일러 오류 C3077

'finalizer': 종료자는 참조 형식의 멤버만 될 수 있습니다.

종료자를 네이티브 또는 값 형식을 선언할 수 없습니다.

자세한 내용은 [방법: 클래스 및 구조체 정의 및 사용 (c + +/cli)의 소멸자 및 종료자](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3077을 생성합니다.

```cpp
// C3077.cpp
// compile with: /clr /c
value struct vs {
   !vs(){}   // C3077
};

ref struct rs {
protected:
   !rs(){}   // OK
};
```
