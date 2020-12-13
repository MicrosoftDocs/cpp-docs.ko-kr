---
description: '자세한 정보: bad_typeid 예외'
title: bad_typeid 예외
ms.date: 10/04/2019
f1_keywords:
- bad_typeid
- bad_typeid_cpp
helpviewer_keywords:
- bad_typeid exception
- exceptions [C++], bad_typeid
ms.assetid: 5963ed58-4ede-4597-957d-f7bbd06299c2
ms.openlocfilehash: cdc582e2becba35b851bc3b6c2d68c877110068c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146265"
---
# <a name="bad_typeid-exception"></a>bad_typeid 예외

의 피연산자가 NULL 포인터인 경우에는 [typeid 연산자](../cpp/typeid-operator.md) 가 **bad_typeid** 예외를 throw 합니다 **`typeid`** .

## <a name="syntax"></a>구문

```
catch (bad_typeid)
   statement
```

## <a name="remarks"></a>설명

**Bad_typeid** 에 대 한 인터페이스는 다음과 같습니다.

```cpp
class bad_typeid : public exception
{
public:
   bad_typeid();
   bad_typeid(const char * _Message = "bad typeid");
   bad_typeid(const bad_typeid &);
   virtual ~bad_typeid();

   bad_typeid& operator=(const bad_typeid&);
   const char* what() const;
};
```

다음 예제에서는 **`typeid`** **bad_typeid** 예외를 throw 하는 연산자를 보여 줍니다.

```cpp
// expre_bad_typeid.cpp
// compile with: /EHsc /GR
#include <typeinfo>
#include <iostream>

class A{
public:
   // object for class needs vtable
   // for RTTI
   virtual ~A();
};

using namespace std;
int main() {
A* a = NULL;

try {
   cout << typeid(*a).name() << endl;  // Error condition
   }
catch (bad_typeid){
   cout << "Object is NULL" << endl;
   }
}
```

## <a name="output"></a>출력

```Output
Object is NULL
```

## <a name="see-also"></a>참조

[런타임 형식 정보](../cpp/run-time-type-information.md)\
[키워드](../cpp/keywords-cpp.md)
