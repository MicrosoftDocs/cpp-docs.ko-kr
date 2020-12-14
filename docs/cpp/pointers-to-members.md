---
description: '자세한 정보: 멤버에 대 한 포인터'
title: pointers_to_members
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, pointers
- class members [C++], pointers to
- pointers, to members
- members [C++], pointers to
- pointers, declarations
ms.assetid: f42ddb79-9721-4e39-95b1-c56b55591f68
ms.openlocfilehash: e9c40ac8903aa61a808468ca18fa379c84f2fb81
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250116"
---
# <a name="pointers-to-members"></a>pointers_to_members

멤버에 대한 포인터 선언은 포인터 선언의 특별한 경우입니다.  다음 시퀀스를 사용 하 여 선언 됩니다.

> *저장소 클래스 지정자*<sub>opt</sub> *cv-*<sub>한정자 옵트인</sub> *형식-지정자* *밀리초-한정자*<sub>옵트인</sub> *정규화-이름* **`::*`** *cv-*<sub>한정자 옵트인</sub> *식별자* *pm-이니셜라이저*<sub>옵트인</sub>**`;`**

1. 선언 지정자:

   - 선택적 스토리지 클래스 지정자.

   - 선택적 **`const`** 및 **`volatile`** 지정자입니다.

   - 형식 지정자: 형식의 이름 클래스가 아니라 가리키는 멤버의 형식입니다.

1. 선언자:

   - 선택적 Microsoft 전용 한정자. 자세한 내용은 [Microsoft 전용 한정자](../cpp/microsoft-specific-modifiers.md)를 참조 하세요.

   - 가리킬 멤버가 포함된 클래스의 정규화된 이름입니다.

   - __`::`__ 연산자입니다.

   - __`*`__ 연산자입니다.

   - 선택적 **`const`** 및 **`volatile`** 지정자입니다.

   - 멤버에 대한 포인터의 이름을 지정하는 식별자

1. 선택적 멤버 포인터 이니셜라이저:

   - **`=`** 연산자입니다.

   - **`&`** 연산자입니다.

   - 클래스의 정규화된 이름

   - __`::`__ 연산자입니다.

   - 적절 한 형식의 클래스에 대 한 비정적 멤버의 이름입니다.

항상 그렇듯이 여러 선언자(및 모든 관련 이니셜라이저)가 단일 선언에서 허용됩니다. 멤버에 대 한 포인터는 클래스의 정적 멤버, 참조 형식의 멤버 또는을 가리킬 수 없습니다 **`void`** .

클래스의 멤버에 대 한 포인터는 일반 포인터와 다릅니다. 멤버의 형식과 멤버가 속한 클래스에 대 한 형식 정보가 모두 있습니다. 일반 포인터는 메모리에 있는 단일 개체만 식별합니다(해당 개체의 주소를 포함함). 클래스의 멤버에 대한 포인터는 클래스의 모든 인스턴스에서 해당 멤버를 식별합니다. 다음 예제에서는 `Window` 클래스와 멤버 데이터에 대한 몇 가지 포인터를 선언합니다.

```cpp
// pointers_to_members1.cpp
class Window
{
public:
   Window();                               // Default constructor.
   Window( int x1, int y1,                 // Constructor specifying
   int x2, int y2 );                       // Window size.
   bool SetCaption( const char *szTitle ); // Set window caption.
   const char *GetCaption();               // Get window caption.
   char *szWinCaption;                     // Window caption.
};

// Declare a pointer to the data member szWinCaption.
char * Window::* pwCaption = &Window::szWinCaption;
int main()
{
}
```

앞의 예제에서 `pwCaption` 는 형식의 클래스 멤버에 대 한 포인터입니다 `Window` **`char*`** . `pwCaption`의 형식은 `char * Window::*`입니다. 다음 코드에서는 `SetCaption` 및 `GetCaption` 멤버 함수에 대한 포인터를 선언합니다.

```cpp
const char * (Window::* pfnwGC)() = &Window::GetCaption;
bool (Window::* pfnwSC)( const char * ) = &Window::SetCaption;
```

`pfnwGC` 및 `pfnwSC` 포인터는 `GetCaption` 클래스의 `SetCaption` 및 `Window`을 각각 가리킵니다. 이 코드에서는 멤버에 대한 포인터 `pwCaption`을 직접 사용하여 창 캡션에 정보를 복사합니다.

```cpp
Window  wMainWindow;
Window *pwChildWindow = new Window;
char   *szUntitled    = "Untitled -  ";
int     cUntitledLen  = strlen( szUntitled );

strcpy_s( wMainWindow.*pwCaption, cUntitledLen, szUntitled );
(wMainWindow.*pwCaption)[cUntitledLen - 1] = '1';     // same as
// wMainWindow.SzWinCaption [cUntitledLen - 1] = '1';
strcpy_s( pwChildWindow->*pwCaption, cUntitledLen, szUntitled );
(pwChildWindow->*pwCaption)[cUntitledLen - 1] = '2'; // same as
// pwChildWindow->szWinCaption[cUntitledLen - 1] = '2';
```

연산자는 **`.*`** **`->*`** **`.*`** 개체 또는 개체 참조에 지정 된 멤버를 선택 하는 반면 연산자는 포인터를 통해 멤버를 선택 하는 반면 및 연산자 (멤버 포인터 연산자)의 차이점은 연산자가 멤버를 선택 하는 것입니다 **`->*`** . 이러한 연산자에 대 한 자세한 내용은 [멤버 포인터 연산자가 있는 식](../cpp/pointer-to-member-operators-dot-star-and-star.md)을 참조 하세요.

멤버 포인터 연산자의 결과는 멤버의 형식입니다. 이 예제의 경우 `char *`입니다.

다음 코드에서는 멤버에 대한 포인터를 사용하여 `GetCaption` 및 `SetCaption` 멤버 함수를 호출합니다.

```cpp
// Allocate a buffer.
enum {
    sizeOfBuffer = 100
};
char szCaptionBase[sizeOfBuffer];

// Copy the main window caption into the buffer
//  and append " [View 1]".
strcpy_s( szCaptionBase, sizeOfBuffer, (wMainWindow.*pfnwGC)() );
strcat_s( szCaptionBase, sizeOfBuffer, " [View 1]" );
// Set the child window's caption.
(pwChildWindow->*pfnwSC)( szCaptionBase );
```

## <a name="restrictions-on-pointers-to-members"></a>멤버에 대한 포인터 제한

정적 멤버의 주소는 멤버에 대 한 포인터가 아닙니다. 정적 멤버의 한 인스턴스에 대 한 일반 포인터입니다. 지정 된 클래스의 모든 개체에 대해 정적 멤버의 인스턴스가 하나만 존재 합니다. 즉, 일반 주소 ( **&** ) 및 역참조 () 연산자를 사용할 수 있습니다 <strong>\*</strong> .

## <a name="pointers-to-members-and-virtual-functions"></a>멤버 및 가상 함수에 대한 포인터

멤버 포인터 함수를 통해 가상 함수를 호출 하는 것은 함수가 직접 호출 된 것 처럼 작동 합니다. 올바른 함수는 v 테이블에서 조회 되 고를 호출 합니다.

가상 함수 작업은 항상 기본 클래스 포인터를 통해 호출합니다. 가상 함수에 대 한 자세한 내용은 [가상 함수](../cpp/virtual-functions.md)를 참조 하세요.

다음 코드에서는 멤버 포인터 함수를 통해 가상 함수를 호출하는 방법을 보여 줍니다.

```cpp
// virtual_functions.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

class Base
{
public:
    virtual void Print();
};
void (Base::* bfnPrint)() = &Base::Print;
void Base::Print()
{
    cout << "Print function for class Base" << endl;
}

class Derived : public Base
{
public:
    void Print();  // Print is still a virtual function.
};

void Derived::Print()
{
    cout << "Print function for class Derived" << endl;
}

int main()
{
    Base   *bPtr;
    Base    bObject;
    Derived dObject;
    bPtr = &bObject;    // Set pointer to address of bObject.
    (bPtr->*bfnPrint)();
    bPtr = &dObject;    // Set pointer to address of dObject.
    (bPtr->*bfnPrint)();
}

// Output:
// Print function for class Base
// Print function for class Derived
```
