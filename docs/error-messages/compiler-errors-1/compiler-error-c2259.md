---
description: '자세한 정보: 컴파일러 오류 C2259'
title: 컴파일러 오류 C2259
ms.date: 11/04/2016
f1_keywords:
- C2259
helpviewer_keywords:
- C2259
ms.assetid: e458236f-bdea-4786-9aa6-a98d8bffa5f4
ms.openlocfilehash: 640349f5870cd818019029c7f04db3e33a068ec9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134695"
---
# <a name="compiler-error-c2259"></a>컴파일러 오류 C2259

' class ': 추상 클래스를 인스턴스화할 수 없습니다.

코드는 추상 클래스 또는 구조체의 인스턴스를 선언 합니다.

하나 이상의 순수 가상 함수를 사용 하 여 클래스 또는 구조체를 인스턴스화할 수 없습니다. 파생 클래스의 개체를 인스턴스화하려면 파생 클래스가 각 순수 가상 함수를 재정의 해야 합니다.

자세한 내용은 [암시적 추상 클래스](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Implicitly_abstract_classes)를 참조 하세요.

다음 샘플에서는 C2259를 생성 합니다.

```cpp
// C2259.cpp
// compile with: /c
class V {
public:
   void virtual func() = 0;
};
class A : public V {};
class B : public V {
public:
   void func();
};
V v;  // C2259, V is an abstract class
A a;  // C2259, A inherits func() as pure virtual
B b;  // OK, B defines func()
```

인터페이스에서 파생 하 고 public이 아닌 액세스 권한으로 파생 클래스에서 인터페이스 메서드를 구현 하는 경우 항상 C2259을 받을 수 있습니다.  이는 컴파일러에서 파생 클래스에 구현 된 인터페이스 메서드를 공용 액세스로 예상 하기 때문에 발생 합니다. 더 제한적인 액세스 권한이 있는 인터페이스에 대 한 멤버 함수를 구현 하는 경우 컴파일러는 인터페이스에 정의 된 인터페이스 메서드를 구현 하는 것으로 간주 하지 않고 파생 된 클래스를 추상 클래스로 만듭니다.

문제에 대 한 두 가지 해결 방법이 있습니다.

- 구현 된 메서드에 대 한 액세스 권한을 public으로 설정 합니다.

- 파생 클래스에 구현 된 인터페이스 메서드에 대해 범위 확인 연산자를 사용 하 여 구현 된 메서드 이름을 인터페이스 이름으로 한정 합니다.

C2259는 Visual Studio 2005에서 수행 된 규칙 작업의 결과로 발생할 수도 있습니다. **/zc: wchar_t** 는 현재 기본적으로 on입니다. 이러한 상황에서 C2599는 **/zc: wchar_t-** 를 사용 하 여 컴파일하여 이전 버전에서의 동작을 얻거나 호환 되도록 형식을 업데이트 하 여 해결할 수 있습니다. 자세한 내용은 [/zc: wchar_t (Wchar_t 네이티브 형식)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md)를 참조 하세요.

다음 샘플에서는 C2259를 생성 합니다.

```cpp
// C2259b.cpp
// compile with: /c
#include <windows.h>

class MyClass {
public:
   // WCHAR now typedef'ed to wchar_t
   virtual void func(WCHAR*) = 0;
};

class MyClass2 : MyClass {
public:
   void func(unsigned short*);
};

MyClass2 x;   // C2259

// OK
class MyClass3 {
public:
   virtual void func(WCHAR*) = 0;
   virtual void func2(wchar_t*) = 0;
   virtual void func3(unsigned short*) = 0;
};

class MyClass4 : MyClass3 {
public:
   void func(WCHAR*) {}
   void func2(wchar_t*) {}
   void func3(unsigned short*) {}
};

MyClass4 y;
```

다음 샘플에서는 C2259를 생성 합니다.

```cpp
// C2259c.cpp
// compile with: /clr
interface class MyInterface {
   void MyMethod();
};

ref class MyDerivedClass: public MyInterface {
private:
   // Uncomment the following line to resolve.
   // public:
   void MyMethod(){}
   // or the following line
   // void MyInterface::MyMethod() {};
};

int main() {
   MyDerivedClass^ instance = gcnew MyDerivedClass; // C2259
}
```
