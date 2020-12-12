---
description: '자세한 정보: 컴파일러 오류 C3459'
title: 컴파일러 오류 C3459
ms.date: 11/04/2016
f1_keywords:
- C3459
helpviewer_keywords:
- C3459
ms.assetid: 3d290a20-d313-4c07-9bd8-c5c159cb169f
ms.openlocfilehash: 862dd9b2f84a44db2e2cd08b918938b14692e18d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113573"
---
# <a name="compiler-error-c3459"></a>컴파일러 오류 C3459

'attribute': 특성은 클래스 인덱서(인덱싱된 기본 속성)에만 사용할 수 있습니다.

클래스 인덱서 속성에 적용하기 위한 특성을 잘못 사용했습니다.

자세한 내용은 [방법: c + +/cli에서 속성 사용](../../dotnet/how-to-use-properties-in-cpp-cli.md)을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3459를 생성합니다.

```cpp
// C3459.cpp
// compile with: /clr /c
public ref class MyString {
public:
   [System::Runtime::CompilerServices::IndexerName("Chars")]   // C3459
   property int Prop;
};

// OK
public ref class MyString2 {
   array<int>^ MyArr;
public:
   MyString2() {
      MyArr = gcnew array<int>(5);
   }

   [System::Runtime::CompilerServices::IndexerName("Chars")]   // OK
   property int default[int] {
      int get(int index) {
         return MyArr[index];
      }
      void set(int index, int value) {
         MyArr[index] = value;
      }
   }
};
```
