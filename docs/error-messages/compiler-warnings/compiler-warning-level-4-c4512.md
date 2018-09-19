---
title: 컴파일러 경고 (수준 4) C4512 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4512
dev_langs:
- C++
helpviewer_keywords:
- C4512
ms.assetid: afb68995-684a-4be5-a73a-38d7a16dc030
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9aee9e7f48430ddc9b2b9a6a7f055ac8b1e32b71
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029951"
---
# <a name="compiler-warning-level-4-c4512"></a>컴파일러 경고(수준 4) C4512

'class': 할당 연산자를 생성하지 못했습니다.

컴파일러가 지정된 클래스에 대한 할당 연산자를 생성할 수 없습니다. 할당 연산자가 작성되지 않았습니다.

이 경고는 파생 클래스에서 액세스할 수 없는 기본 클래스의 할당 연산자로 인해 발생할 수 있습니다.

이 경고를 방지하려면 클래스에 사용자 정의 할당 연산자를 지정합니다.

또한 컴파일러는 할당 연산자 함수를 정의하지 않는 클래스에 대해서도 할당 연산자 함수를 생성합니다. 이 할당 연산자는 개체 데이터 멤버의 멤버 수준 복사본입니다. `const` 데이터 항목은 초기화한 후에는 수정할 수 없으므로 클래스에 `const` 항목이 포함되어 있으면 기본 할당 연산자가 작동하지 않습니다. C4512 경고가 발생하는 또 다른 원인은 참조 형식의 비정적 데이터 멤버 선언입니다. 복사할 수 없는 형식을 만들려는 경우에는 기본 복사 생성자 생성도 차단해야 합니다.

다음의 세 가지 방법 중 하나로 코드에 대한 C4512 경고를 해결할 수 있습니다.

- 클래스에 대해 할당 연산자를 명시적으로 정의합니다.

- 제거할 **const** 또는 클래스의 데이터 항목에서 참조 연산자.

- #pragma 사용 [경고](../../preprocessor/warning.md) 경고를 억제 하려면 문입니다.

## <a name="example"></a>예제

다음 샘플에서는 C4512 오류가 발생하는 경우를 보여 줍니다.

```
// C4512.cpp
// compile with: /EHsc /W4
// processor: x86

class Base {
private:
   const int a;

public:
   Base(int val = 0) : a(val) {}
   int get_a() { return a; }
};   // C4512 warning

class Base2 {
private:
   const int a;

public:
   Base2(int val = 0) : a(val) {}
   Base2 & operator=( const Base2 & ) { return *this; }
   int get_a() { return a; }
};

// Type designer intends this to be non-copyable because it has a
// reference member
class Base3
{
private:
   char& cr;

public:
   Base3(char& r) : cr(r) {}
   // Uncomment the following line to explicitly disable copying:
   // Base3(const Base3&) = delete;
};   // C4512 warning

int main() {
   Base first;
   Base second;

   // OK
   Base2 first2;
   Base2 second2;

   char c = 'x';
   Base3 first3(c);
   Base3 second3 = first3; // C2280 if no default copy ctor
}
```