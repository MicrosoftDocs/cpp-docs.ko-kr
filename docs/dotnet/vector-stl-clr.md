---
title: vector (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector
- cliext::operator!=
- cliext::operator<
- cliext::operator<=
- cliext::operator==
- cliext::operator>
- cliext::operator>=
- cliext::vector::assign
- cliext::vector::at
- cliext::vector::back
- cliext::vector::back_item
- cliext::vector::begin
- cliext::vector::capacity
- cliext::vector::clear
- cliext::vector::const_iterator
- cliext::vector::const_reference
- cliext::vector::const_reverse_iterator
- cliext::vector::difference_type
- cliext::vector::empty
- cliext::vector::end
- cliext::vector::erase
- cliext::vector::front
- cliext::vector::front_item
- cliext::vector::generic_container
- cliext::vector::generic_iterator
- cliext::vector::generic_reverse_iterator
- cliext::vector::generic_value
- cliext::vector::insert
- cliext::vector::iterator
- cliext::vector::operator=
- cliext::vector::operator
- cliext::vector::pop_back
- cliext::vector::push_back
- cliext::vector::rbegin
- cliext::vector::reference
- cliext::vector::rend
- cliext::vector::reserve
- cliext::vector::resize
- cliext::vector::reverse_iterator
- cliext::vector::size
- cliext::vector::size_type
- cliext::vector::swap
- cliext::vector::to_array
- cliext::vector::value_type
- cliext::vector::vector
dev_langs:
- C++
helpviewer_keywords:
- vector class [STL/CLR]
- <cliext/vector> header [STL/CLR]
- <vector> header [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> (vector) member [STL/CLR]
- operator>= member [STL/CLR]
- assign member [STL/CLR]
- at member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- capacity member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- erase member [STL/CLR]
- front member [STL/CLR]
- front_item member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- operator= member [STL/CLR]
- operator member [STL/CLR]
- pop_back member [STL/CLR]
- push_back member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reserve member [STL/CLR]
- resize member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- value_type member [STL/CLR]
- vector member [STL/CLR]
ms.assetid: f90060d5-097a-4e9d-9a26-a634b5b9c6c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5d5b3e94b0b594174538aebe6542b04df7214f1b
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079814"
---
# <a name="vector-stlclr"></a>vector(STL/CLR)
템플릿 클래스는 임의 액세스를 가진 요소의 다양 한 길이의 시퀀스를 제어 하는 개체를 설명 합니다. 컨테이너를 사용 하 여 `vector` 저장소의 연속 블록으로 요소의 시퀀스를 관리할 수 있습니다. 블록 요구에 맞게 증가 하는 배열을로 구현 됩니다.  
  
 아래 설명에 `GValue` 동일 `Value` 후자 형식인 ref 하지 않는 한 경우에서 이기 `Value^`합니다.  
  
## <a name="syntax"></a>구문  
  
```  
template<typename Value>  
    ref class vector  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IVector<GValue>  
    { ..... };  
```  
  
### <a name="parameters"></a>매개 변수  
 값  
 제어되는 시퀀스의 요소 형식입니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<cliext/벡터 >  
  
 **Namespace:** cliext  

## <a name="declarations"></a>선언  
  
|형식 정의|설명|  
|---------------------|-----------------|  
|[vector::const_iterator(STL/CLR)](#const_iterator)|제어되는 시퀀스에 대한 상수 반복기의 형식입니다.|  
|[vector::const_reference(STL/CLR)](#const_reference)|요소에 대한 상수 참조의 형식입니다.|  
|[vector::const_reverse_iterator(STL/CLR)](#const_reverse_iterator)|제어되는 시퀀스에 대한 상수 역방향 반복기의 형식입니다.|  
|[vector::difference_type(STL/CLR)](#difference_type)|두 요소 사이의 부호가 있는 거리의 형식입니다.|  
|[vector::generic_container(STL/CLR)](#generic_container)|컨테이너에 대 한 제네릭 인터페이스의 형식입니다.|  
|[vector::generic_iterator(STL/CLR)](#generic_iterator)|컨테이너에 대 한 제네릭 인터페이스에 대 한 반복기의 형식입니다.|  
|[vector::generic_reverse_iterator(STL/CLR)](#generic_reverse_iterator)|컨테이너에 대 한 제네릭 인터페이스에 대 한 반대 반복기의 형식입니다.|  
|[vector::generic_value(STL/CLR)](#generic_value)|컨테이너에 대 한 제네릭 인터페이스에 대 한 요소의 형식입니다.|  
|[vector::iterator(STL/CLR)](#iterator)|제어되는 시퀀스에 대한 반복기의 형식입니다.|  
|[vector::reference(STL/CLR)](#reference)|요소에 대한 참조의 형식입니다.|  
|[vector::reverse_iterator(STL/CLR)](#reverse_iterator)|제어되는 시퀀스에 대한 반대 반복기의 형식입니다.|  
|[vector::size_type(STL/CLR)](#size_type)|두 요소 사이의 부호가 있는 거리의 형식입니다.|  
|[vector::value_type(STL/CLR)](#value_type)|요소의 형식입니다.|  
  
|멤버 함수|설명|  
|---------------------|-----------------|  
|[vector::assign(STL/CLR)](#assign)|모든 요소를 바꿉니다.|  
|[vector::at(STL/CLR)](#at)|지정된 위치에 있는 요소에 액세스합니다.|  
|[vector::back(STL/CLR)](#back)|마지막 요소에 액세스합니다.|  
|[vector::begin(STL/CLR)](#begin)|제어되는 시퀀스의 시작을 지정합니다.|  
|[vector::capacity(STL/CLR)](#capacity)|컨테이너에 할당 된 저장소의 크기를 보고합니다.|  
|[vector::clear(STL/CLR)](#clear)|모든 요소를 제거합니다.|  
|[vector::empty(STL/CLR)](#empty)|요소가 있는지 여부를 테스트합니다.|  
|[vector::end(STL/CLR)](#end)|제어되는 시퀀스의 끝을 지정합니다.|  
|[vector::erase(STL/CLR)](#erase)|지정된 위치에 있는 요소를 제거합니다.|  
|[vector::front(STL/CLR)](#front)|첫 번째 요소에 액세스합니다.|  
|[vector::insert(STL/CLR)](#insert)|지정된 된 위치에 요소를 추가합니다.|  
|[vector::pop_back(STL/CLR)](#pop_back)|마지막 요소를 제거 합니다.|  
|[vector::push_back(STL/CLR)](#push_back)|새 마지막 요소를 추가 합니다.|  
|[vector::rbegin(STL/CLR)](#rbegin)|제어되는 역방향 시퀀스의 시작을 지정합니다.|  
|[vector::rend(STL/CLR)](#rend)|제어되는 역방향 시퀀스의 끝을 지정합니다.|  
|[vector::reserve(STL/CLR)](#reserve)|컨테이너에 대 한 최소 증가 용량을 보장합니다.|  
|[vector::resize(STL/CLR)](#resize)|요소의 수를 변경합니다.|  
|[vector::size(STL/CLR)](#size)|요소 수를 계산합니다.|  
|[vector::swap(STL/CLR)](#swap)|두 컨테이너의 내용을 바꿉니다.|  
|[vector::to_array(STL/CLR)](#to_array)|제어 되는 새 배열에 복사합니다.|  
|[vector::vector(STL/CLR)](#vector)|컨테이너 개체를 만듭니다.|  
  
|속성|설명|  
|--------------|-----------------|  
|[vector::back_item(STL/CLR)](#back_item)|마지막 요소에 액세스합니다.|  
|[vector::front_item(STL/CLR)](#front_item)|첫 번째 요소에 액세스합니다.|  
  
|연산자|설명|  
|--------------|-----------------|  
|[vector::operator=(STL/CLR)](#op_as)|제어되는 시퀀스를 바꿉니다.|  
|[vector::operator(STL/CLR)](#op)|지정된 위치에 있는 요소에 액세스합니다.|  
|[operator!= (vector)(STL/CLR)](#op_neq)|있는지 여부를 확인 한 `vector` 개체가 다른과 같지 않습니다. `vector` 개체입니다.|  
|[operator< (vector)(STL/CLR)](#op_lt)|있는지 여부를 확인 한 `vector` 개체를 사용 하면 다른 노드보다 작은지 `vector` 개체입니다.|  
|[operator<= (vector)(STL/CLR)](#op_lteq)|있는지 여부를 확인 한 `vector` 개체 보다 작거나 같으면 다른 `vector` 개체입니다.|  
|[operator== (vector)(STL/CLR)](#op_eq)|있는지 여부를 확인 한 `vector` 개체는 다른 `vector` 개체입니다.|  
|[operator> (vector)(STL/CLR)](#op_gt)|있는지 여부를 확인 한 `vector` 개체가 다른 노드보다 큰지 `vector` 개체입니다.|  
|[operator>= (vector)(STL/CLR)](#op_gteq)|있는지 여부를 확인 한 `vector` 개체는 다른 보다 크거나 `vector` 개체입니다.|  
  
## <a name="interfaces"></a>인터페이스  
  
|인터페이스|설명|  
|---------------|-----------------|  
|<xref:System.ICloneable>|개체를 복제 합니다.|  
|<xref:System.Collections.IEnumerable>|요소를 통해 시퀀스입니다.|  
|<xref:System.Collections.ICollection>|요소의 그룹을 유지 합니다.|  
|<xref:System.Collections.Generic.IEnumerable%601>|형식화 된 요소 시퀀스입니다.|  
|<xref:System.Collections.Generic.ICollection%601>|형식화 된 요소의 그룹을 유지 합니다.|  
|<xref:System.Collections.Generic.IList%601>|형식화 된 요소의 순서가 지정 된 그룹을 유지 합니다.|  
|IVector < 값\>|제네릭 컨테이너를 유지 합니다.|  
  
## <a name="remarks"></a>설명  
 개체 할당 및 제어의 배열을 저장 하는 시퀀스에 대 한 저장소를 해제 `Value` 요구에 맞게 증가 하는 요소입니다. 증가 하는 새 요소를 추가 비용이 분할 상환된 상수 시간 하는 방식으로 발생 합니다. 즉, 끝에 요소를 추가 하는 비용 증가 하지 않습니다, 평균적으로 더 큰 제어 되는 시퀀스 가져옵니다의 길이로 합니다. 따라서 벡터는 적합 한 템플릿 클래스에 대 한 기본 컨테이너 [stack (STL/CLR)](../dotnet/stack-stl-clr.md)합니다.  
  
 A `vector` 즉, 첫 번째 (앞) 요소에 대 한 0에서 계산한 직접 숫자의 위치를 지정 하는 요소를 참조할 수는 지원 임의 액세스 반복기 `size() - 1` 마지막 (뒤로) 요소에 대 한 합니다. 또한 벡터에 적합 한 템플릿 클래스에 대 한 기본 컨테이너 임을 의미 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)합니다.  
  
 벡터 반복기를 지정 하는 요소에 대 한 바이어스 함께 해당 관련된 벡터 개체에 대 한 핸들을 저장 합니다. 반복기의 관련된 컨테이너 개체와만 사용할 수 있습니다. 벡터 요소의 바이어스의 위치와 같습니다.  
  
 삽입 또는 요소를 지운 반복기에서 지정 된 값도 변경할 수 있도록 지정된 된 위치에 저장 된 요소 값을 변경할 수 있습니다. (컨테이너 요소를 복사 또는 삽입 하기 전에 구멍을 생성 또는 삭제 한 후 구멍을 채울 아래쪽에 있을 수 있습니다.) 그럼에도 불구 하 고 벡터 반복기 유효 범위에 경우에 바이어스 `[0, size()]`합니다. 또한 유효한 반복기 dereferencable 남아-액세스 하거나 해당 바이어스과 같지 않은으로 지정-요소 값을 변경 하는 사용할 수 있습니다 `size()`합니다.  
  
 지우거 나 요소를 제거 합니다. 저장된 된 값에 대 한 소멸자를 호출 합니다. 컨테이너를 제거 합니다. 모든 요소를 지웁니다. 따라서 요소 형식이 ref 클래스는 컨테이너 보다 수명이 깁니다 컨테이너 요소가 있는지 확인 합니다. 단, 컨테이너 핸들의 해당 요소를 제거 하지 않습니다.  
  
## <a name="members"></a>멤버

## <a name="assign"></a> vector:: assign (STL/CLR)
모든 요소를 바꿉니다.  
  
### <a name="syntax"></a>구문  
  
```  
void assign(size_type count, value_type val);  
template<typename InIt>  
    void assign(InIt first, InIt last);  
void assign(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>매개 변수  
 count  
 삽입할 요소의 수입니다.  
  
 첫 번째  
 삽입할 범위의의 시작입니다.  
  
 last  
 삽입할 범위의 끝입니다.  
  
 오른쪽  
 삽입 하는 열거형입니다.  
  
 Val  
 삽입할 요소의 값입니다.  
  
### <a name="remarks"></a>설명  
 첫 번째 멤버 함수는 반복 된 제어 되는 시퀀스 바꿉니다 `count` 값의 요소 `val`합니다. 하면을 채우는 데 사용할 컨테이너 요소와 동일한 값이 모두 포함 합니다.  
  
 경우 `InIt` 정수 형식, 두 번째 멤버 함수는 동일 하 게 동작 `assign((size_type)first, (value_type)last)`합니다. 제어 되는 순서와 대체 그렇지 않으면 [`first`, `last`). 사용할 있습니다 제어 된 시퀀스 복사본 되도록 다른 시퀀스.  
  
 열거자에 지정 된 시퀀스와 제어 된 시퀀스를 대체 하는 세 번째 멤버 함수 `right`합니다. 제어 되는 시퀀스의 사본을 열거형에서 설명 하는 순서를 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_assign.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// assign a repetition of values   
    cliext::vector<wchar_t> c2;   
    c2.assign(6, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an iterator range   
    c2.assign(c1.begin(), c1.end() - 1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an enumeration   
    c2.assign(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
x x x x x x  
a b  
a b c  
```  

## <a name="at"></a> vector:: at (STL/CLR)
지정된 위치에 있는 요소에 액세스합니다.  
  
### <a name="syntax"></a>구문  
  
```  
reference at(size_type pos);  
```  
  
#### <a name="parameters"></a>매개 변수  
 위치  
 액세스할 요소의 위치입니다.  
  
### <a name="remarks"></a>설명  
 멤버 함수는 위치에서 제어 된 시퀀스의 요소에 대 한 참조를 반환 `pos`합니다. 읽기 또는 쓰기 요소 위치를 알아야 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_at.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using at   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// change an entry and redisplay   
    c1.at(1) = L'x';   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a x c  
```  

## <a name="back"></a> vector:: back (STL/CLR)
마지막 요소에 액세스합니다.  
  
### <a name="syntax"></a>구문  
  
```  
reference back();  
```  
  
### <a name="remarks"></a>설명  
 멤버 함수는 비어 있어야 하는 제어 된 시퀀스의 마지막 요소에 대 한 참조를 반환 합니다. 존재 하는 것을 알고 있는 경우 마지막 요소를 액세스 하려면 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_back.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("back() = {0}", c1.back());   
  
// alter last item and reinspect   
    c1.back() = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
back() = c  
 a b x  
```  

## <a name="back_item"></a> vector:: back_item (STL/CLR)
마지막 요소에 액세스합니다.  
  
### <a name="syntax"></a>구문  
  
```  
property value_type back_item;  
```  
  
### <a name="remarks"></a>설명  
 비어 있는 제어 된 시퀀스의 마지막 요소를 액세스 하는 속성입니다. 읽기 또는 존재 하는 것을 알고 있는 경우 마지막 요소를 쓰기 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_back_item.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("back_item = {0}", c1.back_item);   
  
// alter last item and reinspect   
    c1.back_item = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
back_item = c  
 a b x  
```  

## <a name="begin"></a> vector:: begin (STL/CLR)
제어되는 시퀀스의 시작을 지정합니다.  
  
### <a name="syntax"></a>구문  
  
```  
iterator begin();  
```  
  
### <a name="remarks"></a>설명  
 멤버 함수는 제어 되는 시퀀스 또는 빈 시퀀스의 끝 바로 다음 첫 번째 요소를 지정 하는 임의 액세스 반복기를 반환 합니다. 지정 하는 반복기를 사용 하면는 `current` 제어 된 시퀀스의 길이가 변경 하는 경우의 상태 제어 된 시퀀스의 시작 부분을 변경할 수 있습니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_begin.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
  
// alter first two items and reinspect   
    *--it = L'x';   
    *++it = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*begin() = a  
*++begin() = b  
 x y c  
```  

## <a name="capacity"></a> vector:: capacity (STL/CLR)
컨테이너에 할당 된 저장소의 크기를 보고합니다.  
  
### <a name="syntax"></a>구문  
  
```  
size_type capacity();  
```  
  
### <a name="remarks"></a>설명  
 멤버 함수는 제어 된 시퀀스도 큰 값을 보유할 현재 할당 된 저장소 반환 [vector:: size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`()`합니다. 제어 되는 시퀀스에 대 한 저장소를 다시 할당 해야 하기 전에 얼마나 많은 컨테이너 증가할 수를 확인 하려면 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_capacity.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// increase capacity   
    cliext::vector<wchar_t>::size_type cap = c1.capacity();   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        cap, c1.size() <= cap);   
    c1.reserve(cap + 5);   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        c1.capacity(), cap + 5 <= c1.capacity());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
capacity() = 4, ok = True  
capacity() = 9, ok = True  
```  

## <a name="clear"></a> vector:: clear (STL/CLR)
모든 요소를 제거합니다.  
  
### <a name="syntax"></a>구문  
  
```  
void clear();  
```  
  
### <a name="remarks"></a>설명  
 멤버 함수 시그니처 [vector:: erase (STL/CLR)](../dotnet/vector-erase-stl-clr.md) `(` [vector:: begin (STL/CLR)](../dotnet/vector-begin-stl-clr.md) `(),` [vector:: end (STL/CLR)](../dotnet/vector-end-stl-clr.md) `())`. 제어 되는 시퀀스 비어 있는지 확인 하려면 사용 합니다.  
  
### <a name="example"></a>예  
  
```  
// cliext_vector_clear.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 0  
 a b  
size() = 0  
```  

## <a name="const_iterator"></a> vector:: const_iterator (STL/CLR)
제어되는 시퀀스에 대한 상수 반복기의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef T2 const_iterator;  
```  
  
### <a name="remarks"></a>설명  
 이 형식은 지정 되지 않은 형식의 개체를 설명 `T2` 제어 되는 시퀀스에 대 한 상수 임의 액세스 반복기로 사용할 수 있는 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_const_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::vector<wchar_t>::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="const_reference"></a> vector:: const_reference (STL/CLR)
요소에 대한 상수 참조의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>설명  
 이 형식은 요소에 대 한 상수 참조를 설명 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_const_reference.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    cliext::vector<wchar_t>::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        cliext::vector<wchar_t>::const_reference cref = *cit;   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="const_reverse_iterator"></a> vector:: const_reverse_iterator (STL/CLR)
제어 되는 시퀀스에 대 한 상수 역방향 반복기의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef T4 const_reverse_iterator;  
```  
  
### <a name="remarks"></a>설명  
 이 형식은 지정 되지 않은 형식의 개체를 설명 `T4` 제어 되는 시퀀스에 대 한 상수 역방향 반복기로 사용할 수 있는 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::vector<wchar_t>::const_reverse_iterator crit = c1.rbegin();   
    cliext::vector<wchar_t>::const_reverse_iterator crend = c1.rend();   
    for (; crit != crend; ++crit)   
        System::Console::Write(" {0}", *crit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  

## <a name="difference_type"></a> vector:: difference_type (STL/CLR)
두 요소 사이의 부호가 있는 거리의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>설명  
 형식은 부호 있는 요소 수를 설명 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_difference_type.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    cliext::vector<wchar_t>::difference_type diff = 0;   
    for (cliext::vector<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it) ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (cliext::vector<wchar_t>::iterator it = c1.end();   
        it != c1.begin(); --it) --diff;   
    System::Console::WriteLine("begin()-end() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
begin()-end() = -3  
```  

## <a name="empty"></a> vector:: empty (STL/CLR)
요소가 있는지 여부를 테스트합니다.  
  
### <a name="syntax"></a>구문  
  
```  
bool empty();  
```  
  
### <a name="remarks"></a>설명  
 멤버 함수는 빈 제어되는 시퀀스에 대해 true를 반환합니다. 동일 [vector:: size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`() == 0`합니다. 벡터가 비어 있는지 여부를 테스트 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_empty.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 3  
empty() = False  
size() = 0  
empty() = True  
```  

## <a name="end"></a> vector:: end (STL/CLR)
제어되는 시퀀스의 끝을 지정합니다.  
  
### <a name="syntax"></a>구문  
  
```  
iterator end();  
```  
  
### <a name="remarks"></a>설명  
 멤버 함수는 제어 된 시퀀스의 끝 바로 다음을 가리키는 임의 액세스 반복기를 반환합니다. 지정 하는 반복기를 사용 하면는 `current` 제어 된 시퀀스의 길이가 변경 하는 경우의 상태 제어 된 시퀀스의 끝을 변경할 수 있습니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_end.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last two items   
    cliext::vector<wchar_t>::iterator it = c1.end();   
    --it;   
    System::Console::WriteLine("*-- --end() = {0}", *--it);   
    System::Console::WriteLine("*--end() = {0}", *++it);   
  
// alter first two items and reinspect   
    *--it = L'x';   
    *++it = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --end() = b  
*--end() = c  
 a x y  
```  

## <a name="erase"></a> vector:: erase (STL/CLR)
지정된 위치에 있는 요소를 제거합니다.  
  
### <a name="syntax"></a>구문  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>매개 변수  
 첫 번째  
 범위를 지우려면의 시작입니다.  
  
 last  
 범위를 지우려면의 끝입니다.  
  
 형식에 대한 설명  
 지울 요소입니다.  
  
### <a name="remarks"></a>설명  
 첫 번째 멤버 함수는 `where`로 지정된 제어 시퀀스의 요소를 제거합니다. 단일 요소를 제거 하려면 사용 합니다.  
  
 두 번째 멤버 함수는 [`first`, `last`]의 범위에서 제어되는 시퀀스의 요소를 제거합니다. 0 개 이상의 연속 요소를 제거 하려면 사용 합니다.  
  
 제거 된 요소 뒤에 남은 첫 번째 요소를 지정 하는 반복기를 반환 하는 두 멤버 함수 또는 [vector:: end (STL/CLR)](../dotnet/vector-end-stl-clr.md) `()` 이러한 요소가 없을 경우.  
  
 요소를 지운 경우에 요소 복사본의 수는 시퀀스의 할수록 끝과 여 지우기의 끝 간 요소 수에 비례 합니다. (시퀀스의 끝에 하나 이상의 요소를 지우는 중 요소 복사본이 발생 합니다.)  
  
### <a name="example"></a>예  
  
```cpp 
// cliext_vector_erase.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.push_back(L'd');   
    c1.push_back(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    cliext::vector<wchar_t>::iterator it = c1.end();   
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",   
        *c1.erase(c1.begin(), --it));   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
erase(begin()) = b  
 b c d e  
erase(begin(), end()-1) = e  
size() = 1  
```  

## <a name="front"></a> vector:: front (STL/CLR)
첫 번째 요소에 액세스합니다.  
  
### <a name="syntax"></a>구문  
  
```  
reference front();  
```  
  
### <a name="remarks"></a>설명  
 멤버 함수는 비어 있어야 하는 제어 된 시퀀스의 첫 번째 요소에 대 한 참조를 반환 합니다. 읽기 또는 존재 하는 것을 알고 있는 경우 첫 번째 요소를 쓰기를 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_front.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first item   
    System::Console::WriteLine("front() = {0}", c1.front());   
  
// alter first item and reinspect   
    c1.front() = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
front() = a  
 x b c  
```  

# <a name="front_item"></a> vector:: front_item (STL/CLR)
첫 번째 요소에 액세스합니다.  
  
### <a name="syntax"></a>구문  
  
```  
property value_type front_item;  
```  
  
### <a name="remarks"></a>설명  
 비어 있는 제어 된 시퀀스의 첫 번째 요소를 액세스 하는 속성입니다. 읽기 또는 존재 하는 것을 알고 있는 경우 첫 번째 요소를 쓰기를 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_front_item.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first item   
    System::Console::WriteLine("front_item = {0}", c1.front_item);   
  
// alter first item and reinspect   
    c1.front_item = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
front_item = a  
 x b c  
```  

# <a name="generic_container"></a> vector:: generic_container (STL/CLR)
컨테이너에 대 한 제네릭 인터페이스의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef Microsoft::VisualC::StlClr::  
    IVector<generic_value>  
    generic_container;  
```  
  
### <a name="remarks"></a>설명  
 이 형식은이 서식 파일 컨테이너 클래스에 대 한 제네릭 인터페이스를 설명 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_generic_container.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->insert(gc1->end(), L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.push_back(L'e');   
  
    System::Collections::IEnumerator^ enum1 =   
        gc1->GetEnumerator();   
    while (enum1->MoveNext())   
        System::Console::Write(" {0}", enum1->Current);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a b c d  
a b c d e  
```  

## <a name="generic_iterator"></a> vector:: generic_iterator (STL/CLR)
컨테이너에 대 한 제네릭 인터페이스와 함께 사용 하기 위해 반복기의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ContainerRandomAccessIterator<generic_value>  
    generic_iterator;  
```  
  
### <a name="remarks"></a>설명  
 형식은이 서식 파일 컨테이너 클래스에 대 한 제네릭 인터페이스와 함께 사용할 수 있는 일반 반복기를 설명 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::vector<wchar_t>::generic_iterator gcit = gc1->begin();   
    cliext::vector<wchar_t>::generic_value gcval = *gcit;   
    *++gcit = gcval;   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a a c  
```  

# <a name="generic_reverse_iterator"></a> vector:: generic_reverse_iterator (STL/CLR)
컨테이너에 대 한 제네릭 인터페이스와 함께 사용 하기 위해 한 반대 반복기의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ReverseRandomAccessIterator<generic_value> generic_reverse_iterator;  
```  
  
### <a name="remarks"></a>설명  
 형식은이 서식 파일 컨테이너 클래스에 대 한 제네릭 인터페이스와 함께 사용할 수 있는 제네릭 역방향 반복기를 설명 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::vector<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();   
    cliext::vector<wchar_t>::generic_value gcval = *gcit;   
    *++gcit = gcval;   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a c c  
```  

## <a name="generic_value"></a> vector:: generic_value (STL/CLR)
컨테이너에 대 한 제네릭 인터페이스와 함께 사용 하기 위해 요소의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>설명  
 이 형식은 형식의 개체를 설명 `GValue` 이 서식 파일 컨테이너 클래스에 대 한 제네릭 인터페이스와 함께 사용 하기 위해 저장 된 요소 값을 설명 하는 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_generic_value.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::vector<wchar_t>::generic_iterator gcit = gc1->begin();   
    cliext::vector<wchar_t>::generic_value gcval = *gcit;   
    *++gcit = gcval;   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a a c  
```  

## <a name="insert"></a> vector:: insert (STL/CLR)
지정된 된 위치에 요소를 추가합니다.  
  
### <a name="syntax"></a>구문  
  
```  
iterator insert(iterator where, value_type val);  
void insert(iterator where, size_type count, value_type val);  
template<typename InIt>  
    void insert(iterator where, InIt first, InIt last);  
void insert(iterator where,  
    System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>매개 변수  
 count  
 삽입할 요소의 수입니다.  
  
 첫 번째  
 삽입할 범위의의 시작입니다.  
  
 last  
 삽입할 범위의 끝입니다.  
  
 오른쪽  
 삽입 하는 열거형입니다.  
  
 Val  
 삽입할 요소의 값입니다.  
  
 형식에 대한 설명  
 앞에 삽입 하는 컨테이너의 위치입니다.  
  
### <a name="remarks"></a>설명  
 가 가리키는 요소 앞의 삽입, 함수는 멤버의 각 `where` 제어 된 시퀀스의 시퀀스는 나머지 피연산자에서 지정 합니다.  
  
 첫 번째 멤버 함수는 값을 가진 요소를 삽입 `val` 새로 삽입된 된 요소를 지정 하는 반복기를 반환 합니다. 반복기에서 지정 하는 장소 하기 전에 단일 요소를 삽입 하려면 사용 합니다.  
  
 두 번째 멤버 함수는 `val` 값의 `count` 요소 반복을 삽입합니다. 같은 값의 모든 복사본 인 0 개 이상의 연속 요소를 삽입 하려면 사용 합니다.  
  
 `InIt`가 정수 형식이면 세 번째 멤버 함수는 `insert(where, (size_type)first, (value_type)last)`와 동일하게 동작합니다. 시퀀스를 삽입, 그렇지 않으면 [`first`, `last`). 다른 시퀀스에서 복사 된 0 개 이상의 연속 요소를 삽입 하려면 사용 합니다.  
  
 로 지정 된 시퀀스를 삽입 하는 네 번째 멤버 함수는 `right`합니다. 열거자에서 설명 하는 시퀀스를 삽입 하려면 사용 합니다.  
  
 단일 요소를 삽입할 경우에 요소 복사본의 수는 삽입 지점와 떨어진 끝 시퀀스의 요소 수에 비례 합니다. (시퀀스의 끝에 하나 이상의 요소를 삽입할 경우 요소 복사본이 발생 합니다.) 경우 `InIt` 입력 반복기, 세 번째 멤버 함수는 시퀀스의 각 요소에 대 한 단일 삽입을 효과적으로 수행 합니다. 삽입할 때 그렇지 `N` 요소, 요소 복사본 수에 비례는 `N` 삽입 포인터와 떨어진 시퀀스의 끝 간 요소 수를 더한 값입니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_insert.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using iterator   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",   
        *c1.insert(++it, L'x'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a repetition of values   
    cliext::vector<wchar_t> c2;   
    c2.insert(c2.begin(), 2, L'y');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    it = c1.end();   
    c2.insert(c2.end(), c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    c2.insert(c2.begin(),   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
insert(begin()+1, L'x') = x  
 a x b c  
 y y  
 y y a x b  
 a x b c y y a x b  
```  
  
## <a name="iterator"></a> vector:: iterator (STL/CLR)
제어되는 시퀀스에 대한 반복기의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>설명  
 이 형식은 지정 되지 않은 형식의 개체를 설명 `T1` 제어 되는 시퀀스에 대 한 임의 액세스 반복기로 사용할 수 있는 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
  
// alter first element and redisplay   
    it = c1.begin();   
    *it = L'x';   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
x b c  
```  

## <a name="op_as"></a> vector:: operator = (STL/CLR)
제어되는 시퀀스를 바꿉니다.  
  
### <a name="syntax"></a>구문  
  
```  
vector<Value>% operator=(vector<Value>% right);  
```  
  
#### <a name="parameters"></a>매개 변수  
 오른쪽  
 복사할 컨테이너입니다.  
  
### <a name="remarks"></a>설명  
 멤버 연산자 복사본 `right` 개체에 반환 `*this`합니다. 이를 사용하여 제어되는 시퀀스를 `right`의 제어되는 시퀀스 복사본으로 대체합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_operator_as.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2 = c1;   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
```  

## <a name="op"></a> vector::operator(STL/CLR)
지정된 위치에 있는 요소에 액세스합니다.  
  
### <a name="syntax"></a>구문  
  
```  
reference operator[](size_type pos);  
```  
  
#### <a name="parameters"></a>매개 변수  
 위치  
 액세스할 요소의 위치입니다.  
  
### <a name="remarks"></a>설명  
 멤버 연산자는 referene 위치에 요소를 반환 `pos`합니다. 요소를 알면 해당 위치에 액세스 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp 
// cliext_vector_operator_sub.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using subscripting   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
  
// change an entry and redisplay   
    c1[1] = L'x';   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a x c  
```  

## <a name="pop_back"></a> vector:: pop_back (STL/CLR)
마지막 요소를 제거 합니다.  
  
### <a name="syntax"></a>구문  
  
```  
void pop_back();  
```  
  
### <a name="remarks"></a>설명  
 멤버 함수는 비어 있어야 하는 제어 된 시퀀스의 마지막 요소를 제거 합니다. 뒤에 한 요소 하 여 벡터를 축소를 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_pop_back.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop_back();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b  
```  

## <a name="push_back"></a> vector:: push_back (STL/CLR)
새 마지막 요소를 추가 합니다.  
  
### <a name="syntax"></a>구문  
  
```  
void push_back(value_type val);  
```  
  
### <a name="remarks"></a>설명  
 멤버 함수는 값을 가진 요소를 삽입 `val` 제어 된 시퀀스의 끝입니다. 벡터에 다른 요소를 추가 하려면 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_push_back.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="rbegin"></a> vector:: rbegin (STL/CLR)
제어되는 역방향 시퀀스의 시작을 지정합니다.  
  
### <a name="syntax"></a>구문  
  
```  
reverse_iterator rbegin();  
```  
  
### <a name="remarks"></a>설명  
 멤버 함수는 빈 시퀀스의 시작 부분 바로 다음 또는 제어 된 시퀀스의 마지막 요소를 지정 하는 역방향 반복기를 반환 합니다. 따라서을 지정 된 `beginning` 역방향 시퀀스의 합니다. 지정 하는 반복기를 사용 하면는 `current` 제어 된 시퀀스를 역순으로 표시 하지만 해당 상태의 시작 부분 제어 된 시퀀스의 길이가 변경 되 면 변경할 수 있습니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_rbegin.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = {0}", *rit);   
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);   
  
// alter first two items and reinspect   
    *--rit = L'x';   
    *++rit = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*rbegin() = c  
*++rbegin() = b  
 a y x  
```  

## <a name="reference"></a> vector:: reference (STL/CLR)
요소에 대한 참조의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>설명  
 이 형식은 요소에 대 한 참조를 설명 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_reference.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        cliext::vector<wchar_t>::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
  
// modify contents " a b c"   
    for (it = c1.begin(); it != c1.end(); ++it)   
        {   // get a reference to an element   
        cliext::vector<wchar_t>::reference ref = *it;   
  
        ref += (wchar_t)(L'A' - L'a');   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
A B C  
```  

## <a name="rend"></a> vector:: rend (STL/CLR)
제어되는 역방향 시퀀스의 끝을 지정합니다.  
  
### <a name="syntax"></a>구문  
  
```  
reverse_iterator rend();  
```  
  
### <a name="remarks"></a>설명  
 멤버 함수는 제어 된 시퀀스의 시작 부분 바로 다음 가리키는 역방향 반복기를 반환합니다. 따라서을 지정 된 `end` 역방향 시퀀스의 합니다. 지정 하는 반복기를 사용 하면는 `current` 제어 된 시퀀스를 역순으로 표시 하지만 해당 상태의 끝 제어 된 시퀀스의 길이가 변경 되 면 변경할 수 있습니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_rend.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rend();   
    --rit;   
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);   
    System::Console::WriteLine("*--rend() = {0}", *++rit);   
  
// alter first two items and reinspect   
    *--rit = L'x';   
    *++rit = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --rend() = b  
*--rend() = a  
 y x c  
```  

## <a name="reserve"></a> vector:: reserve (STL/CLR)
컨테이너에 대 한 최소 증가 용량을 보장합니다.  
  
### <a name="syntax"></a>구문  
  
```  
void reserve(size_type count);  
```  
  
#### <a name="parameters"></a>매개 변수  
 count  
 새 컨테이너의 최소 용량입니다.  
  
### <a name="remarks"></a>설명  
 멤버 함수를 사용 하면 `capacity()` 예측이 이상 반환 `count`합니다. 컨테이너 지정된 된 크기 성장 했으며 될 때까지 제어 되는 시퀀스에 대 한 저장소 할당 되지 필요 하도록 사용할 수 있습니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_reserve.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// increase capacity   
    cliext::vector<wchar_t>::size_type cap = c1.capacity();   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        cap, c1.size() <= cap);   
    c1.reserve(cap + 5);   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        c1.capacity(), cap + 5 <= c1.capacity());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
capacity() = 4, ok = True  
capacity() = 9, ok = True  
```  

## <a name="resize"></a> vector:: resize (STL/CLR)
요소의 수를 변경합니다.  
  
### <a name="syntax"></a>구문  
  
```  
void resize(size_type new_size);  
void resize(size_type new_size, value_type val);  
```  
  
#### <a name="parameters"></a>매개 변수  
 new_size  
 제어 된 시퀀스의 새 크기입니다.  
  
 Val  
 안쪽 여백 요소의 값입니다.  
  
### <a name="remarks"></a>설명  
 두 멤버 함수를 확인 하는 [vector:: size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `()` 예측이 반환 `new_size`합니다. 제어되는 시퀀스 길이를 늘려야 할 경우 첫 번째 멤버 함수는 값이 `value_type()`인 요소를 추가하지만, 두 번째 멤버 함수는 값이 `val`인 요소를 추가합니다. 더 짧은 제어 되는 시퀀스를 두 멤버 함수는 효과적으로 지울 마지막 요소 [vector:: size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `() -` `new_size` 시간입니다. 제어 되는 시퀀스의 크기가을 사용 하면 `new_size`, 트리밍 하거나 현재 제어 되는 시퀀스를 패딩 하 여 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_resize.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::vector<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
    c1.resize(4);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// resize to empty   
    c1.resize(0);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// resize and pad   
    c1.resize(5, L'x');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 0 0 0 0  
size() = 0  
 x x x x x  
```  

## <a name="reverse_iterator"></a> vector:: reverse_iterator (STL/CLR)
제어되는 시퀀스에 대한 반대 반복기의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef T3 reverse_iterator;  
```  
  
### <a name="remarks"></a>설명  
 이 형식은 제어된 시퀀스에 대해 반대 반복기로 사용될 수 있는 지정되지 않은 `T3` 형식의 개체를 설명합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
  
// alter first element and redisplay   
    rit = c1.rbegin();   
    *rit = L'x';   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
x b a  
```  

## <a name="size"></a> vector:: size (STL/CLR)
요소 수를 계산합니다.  
  
### <a name="syntax"></a>구문  
  
```  
size_type size();  
```  
  
### <a name="remarks"></a>설명  
 멤버 함수는 제어되는 시퀀스의 길이를 반환합니다. 제어 되는 시퀀스의 현재 요소 수를 확인 하려면 사용 합니다. 모든 경우에 중요 한 여부 시퀀스 크기가 0이 아닌 참조 [vector:: empty (STL/CLR)](../dotnet/vector-empty-stl-clr.md)`()`합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_size.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 3 starting with 3  
size() = 0 after clearing  
size() = 2 after adding 2  
```  

## <a name="size_type"></a> vector:: size_type (STL/CLR)
두 요소 사이의 부호가 있는 거리의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef int size_type;  
```  
  
### <a name="remarks"></a>설명  
 형식은은 음수가 아닌 요소 수를 설명 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_size_type.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    cliext::vector<wchar_t>::size_type diff = c1.end() - c1.begin();   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```  
  
## <a name="swap"></a> vector:: swap (STL/CLR)
두 컨테이너의 내용을 바꿉니다.  
  
### <a name="syntax"></a>구문  
  
```  
void swap(vector<Value>% right);  
```  
  
#### <a name="parameters"></a>매개 변수  
 오른쪽  
 콘텐츠와 바꿀 컨테이너입니다.  
  
### <a name="remarks"></a>설명  
 멤버 함수는 `*this` 와 `right`간에 제어되는 시퀀스를 교환합니다. 일정 한 시간에 작업을 수행 하 고 예외가 throw 됩니다. 두 컨테이너의 내용을 교환에 신속 하 게 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_swap.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    cliext::vector<wchar_t> c2(5, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
x x x x x  
x x x x x  
a b c  
```  

## <a name="to_array"></a> vector:: to_array (STL/CLR)
제어 되는 새 배열에 복사합니다.  
  
### <a name="syntax"></a>구문  
  
```  
cli::array<Value>^ to_array();  
```  
  
### <a name="remarks"></a>설명  
 멤버 함수는 제어 되는 시퀀스를 포함 하는 배열을 반환 합니다. 배열 형식으로 제어 되는 시퀀스의 복사본을 사용 하면 됩니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_to_array.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// copy the container and modify it   
    cli::array<wchar_t>^ a1 = c1.to_array();   
  
    c1.push_back(L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display the earlier array copy   
    for each (wchar_t elem in a1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c d  
a b c  
```  

## <a name="value_type"></a> vector:: value_type (STL/CLR)
요소의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef Value value_type;  
```  
  
### <a name="remarks"></a>설명  
 이 형식은 템플릿 매개 변수 `Value`의 동의어입니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_value_type.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using value_type   
    for (cliext::vector<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   // store element in value_type object   
        cliext::vector<wchar_t>::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="vector"></a> vector:: vector (STL/CLR)
컨테이너 개체를 만듭니다.  
  
### <a name="syntax"></a>구문  
  
```  
vector();  
vector(vector<Value>% right);  
vector(vector<Value>^ right);  
explicit vector(size_type count);  
vector(size_type count, value_type val);  
template<typename InIt>  
    vector(InIt first, InIt last);  
vector(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>매개 변수  
 count  
 삽입할 요소의 수입니다.  
  
 첫 번째  
 삽입할 범위의의 시작입니다.  
  
 last  
 삽입할 범위의 끝입니다.  
  
 오른쪽  
 삽입할 개체 또는 범위입니다.  
  
 Val  
 삽입할 요소의 값입니다.  
  
### <a name="remarks"></a>설명  
 생성자:  
  
 `vector();`  
  
 요소가 없는 제어 되는 시퀀스를 초기화합니다. 초기는 빈 제어 시퀀스를 지정 하려면 사용 합니다.  
  
 생성자:  
  
 `vector(vector<Value>% right);`  
  
 순서와 제어 된 시퀀스를 초기화 합니다. [`right.begin()`, `right.end()`). 벡터 개체에 의해 제어 되는 시퀀스의 복사본 인는 초기 제어 시퀀스를 지정 하려면 사용할 `right`합니다.  
  
 생성자:  
  
 `vector(vector<Value>^ right);`  
  
 순서와 제어 된 시퀀스를 초기화 합니다. [`right->begin()`, `right->end()`). 핸들은 벡터 개체에 의해 제어 되는 시퀀스의 복사본 인는 초기 제어 시퀀스를 지정 하려면 사용할 `right`합니다.  
  
 생성자:  
  
 `explicit vector(size_type count);`  
  
 이 있는 제어 된 시퀀스를 초기화 `count` 각 요소 값을 가진 `value_type()`합니다. 있습니다을 채우는 데 사용할 컨테이너 요소와 모든 기본 값이 포함 됩니다.  
  
 생성자:  
  
 `vector(size_type count, value_type val);`  
  
 이 있는 제어 된 시퀀스를 초기화 `count` 각 요소 값을 가진 `val`합니다. 하면을 채우는 데 사용할 컨테이너 요소와 동일한 값이 모두 포함 합니다.  
  
 생성자:  
  
 `template<typename InIt>`  
  
 `vector(InIt first, InIt last);`  
  
 순서와 제어 된 시퀀스를 초기화 합니다. [`first`, `last`). 제어 되는 시퀀스의 사본을 다른 시퀀스를 사용 합니다.  
  
 생성자:  
  
 `vector(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 열거자에 지정 된 시퀀스와 제어 된 시퀀스를 초기화 `right`합니다. 제어 되는 시퀀스의 사본을 열거자에서 설명 하는 다른 시퀀스를 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_construct.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
// construct an empty container   
    cliext::vector<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::vector<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::vector<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::vector<wchar_t>::iterator it = c3.end();   
    cliext::vector<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::vector<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::vector<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::vector<wchar_t> c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 0 0 0  
 x x x x x x  
 x x x x x  
 x x x x x x  
 x x x x x x  
 x x x x x x  
```  

## <a name="op_neq"></a> operator! = (vector) (STL/CLR)
같지 않음 비교를 벡터입니다.  
  
### <a name="syntax"></a>구문  
  
```cpp  
template<typename Value>  
    bool operator!=(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>매개 변수  
 왼쪽  
 비교할 왼쪽 컨테이너입니다.  
  
 오른쪽  
 비교할 오른쪽 컨테이너입니다.  
  
### <a name="remarks"></a>설명  
 연산자 함수 반환 `!(left == right)`합니다. 테스트를 사용 하는지 여부를 `left` 동일 정렬 되지 않은 `right` 두 벡터 요소에서 비교 된 요소를가 하는 경우.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_operator_ne.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] != [a b c] is {0}",   
        c1 != c1);   
    System::Console::WriteLine("[a b c] != [a b d] is {0}",   
        c1 != c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] != [a b c] is False  
[a b c] != [a b d] is True  
```  

## <a name="op_lt"></a> 연산자&lt; (vector) (STL/CLR)
벡터 비교 미만입니다.  
  
### <a name="syntax"></a>구문  
  
```  
template<typename Value>  
    bool operator<(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>매개 변수  
 왼쪽  
 비교할 왼쪽 컨테이너입니다.  
  
 오른쪽  
 비교할 오른쪽 컨테이너입니다.  
  
### <a name="remarks"></a>설명  
 연산자 함수 이면 true를 반환, 가장 낮은 위치에 대 한 `i` 를 `!(right[i] < left[i])` 도 true 하는 것이 `left[i] < right[i]`합니다. 그렇지 않으면 반환 `left->size() < right->size()` 테스트를 사용 하는지 여부를 `left` 앞에 정렬 `right` 두 벡터 요소에서 비교 된 요소를가 하는 경우.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_operator_lt.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] < [a b c] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[a b c] < [a b d] is {0}",   
        c1 < c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] < [a b c] is False  
[a b c] < [a b d] is True  
```  

## <a name="op_lteq"></a> 연산자&lt;= (vector) (STL/CLR)
벡터 보다 작거나 같은지 비교 합니다.  
  
### <a name="syntax"></a>구문  
  
```  
template<typename Value>  
    bool operator<=(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>매개 변수  
 왼쪽  
 비교할 왼쪽 컨테이너입니다.  
  
 오른쪽  
 비교할 오른쪽 컨테이너입니다.  
  
### <a name="remarks"></a>설명  
 연산자 함수 반환 `!(right < left)`합니다. 테스트를 사용 하는지 여부를 `left` 후 정렬 되지 않은 `right` 두 벡터 요소에서 비교 된 요소를가 하는 경우.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_operator_le.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] <= [a b c] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] <= [a b c] is True  
[a b d] <= [a b c] is False  
```  

## <a name="op_eq"></a> 연산자 = = (vector) (STL/CLR)
벡터 같은지 비교 합니다.  
  
### <a name="syntax"></a>구문  
  
```  
template<typename Value>  
    bool operator==(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>매개 변수  
 왼쪽  
 비교할 왼쪽 컨테이너입니다.  
  
 오른쪽  
 비교할 오른쪽 컨테이너입니다.  
  
### <a name="remarks"></a>설명  
 연산자 함수는 시퀀스에 의해 제어 하는 경우에 true를 반환 `left` 및 `right` 동일한 길이 및 각 위치에 대 한 `i`, `left[i] ==` `right[i]`합니다. 테스트를 사용 하는지 여부를 `left` 와 동일 하 게 정렬 되 `right` 두 벡터 요소에서 비교 된 요소를가 하는 경우.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_operator_eq.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] == [a b c] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[a b c] == [a b d] is {0}",   
        c1 == c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] == [a b c] is True  
[a b c] == [a b d] is False  
```  

## <a name="op_gt"></a> 연산자&gt; (vector) (STL/CLR)
비교에 보다 큰 사용 되는 벡터입니다.  
  
### <a name="syntax"></a>구문  
  
```  
template<typename Value>  
    bool operator>(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>매개 변수  
 왼쪽  
 비교할 왼쪽 컨테이너입니다.  
  
 오른쪽  
 비교할 오른쪽 컨테이너입니다.  
  
### <a name="remarks"></a>설명  
 연산자 함수 반환 `right` `<` `left`합니다. 테스트를 사용 하는지 여부를 `left` 후 정렬 `right` 두 벡터 요소에서 비교 된 요소를가 하는 경우.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_operator_gt.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] > [a b c] is {0}",   
        c1 > c1);   
    System::Console::WriteLine("[a b d] > [a b c] is {0}",   
        c2 > c1);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] > [a b c] is False  
[a b d] > [a b c] is True  
```  

## <a name="op_gteq"></a> 연산자&gt;= (vector) (STL/CLR)
벡터 보다 큰 또는 같은지 비교 합니다.  
  
### <a name="syntax"></a>구문  
  
```  
template<typename Value>  
    bool operator>=(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>매개 변수  
 왼쪽  
 비교할 왼쪽 컨테이너입니다.  
  
 오른쪽  
 비교할 오른쪽 컨테이너입니다.  
  
### <a name="remarks"></a>설명  
 연산자 함수 반환 `!(left < right)`합니다. 테스트를 사용 하는지 여부를 `left` 하기 전에 정렬 되지 않은 `right` 두 벡터 요소에서 비교 된 요소를가 하는 경우.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_vector_operator_ge.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] >= [a b c] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] >= [a b c] is True  
[a b c] >= [a b d] is False  
```  
