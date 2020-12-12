---
description: '자세한 정보: 컴파일러 오류 C3893'
title: 컴파일러 오류 C3893
ms.date: 11/04/2016
f1_keywords:
- C3893
helpviewer_keywords:
- C3893
ms.assetid: 90d52eae-6ef2-4db1-b7ad-92f9e8b140fb
ms.openlocfilehash: 975e2e356bc4b98a25a80e8ae4cc152c3b9b3207
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119920"
---
# <a name="compiler-error-c3893"></a>컴파일러 오류 C3893

' var ': ' type_name ' 클래스의 인스턴스 생성자 에서만 initonly 데이터 멤버를 l-value로 사용할 수 있습니다.

정적 [initonly](../../dotnet/initonly-cpp-cli.md) 데이터 멤버는 정적 생성자에서 해당 주소만 가져올 수 있습니다.

인스턴스 (비정적) initonly 데이터 멤버는 인스턴스 (비정적) 생성자에서 해당 주소만 가져올 수 있습니다.

다음 샘플에서는 C3893를 생성 합니다.

```cpp
// C3893.cpp
// compile with: /clr
ref struct Y1 {
   Y1() : data_var(0) {
      int% i = data_var;   // OK
   }
   initonly int data_var;
};

int main(){
   Y1^ y= gcnew Y1;
   int% i = y->data_var;   // C3893
}
```
