---
description: '자세한 정보: 컴파일러 오류 C3799'
title: 컴파일러 오류 C3799
ms.date: 11/04/2016
f1_keywords:
- C3799
helpviewer_keywords:
- C3799
ms.assetid: 336a2811-9370-4e6e-b03b-325bda470805
ms.openlocfilehash: 31ada62b9bc347ce4d4889eca72d8d8e9c2987e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291625"
---
# <a name="compiler-error-c3799"></a>컴파일러 오류 C3799

인덱싱된 속성은 빈 매개 변수 목록을 포함할 수 없습니다.

인덱싱된 속성이 잘못 선언 되었습니다. 자세한 내용은 [방법: c + +/cli에서 속성 사용](../../dotnet/how-to-use-properties-in-cpp-cli.md)을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3799를 생성 하 고 수정 하는 방법을 보여 줍니다.

```cpp
// C3799.cpp
// compile with: /clr /c
ref struct C {
   property int default[] {   // C3799
   // try the following line instead
   // property int default[int] {
      int get(int index) { return 0; }
      void set(int index, int value) {}
   }
};
```
