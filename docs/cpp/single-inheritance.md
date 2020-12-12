---
description: '자세한 정보: 단일 상속'
title: 단일 상속
ms.date: 11/19/2018
helpviewer_keywords:
- single inheritance
- base classes [C++], indirect
- scope, scope resolution operator
- operators [C++], scope resolution
- scope resolution operator
- derived classes [C++], single base class
- inheritance, single
ms.assetid: 1cb946ed-8b1b-4cf1-bde0-d9cecbfdc622
ms.openlocfilehash: a750cf66074612ce40f9a4fa03d8453ae2decfef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116953"
---
# <a name="single-inheritance"></a>단일 상속

일반적인 상속 형식인 "단일 상속"에서 클래스에는 기본 클래스가 하나만 포함됩니다. 다음 그림에 나와 있는 관계를 살펴보십시오.

![기본 단일&#45;상속 그래프](../cpp/media/vc38xj1.gif "기본 단일&#45;상속 그래프") <br/>
간단한 단일 상속 그래프

그림에 나와 있는 일반적인 관계에서 구체적인 관계로의 진행 방식을 잘 살펴보십시오. 대부분의 클래스 계층 구조 디자인에서 확인할 수 있는 또 다른 공통적인 특성은, 파생 클래스와 기본 클래스 간에 "일종의" 관계가 있다는 것입니다. 그림에서 `Book`은 일종의 `PrintedDocument`이고 `PaperbackBook`은 일종의 `book`입니다.

그림에서 확인할 수 있는 또 한 가지 사항은, `Book`이 `PrintedDocument`에서 파생 클래스인 동시에 기본 클래스라는 것입니다(`PaperbackBook`이 `Book`에서 파생됨). 이러한 클래스 계층 구조의 기본적인 선언이 다음 예제에 나와 있습니다.

```cpp
// deriv_SingleInheritance.cpp
// compile with: /LD
class PrintedDocument {};

// Book is derived from PrintedDocument.
class Book : public PrintedDocument {};

// PaperbackBook is derived from Book.
class PaperbackBook : public Book {};
```

`PrintedDocument`는 `Book`의 "직접 기본" 클래스로 간주되며 `PaperbackBook`의 "간접 기본" 클래스입니다. 이 두 클래스 간의 차이점은 직접 기본 클래스의 경우 클래스 선언의 기본 목록에 표시되지만 간접 기본 클래스는 표시되지 않는다는 것입니다.

각 클래스가 파생되는 기본 클래스는 파생 클래스의 선언 이전에 선언됩니다. 기본 클래스에 대한 전방 참조 선언만을 제공하는 것으로는 부족하며 완전한 선언을 제공해야 합니다.

앞의 예제에서는 액세스 지정자를 **`public`** 사용 합니다. Public, protected 및 private 상속의 의미는 멤버 Access Control에 설명 되어 [있습니다.](../cpp/member-access-control-cpp.md)

다음 그림과 같이 클래스 하나를 여러 특정 클래스의 기본 클래스로 사용할 수 있습니다.

![방향성 비순환 그래프](../cpp/media/vc38xj2.gif "방향성 비순환 그래프") <br/>
방향이 있는 비순환 그래프 샘플

위의 다이어그램에 나와 있는 "DAG"("방향이 있는 비순환 그래프")에서 일부 클래스는 파생 클래스 두 개 이상의 기본 클래스입니다. 그러나 그 반대의 경우는 성립하지 않습니다. 즉, 지정된 파생 클래스의 직접 기본 클래스는 하나뿐입니다. 그림의 그래프는 "단일 상속" 구조체를 나타냅니다.

> [!NOTE]
> 방향이 있는 비순환 그래프는 단일 상속만을 고유하게 나타내지 않습니다. 즉, 다중 상속 그래프를 나타내는 데 사용되기도 합니다.

상속에서 파생 클래스는 기본 클래스의 멤버와 새로 추가하는 멤버를 포함합니다. 따라서 파생 클래스는 기본 클래스의 멤버를 참조할 수 있습니다(해당 멤버가 파생 클래스에서 다시 정의되는 경우는 제외). 이러한 멤버가 파생 클래스에서 다시 정의된 경우에는 범위 결정 연산자(`::`)를 사용하여 직접 또는 간접 기본 클래스의 멤버를 참조할 수 있습니다. 다음 예제를 고려해 보세요.

```cpp
// deriv_SingleInheritance2.cpp
// compile with: /EHsc /c
#include <iostream>
using namespace std;
class Document {
public:
   char *Name;   // Document name.
   void PrintNameOf();   // Print name.
};

// Implementation of PrintNameOf function from class Document.
void Document::PrintNameOf() {
   cout << Name << endl;
}

class Book : public Document {
public:
   Book( char *name, long pagecount );
private:
   long  PageCount;
};

// Constructor from class Book.
Book::Book( char *name, long pagecount ) {
   Name = new char[ strlen( name ) + 1 ];
   strcpy_s( Name, strlen(Name), name );
   PageCount = pagecount;
};
```

`Book`의 생성자(`Book::Book`)는 데이터 멤버 `Name`에 액세스할 수 있습니다. 프로그램에서는 `Book` 형식 개체를 만들어 다음과 같이 사용할 수 있습니다.

```cpp
//  Create a new object of type Book. This invokes the
//   constructor Book::Book.
Book LibraryBook( "Programming Windows, 2nd Ed", 944 );

...

//  Use PrintNameOf function inherited from class Document.
LibraryBook.PrintNameOf();
```

위의 예제에 나와 있는 것처럼 클래스 멤버와 상속된 데이터 및 함수는 동일하게 사용됩니다. 클래스 `Book`의 구현에서 `PrintNameOf` 함수를 다시 구현해야 하는 경우 `Document` 클래스에 속하는 함수는 범위 결정(`::`) 연산자를 통해서만 호출할 수 있습니다.

```cpp
// deriv_SingleInheritance3.cpp
// compile with: /EHsc /LD
#include <iostream>
using namespace std;

class Document {
public:
   char *Name;          // Document name.
   void  PrintNameOf() {}  // Print name.
};

class Book : public Document {
   Book( char *name, long pagecount );
   void PrintNameOf();
   long  PageCount;
};

void Book::PrintNameOf() {
   cout << "Name of book: ";
   Document::PrintNameOf();
}
```

액세스 가능하며 명확한 기본 클래스가 있으면 파생 클래스에 대한 참조 및 포인터를 암시적으로 해당 기본 클래스에 대한 참조 및 포인터로 변환할 수 있습니다. 다음 코드에서는 포인터를 사용하여 이 개념을 보여 줍니다. 참조에도 동일한 원칙이 적용됩니다.

```cpp
// deriv_SingleInheritance4.cpp
// compile with: /W3
struct Document {
   char *Name;
   void PrintNameOf() {}
};

class PaperbackBook : public Document {};

int main() {
   Document * DocLib[10];   // Library of ten documents.
   for (int i = 0 ; i < 5 ; i++)
      DocLib[i] = new Document;
   for (int i = 5 ; i < 10 ; i++)
      DocLib[i] = new PaperbackBook;
}
```

위의 예제에서는 여러 가지 형식이 작성됩니다. 그러나 이러한 형식은 모두 `Document` 클래스에서 파생되므로 `Document *`로의 암시적 변환이 수행됩니다. 따라서 `DocLib`는 여러 종류의 개체를 포함하는 "유형이 다른 목록", 즉 개체의 형식이 서로 다를 수 있는 목록입니다.

`Document` 클래스는 `PrintNameOf` 함수를 포함하므로 도서관에 있는 각 책의 이름을 인쇄할 수 있습니다. 그러나 `Book`의 페이지 수, `HelpFile`의 바이트 수 등 문서 형식과 관련된 일부 정보는 생략될 수 있습니다.

> [!NOTE]
> 기본 클래스를 강제로 적용하여 `PrintNameOf`와 같은 함수를 구현하는 방식은 최적의 디자인이 아닌 경우가 많습니다. [가상 함수](../cpp/virtual-functions.md) 는 다른 디자인 대안을 제공 합니다.
