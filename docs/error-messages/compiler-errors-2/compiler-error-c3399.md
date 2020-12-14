---
description: '자세한 정보: 컴파일러 오류 C3399'
title: 컴파일러 오류 C3399
ms.date: 11/04/2016
f1_keywords:
- C3399
helpviewer_keywords:
- C3399
ms.assetid: 306ad199-d150-4f6c-bcf1-24a7948b93be
ms.openlocfilehash: a950857e88c5cfcad50ac2efb064af4d7a5c0cf1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316429"
---
# <a name="compiler-error-c3399"></a>컴파일러 오류 C3399

'type': 제네릭 매개 변수의 인스턴스를 만들 때는 인수를 지정할 수 없습니다.

`gcnew()` 제약 조건을 지정할 때 제약 조건 형식이 매개 변수가 없는 생성자를 갖도록 지정합니다. 따라서 해당 형식을 인스턴스화하고 매개 변수를 전달하려고 하면 오류가 발생합니다.

자세한 내용은 [제네릭 형식 매개 변수에 대 한 제약 조건 (c + +/cli)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) 을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3399를 생성합니다.

```cpp
// C3399.cpp
// compile with: /clr /c
generic <class T>
where T : gcnew()
void f() {
   T t = gcnew T(1);   // C3399
   T t2 = gcnew T();   // OK
}
```
