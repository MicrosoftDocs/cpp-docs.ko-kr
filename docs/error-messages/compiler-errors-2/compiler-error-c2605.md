---
description: '자세한 정보: 컴파일러 오류 C2605'
title: 컴파일러 오류 C2605
ms.date: 11/04/2016
f1_keywords:
- C2605
helpviewer_keywords:
- C2605
ms.assetid: a0e6f132-5acf-4e19-b277-ddf196d182bf
ms.openlocfilehash: e2aa86419b816cc48eecb9b981df73eeb3e48ccd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336234"
---
# <a name="compiler-error-c2605"></a>컴파일러 오류 C2605

'name': 이 메서드는 관리되는 클래스나 WinRT 클래스에서 예약됩니다.

특정 이름은 내부 함수용으로 컴파일러에서 예약됩니다.  자세한 내용은 [소멸자 및 종료자](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C2605 오류가 발생하는 경우를 보여 줍니다.

```cpp
// C2605.cpp
// compile with: /clr /c
ref class R {
protected:
   void Finalize() {}   // C2605
};
```
