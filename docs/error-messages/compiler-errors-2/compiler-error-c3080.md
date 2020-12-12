---
description: '자세한 정보: 컴파일러 오류 C3080'
title: 컴파일러 오류 C3080
ms.date: 11/04/2016
f1_keywords:
- C3080
helpviewer_keywords:
- C3080
ms.assetid: ff62a3f7-9b3b-44bd-b8d9-f3a8e5354560
ms.openlocfilehash: 746e5527118c617983e96d02a584a0aa4508c64c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320156"
---
# <a name="compiler-error-c3080"></a>컴파일러 오류 C3080

'finalizer_function': 종료자에는 스토리지 클래스 지정자를 사용할 수 없습니다.

자세한 내용은 [방법: 클래스 및 구조체 정의 및 사용 (c + +/cli)의 소멸자 및 종료자](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3080을 생성합니다.

```cpp
// C3080.cpp
// compile with: /clr /c
ref struct rs {
protected:
   static !rs(){}   // C3080
   !rs(){}   // OK
};
```
