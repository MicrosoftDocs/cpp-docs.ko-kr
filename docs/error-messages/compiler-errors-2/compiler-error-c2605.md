---
title: 컴파일러 오류 C2605 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2605
dev_langs:
- C++
helpviewer_keywords:
- C2605
ms.assetid: a0e6f132-5acf-4e19-b277-ddf196d182bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3689e7f0784c847d260c2e97c502b57db99a8918
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044329"
---
# <a name="compiler-error-c2605"></a>컴파일러 오류 C2605

'name': 이 메서드는 관리되는 클래스나 WinRT 클래스에서 예약됩니다.

특정 이름은 내부 함수용으로 컴파일러에서 예약됩니다.  자세한 내용은 [소멸자 및 종료자](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)합니다.

## <a name="example"></a>예제

다음 샘플에서는 C2605 오류가 발생하는 경우를 보여 줍니다.

```
// C2605.cpp
// compile with: /clr /c
ref class R {
protected:
   void Finalize() {}   // C2605
};
```