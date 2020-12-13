---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4291'
title: 컴파일러 경고(수준 1) C4291
ms.date: 11/04/2016
f1_keywords:
- C4291
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
ms.openlocfilehash: 190fbb1ed91c5524dcd83a0a02a0b0280e264891
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340114"
---
# <a name="compiler-warning-level-1-c4291"></a>컴파일러 경고(수준 1) C4291

' 선언 ': 일치 하는 operator delete를 찾을 수 없습니다. 초기화에서 예외가 throw 되 면 메모리가 해제 되지 않습니다.

Placement [delete](../../cpp/delete-operator-cpp.md)가 없는 경우 placement [new](../../cpp/new-operator-cpp.md) 가 사용 됩니다.

연산자가 포함 된 개체에 대해 메모리를 할당 하면 **`new`** 개체의 생성자가 호출 됩니다. 생성자가 예외를 throw 하는 경우 개체에 할당 된 모든 메모리를 할당 취소 해야 합니다. **`delete`** 연산자와 일치 하는 operator 함수를 사용 하지 않는 경우이는 발생 하지 않습니다 **`new`** .

추가 인수 없이 연산자를 사용 하 **`new`** 고 [/Gx](../../build/reference/gx-enable-exception-handling.md), [/EHs](../../build/reference/eh-exception-handling-model.md)또는/eha 옵션으로 컴파일하여 예외 처리를 사용 하도록 설정 하는 경우 생성자가 예외를 throw 하는 경우 컴파일러는 연산자를 호출 하는 코드를 생성 합니다 **`delete`** .

연산자의 배치 형태를 사용 하는 경우 **`new`** (할당 크기 외에 인수를 포함 하는 폼), 개체의 생성자가 예외를 throw 하는 경우 컴파일러는 연산자를 호출 하는 코드를 생성 **`delete`** 하지만, 연산자의 배치 형식이 **`delete`** **`new`** 메모리를 할당 한 연산자의 배치 형식과 일치 하는 경우에만이 작업을 수행 합니다. 예를 들어:

```cpp
// C4291.cpp
// compile with: /EHsc /W1
#include <malloc.h>

class CList
{
public:
   CList(int)
   {
      throw "Fail!";
   }
};

void* operator new(size_t size, char* pszFilename, int nLine)
{
   return malloc(size);
}

int main(void)
{
   try
   {
      // This will call ::operator new(unsigned int) to allocate heap
      // memory. Heap memory pointed to by pList1 will automatically be
      // deallocated by a call to ::operator delete(void*) when
      // CList::CList(int) throws an exception.
      CList* pList1 = new CList(10);
   }
   catch (...)
   {
   }

   try
   {
      // This will call the overloaded ::operator new(size_t, char*, int)
      // to allocate heap memory. When CList::CList(int) throws an
      // exception, ::operator delete(void*, char*, int) should be called
      // to deallocate the memory pointed to by pList2. Since
      // ::operator delete(void*, char*, int) has not been implemented,
      // memory will be leaked when the deallocation cannot occur.
      CList* pList2 = new(__FILE__, __LINE__) CList(20);   // C4291
   }
   catch (...)
   {
   }
}
```

위의 예에서는 연산자 **`delete`** 의 배치 형태와 일치 하는 연산자의 배치 형식이 정의 되어 있지 않기 때문에 경고 C4291을 생성 합니다 **`new`** . 문제를 해결 하려면 **main** 위에 다음 코드를 삽입 합니다. 오버 로드 된 모든 연산자 **`delete`** 함수 매개 변수는 **`new`** 첫 번째 매개 변수를 제외 하 고 오버 로드 된 연산자의 매개 변수와 일치 합니다.

```cpp
void operator delete(void* pMem, char* pszFilename, int nLine)
{
   free(pMem);
}
```
