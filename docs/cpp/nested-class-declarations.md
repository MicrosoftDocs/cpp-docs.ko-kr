---
description: '자세히 알아보기: 중첩 클래스 선언'
title: 중첩 클래스 선언
ms.date: 11/04/2016
helpviewer_keywords:
- classes [C++], declaring
- declarations, class
- nested classes [C++]
- nested classes [C++], declaring
- declaring classes [C++]
- declarations, nested classes
ms.assetid: c02e471d-b7f9-41b8-8ef6-2323f006dbd5
ms.openlocfilehash: 8247a969be59cb35752f141ea281a271de24f87b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313686"
---
# <a name="nested-class-declarations"></a>중첩 클래스 선언

클래스는 다른 클래스의 범위 내에서 선언될 수 있습니다. 이러한 클래스를 "중첩 클래스"라고 합니다. 중첩 클래스는 바깥쪽 클래스의 범위 내에 있는 것으로 간주되고 해당 범위 내에서 사용할 수 있습니다. 바로 바깥쪽 범위 이외의 범위에서 중첩 클래스를 참조하려면 정규화된 이름을 사용해야 합니다.

다음 예제에서는 중첩 클래스를 선언하는 방법을 보여 줍니다.

```cpp
// nested_class_declarations.cpp
class BufferedIO
{
public:
   enum IOError { None, Access, General };

   // Declare nested class BufferedInput.
   class BufferedInput
   {
   public:
      int read();
      int good()
      {
         return _inputerror == None;
      }
   private:
       IOError _inputerror;
   };

   // Declare nested class BufferedOutput.
   class BufferedOutput
   {
      // Member list
   };
};

int main()
{
}
```

`BufferedIO::BufferedInput` 및 `BufferedIO::BufferedOutput`은 `BufferedIO` 내에 선언됩니다. 이러한 클래스 이름은 `BufferedIO` 클래스의 범위 외부에서 표시되지 않습니다. 그러나 `BufferedIO` 형식의 개체에는 `BufferedInput` 또는 `BufferedOutput` 형식의 개체가 포함되지 않습니다.

중첩 클래스는 바깥쪽 클래스에서만 제공된 이름, 형식 이름, 정적 멤버의 이름 및 열거자를 직접 사용할 수 있습니다. 다른 클래스 멤버의 이름을 사용하려면 포인터, 참조 또는 개체 이름을 사용해야 합니다.

위의 `BufferedIO` 예제에서 `IOError` 함수에 표시된 것과 같이 중첩 클래스 `BufferedIO::BufferedInput` 또는 `BufferedIO::BufferedOutput`의 멤버 함수에서 `good` 열거형에 직접 액세스할 수 있습니다.

> [!NOTE]
> 중첩 클래스는 클래스 범위 내에서 형식만 선언하며, 중첩 클래스의 포함된 개체가 만들어지지는 않습니다. 위의 예제에서는 두 중첩 클래스를 선언하지만 이러한 클래스 형식의 개체는 선언하지 않습니다.

중첩 클래스 선언의 범위 표시 유형에 대한 예외는 형식 이름이 정방향 선언과 함께 선언된 경우입니다.  이 경우 정방향 선언에서 선언된 클래스 이름은 바깥쪽 클래스 외부에 표시되며 해당 범위는 가장 작은 바깥쪽 비클래스 범위로 정의됩니다.  예를 들어:

```cpp
// nested_class_declarations_2.cpp
class C
{
public:
    typedef class U u_t; // class U visible outside class C scope
    typedef class V {} v_t; // class V not visible outside class C
};

int main()
{
    // okay, forward declaration used above so file scope is used
    U* pu;

    // error, type name only exists in class C scope
    u_t* pu2; // C2065

    // error, class defined above so class C scope
    V* pv; // C2065

    // okay, fully qualified name
    C::V* pv2;
}
```

## <a name="access-privilege-in-nested-classes"></a>중첩 클래스에 대한 액세스 권한

클래스가 다른 클래스 안에 중첩되면 중첩된 클래스의 멤버 함수에 대해 특별한 액세스 권한이 부여되지 않습니다. 마찬가지로 바깥쪽 클래스의 멤버 함수는 중첩된 클래스의 멤버에 대해 특별한 액세스 권한이 없습니다.

## <a name="member-functions-in-nested-classes"></a>중첩 클래스의 멤버 함수

중첩 클래스에서 선언된 멤버 함수는 파일 범위에서 정의될 수 있습니다. 앞의 예제는 다음과 같이 작성될 수도 있습니다.

```cpp
// member_functions_in_nested_classes.cpp
class BufferedIO
{
public:
    enum IOError { None, Access, General };
    class BufferedInput
    {
    public:
        int read(); // Declare but do not define member
        int good(); //  functions read and good.
    private:
        IOError _inputerror;
    };

    class BufferedOutput
    {
        // Member list.
    };
};
// Define member functions read and good in
//  file scope.
int BufferedIO::BufferedInput::read()
{
   return(1);
}

int BufferedIO::BufferedInput::good()
{
    return _inputerror == None;
}
int main()
{
}
```

앞의 예제에서 정규화 된 *형식 이름* 구문은 함수 이름을 선언 하는 데 사용 됩니다. 다음 선언은

```cpp
BufferedIO::BufferedInput::read()
```

"`read` 클래스의 범위에 있는 `BufferedInput` 클래스의 멤버인 `BufferedIO` 함수"를 의미합니다. 이 선언은 *정규화 된 형식 이름* 구문을 사용 하기 때문에 다음과 같은 형식의 구문을 사용할 수 있습니다.

```cpp
typedef BufferedIO::BufferedInput BIO_INPUT;

int BIO_INPUT::read()
```

앞의 선언은 이전 선언과 동일 하지만 **`typedef`** 클래스 이름 대신 이름을 사용 합니다.

## <a name="friend-functions-in-nested-classes"></a>중첩 클래스의 Friend 함수

중첩 클래스에 선언된 friend 함수는 바깥쪽 클래스가 아닌 중첩 클래스 범위에 있다고 간주됩니다. 따라서 friend 함수는 바깥쪽 클래스의 멤버 또는 멤버 함수에 대해 특별한 액세스 권한이 없습니다. friend 함수가 파일 범위에 정의된 경우 friend 함수의 중첩 클래스에 선언된 이름을 사용하려면 다음과 같이 정규화된 형식 이름을 사용하세요.

```cpp
// friend_functions_and_nested_classes.cpp

#include <string.h>

enum
{
    sizeOfMessage = 255
};

char *rgszMessage[sizeOfMessage];

class BufferedIO
{
public:
    class BufferedInput
    {
    public:
        friend int GetExtendedErrorStatus();
        static char *message;
        static int  messageSize;
        int iMsgNo;
   };
};

char *BufferedIO::BufferedInput::message;
int BufferedIO::BufferedInput::messageSize;

int GetExtendedErrorStatus()
{
    int iMsgNo = 1; // assign arbitrary value as message number

    strcpy_s( BufferedIO::BufferedInput::message,
              BufferedIO::BufferedInput::messageSize,
              rgszMessage[iMsgNo] );

    return iMsgNo;
}

int main()
{
}
```

다음 코드에서는 friend 함수로 선언된 `GetExtendedErrorStatus` 함수를 보여 줍니다. 파일 범위에 정의된 함수에서는 메시지가 정적 배열에서 클래스 멤버로 복사됩니다. `GetExtendedErrorStatus`를 효과적으로 구현하려면 다음과 같이 선언하십시오.

```cpp
int GetExtendedErrorStatus( char *message )
```

이전의 인터페이스를 사용하면 여러 클래스에서 오류 메시지를 복사할 메모리 위치를 전달하여 이 함수의 서비스를 사용할 수 있습니다.

## <a name="see-also"></a>참조

[클래스 및 구조체](../cpp/classes-and-structs-cpp.md)
