---
title: '방법: 정의 이동 생성자 및 이동 할당 연산자 (c + +) | Microsoft Docs'
ms.custom: ''
ms.date: 03/05/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- move constructor [C++]
ms.assetid: e75efe0e-4b74-47a9-96ed-4e83cfc4378d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af1220cbb6b872ebd0370cfa526aba47338e70e6
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/13/2018
ms.locfileid: "39028153"
---
# <a name="move-constructors-and-move-assignment-operators-c"></a>이동 생성자 및 이동 할당 연산자(C++)
이 항목에서는 작성 하는 방법에 설명 합니다는 *이동 생성자* 와 c + + 클래스에 대 한 이동 할당 연산자입니다. 이동 생성자는 rvalue lvalue로 복사 하지 않고 이동 될 개체를 소유한 리소스 수 있습니다. 이동 의미 체계에 대 한 자세한 내용은 참조 하세요. [Rvalue 참조 선언 자: & &](../cpp/rvalue-reference-declarator-amp-amp.md)합니다.  
  
 이 항목은 메모리 버퍼를 관리하는 다음 C++클래스 `MemoryBlock`을 기반으로 합니다.  
  
```cpp  
// MemoryBlock.h  
#pragma once  
#include <iostream>  
#include <algorithm>  
  
class MemoryBlock  
{  
public:  
  
   // Simple constructor that initializes the resource.  
   explicit MemoryBlock(size_t length)  
      : _length(length)  
      , _data(new int[length])  
   {  
      std::cout << "In MemoryBlock(size_t). length = "  
                << _length << "." << std::endl;  
   }  
  
   // Destructor.  
   ~MemoryBlock()  
   {  
      std::cout << "In ~MemoryBlock(). length = "  
                << _length << ".";  
  
      if (_data != nullptr)  
      {  
         std::cout << " Deleting resource.";  
         // Delete the resource.  
         delete[] _data;  
      }  
  
      std::cout << std::endl;  
   }  
  
   // Copy constructor.  
   MemoryBlock(const MemoryBlock& other)  
      : _length(other._length)  
      , _data(new int[other._length])  
   {  
      std::cout << "In MemoryBlock(const MemoryBlock&). length = "   
                << other._length << ". Copying resource." << std::endl;  
  
      std::copy(other._data, other._data + _length, _data);  
   }  
  
   // Copy assignment operator.  
   MemoryBlock& operator=(const MemoryBlock& other)  
   {  
      std::cout << "In operator=(const MemoryBlock&). length = "   
                << other._length << ". Copying resource." << std::endl;  
  
      if (this != &other)  
      {  
         // Free the existing resource.  
         delete[] _data;  
  
         _length = other._length;  
         _data = new int[_length];  
         std::copy(other._data, other._data + _length, _data);  
      }  
      return *this;  
   }  
  
   // Retrieves the length of the data resource.  
   size_t Length() const  
   {  
      return _length;  
   }  
  
private:  
   size_t _length; // The length of the resource.  
   int* _data; // The resource.  
};  
```  
  
 다음 절차에서는 예제 C++ 클래스에 대한 이동 생성자와 이동 할당 연산자를 작성하는 방법을 설명합니다.  
  
### <a name="to-create-a-move-constructor-for-a-c-class"></a>C++ 클래스에 대한 이동 생성자를 만들려면  
  
1.  다음 예제와 같이 클래스 형식에 대한 rvalue 참조를 매개 변수로 사용하는 빈 생성자 메서드를 정의합니다.  
  
    ```cpp  
    MemoryBlock(MemoryBlock&& other)  
       : _data(nullptr)  
       , _length(0)  
    {  
    }  
    ```  
  
2.  이동 생성자에서 소스 개체의 클래스 데이터 멤버를 생성될 개체에 할당합니다.  
  
    ```cpp  
    _data = other._data;  
    _length = other._length;  
    ```  
  
3.  소스 개체의 데이터 멤버를 기본 값에 할당합니다. 이에 따라 소멸자가 리소스(예: 메모리)를 여러 번 해제하는 것이 방지됩니다.  
  
    ```cpp  
    other._data = nullptr;  
    other._length = 0;  
    ```  
  
### <a name="to-create-a-move-assignment-operator-for-a-c-class"></a>C++ 클래스에 대한 이동 할당 연산자를 만들려면  

1.  다음 예제와 같이 클래스 형식에 대한 rvalue 참조를 매개 변수로 사용하고 클래스 형식에 대한 참조를 반환하는 빈 할당 연산자를 정의합니다.  
  
    ```cpp  
    MemoryBlock& operator=(MemoryBlock&& other)  
    {  
    }  
    ```  
  
2.  이동 할당 연산자에서 개체를 자체에 할당하려는 경우 작업을 수행하지 않는 조건문을 추가합니다.  
  
    ```cpp  
    if (this != &other)  
    {  
    }  
    ```  
  
3.  조건문에서 할당될 개체로부터 모든 리소스(예: 메모리)를 해제합니다.  
  
     다음 예제에서는 할당될 개체로부터 `_data` 멤버를 해제합니다.  
  
    ```cpp  
    // Free the existing resource.  
    delete[] _data;  
    ```  
  
     첫 번째 절차의 2-3단계에 따라 소스 개체의 데이터 멤버를 생성할 개체로 전송합니다.  
  
    ```cpp  
    // Copy the data pointer and its length from the   
    // source object.  
    _data = other._data;  
    _length = other._length;  
  
    // Release the data pointer from the source object so that  
    // the destructor does not free the memory multiple times.  
    other._data = nullptr;  
    other._length = 0;  
    ```  
  
4.  다음 예제와 같이 현재 개체에 대한 참조를 반환합니다.  
  
    ```cpp  
    return *this;  
    ```  
  
## <a name="example"></a>예  
 다음 예제에서는 `MemoryBlock` 클래스에 대한 완전한 이동 생성자와 이동 할당 연산자를 보여 줍니다.  
  
```cpp  
// Move constructor.  
MemoryBlock(MemoryBlock&& other)  
   : _data(nullptr)  
   , _length(0)  
{  
   std::cout << "In MemoryBlock(MemoryBlock&&). length = "   
             << other._length << ". Moving resource." << std::endl;  
  
   // Copy the data pointer and its length from the   
   // source object.  
   _data = other._data;  
   _length = other._length;  
  
   // Release the data pointer from the source object so that  
   // the destructor does not free the memory multiple times.  
   other._data = nullptr;  
   other._length = 0;  
}  
  
// Move assignment operator.  
MemoryBlock& operator=(MemoryBlock&& other)  
{  
   std::cout << "In operator=(MemoryBlock&&). length = "   
             << other._length << "." << std::endl;  
  
   if (this != &other)  
   {  
      // Free the existing resource.  
      delete[] _data;  
  
      // Copy the data pointer and its length from the   
      // source object.  
      _data = other._data;  
      _length = other._length;  
  
      // Release the data pointer from the source object so that  
      // the destructor does not free the memory multiple times.  
      other._data = nullptr;  
      other._length = 0;  
   }  
   return *this;  
}  
```  
  
## <a name="example"></a>예  
 다음 예제에서는 이동 의미 체계를 통해 응용 프로그램의 성능을 향상시키는 방법을 보여 줍니다. 이 예제에서는 벡터 개체에 두 요소를 추가한 다음 기존의 두 요소 사이에 새 요소를 삽입합니다. `vector` 클래스는 이동 의미 체계를 복사 하는 대신 벡터의 요소를 이동 하 여 삽입 작업을 효율적으로 수행 합니다.  
  
```cpp  
// rvalue-references-move-semantics.cpp  
// compile with: /EHsc  
#include "MemoryBlock.h"  
#include <vector>  
  
using namespace std;  
  
int main()  
{  
   // Create a vector object and add a few elements to it.  
   vector<MemoryBlock> v;  
   v.push_back(MemoryBlock(25));  
   v.push_back(MemoryBlock(75));  
  
   // Insert a new element into the second position of the vector.  
   v.insert(v.begin() + 1, MemoryBlock(50));  
}  
```  
  
 이 예제는 다음과 같은 출력을 생성합니다.  
  
```  
In MemoryBlock(size_t). length = 25.  
In MemoryBlock(MemoryBlock&&). length = 25. Moving resource.  
In ~MemoryBlock(). length = 0.  
In MemoryBlock(size_t). length = 75.  
In MemoryBlock(MemoryBlock&&). length = 25. Moving resource.  
In ~MemoryBlock(). length = 0.  
In MemoryBlock(MemoryBlock&&). length = 75. Moving resource.  
In ~MemoryBlock(). length = 0.  
In MemoryBlock(size_t). length = 50.  
In MemoryBlock(MemoryBlock&&). length = 50. Moving resource.  
In MemoryBlock(MemoryBlock&&). length = 50. Moving resource.  
In operator=(MemoryBlock&&). length = 75.  
In operator=(MemoryBlock&&). length = 50.  
In ~MemoryBlock(). length = 0.  
In ~MemoryBlock(). length = 0.  
In ~MemoryBlock(). length = 25. Deleting resource.  
In ~MemoryBlock(). length = 50. Deleting resource.  
In ~MemoryBlock(). length = 75. Deleting resource.  
```  
  
 Visual Studio 2010 이전이 예제에서는 다음과 같은 출력이 생성 됩니다.  
  
```  
In MemoryBlock(size_t). length = 25.  
In MemoryBlock(const MemoryBlock&). length = 25. Copying resource.  
In ~MemoryBlock(). length = 25. Deleting resource.  
In MemoryBlock(size_t). length = 75.  
In MemoryBlock(const MemoryBlock&). length = 25. Copying resource.  
In ~MemoryBlock(). length = 25. Deleting resource.  
In MemoryBlock(const MemoryBlock&). length = 75. Copying resource.  
In ~MemoryBlock(). length = 75. Deleting resource.  
In MemoryBlock(size_t). length = 50.  
In MemoryBlock(const MemoryBlock&). length = 50. Copying resource.  
In MemoryBlock(const MemoryBlock&). length = 50. Copying resource.  
In operator=(const MemoryBlock&). length = 75. Copying resource.  
In operator=(const MemoryBlock&). length = 50. Copying resource.  
In ~MemoryBlock(). length = 50. Deleting resource.  
In ~MemoryBlock(). length = 50. Deleting resource.  
In ~MemoryBlock(). length = 25. Deleting resource.  
In ~MemoryBlock(). length = 50. Deleting resource.  
In ~MemoryBlock(). length = 75. Deleting resource.  
```  
  
 이동 의미 체계를 사용하는 이 예제의 버전은 이동 의미 체계를 사용하지 않는 버전보다 적은 복사, 메모리 할당 및 메모리 할당 취소 작업을 수행하기 때문에 효율적입니다.  
  
## <a name="robust-programming"></a>강력한 프로그래밍  
 리소스 누수를 방지하려면 항상 이동 할당 연산자에서 메모리, 파일 핸들 및 소켓과 같은 리소스를 해제합니다.  
  
 리소스의 복구할 수 없는 소멸을 방지하려면 이동 할당 연산자에서 자체 할당을 적절하게 처리합니다.  
  
 사용자 클래스에 이동 생성자와 이동 할당 연산자를 둘 다 제공하는 경우 이동 할당 연산자를 호출하는 이동 생성자를 작성하여 중복 코드를 제거할 수 있습니다. 다음 예제에서는 이동 할당 연산자를 호출하는 이동 생성자의 수정된 버전을 보여 줍니다.  
  
```cpp
  
// Move constructor.  
MemoryBlock(MemoryBlock&& other)  
   : _data(nullptr)  
   , _length(0)  
{  
   *this = std::move(other);  
}  
```  
  
 합니다 [std:: move](../standard-library/utility-functions.md#move) 변수의 rvalue 속성을 유지 하는 함수는 *다른* 매개 변수입니다.  
  
## <a name="see-also"></a>참고 항목  
 [Rvalue 참조 선언 자: & &](../cpp/rvalue-reference-declarator-amp-amp.md)   
 [\<유틸리티 > 이동](http://msdn.microsoft.com/abef7e85-9dd6-4724-85da-d7f7fe95dca9)