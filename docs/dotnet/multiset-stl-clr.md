---
title: multiset (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multiset
- cliext::multiset::begin
- cliext::multiset::clear
- cliext::multiset::const_iterator
- cliext::multiset::const_reference
- cliext::multiset::const_reverse_iterator
- cliext::multiset::count
- cliext::multiset::difference_type
- cliext::multiset::empty
- cliext::multiset::end
- cliext::multiset::equal_range
- cliext::multiset::erase
- cliext::multiset::find
- cliext::multiset::generic_container
- cliext::multiset::generic_iterator
- cliext::multiset::generic_reverse_iterator
- cliext::multiset::generic_value
- cliext::multiset::insert
- cliext::multiset::iterator
- cliext::multiset::key_comp
- cliext::multiset::key_compare
- cliext::multiset::key_type
- cliext::multiset::lower_bound
- cliext::multiset::make_value
- cliext::multiset::multiset
- cliext::multiset::operator=
- cliext::multiset::rbegin
- cliext::multiset::reference
- cliext::multiset::rend
- cliext::multiset::reverse_iterator
- cliext::multiset::size
- cliext::multiset::size_type
- cliext::multiset::swap
- cliext::multiset::to_array
- cliext::multiset::upper_bound
- cliext::multiset::value_comp
- cliext::multiset::value_compare
- cliext::multiset::value_type
- cliext::multiset::operator!=
- cliext::multiset::operator<
- cliext::multiset::operator<=
- cliext::multiset::operator==
- cliext::multiset::operator>
- cliext::multiset::operator>=
dev_langs:
- C++
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- multiset class [STL/CLR]
- begin member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- count member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- equal_range member [STL/CLR]
- erase member [STL/CLR]
- find member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- map member [STL/CLR]
- mapped_type member [STL/CLR]
- operator= member [STL/CLR]
- operator member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- upper_bound member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
ms.assetid: 7c46e2b4-cd88-49b7-a9e6-63ad5ae7feb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d4a4255e5c6229ee570b9baa8952cc784044ef95
ms.sourcegitcommit: 301bb19056e5bae84ff50f7d1df1e546efe225ba
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36305815"
---
# <a name="multiset-stlclr"></a>multiset(STL/CLR)
이 템플릿 클래스는 다양 한 길이의 요소 시퀀스를 양방향 액세스할 수 있는 제어 하는 개체를 설명 합니다. 컨테이너를 사용 하 여 `multiset` 하나의 요소 저장 하 고 각 노드의 정렬 된 나무를 균형 있게 (거의)으로 요소의 시퀀스를 관리할 수 있습니다.  
  
 아래 설명에 `GValue` 동일 `GKey`는 다시 됩니다 동일 `Key` 후자 형식인 ref 하지 않는 한 경우에서 이기 `Key^`합니다.  
  
## <a name="syntax"></a>구문  
  
```  
template<typename Key>  
    ref class multiset  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>매개 변수  
 Key  
 형식 제어 된 시퀀스의 요소의 핵심 구성 요소입니다.  

## <a name="requirements"></a>요구 사항  
 **헤더:** \<cliext/set >  
  
 **Namespace:** cliext  

## <a name="declarations"></a>선언  
  
|형식 정의|설명|  
|---------------------|-----------------|  
|[multiset::const_iterator(STL/CLR)](#const_iterator)|제어되는 시퀀스에 대한 상수 반복기의 형식입니다.|  
|[multiset::const_reference(STL/CLR)](#const_reference)|요소에 대한 상수 참조의 형식입니다.|  
|[multiset::const_reverse_iterator(STL/CLR)](#const_reverse_iterator)|제어되는 시퀀스에 대한 상수 역방향 반복기의 형식입니다.|  
|[multiset::difference_type(STL/CLR)](#difference_type)|두 요소 사이의 거리 (서명 된 가능)의 형식입니다.|  
|[multiset::generic_container(STL/CLR)](#generic_container)|컨테이너에 대 한 제네릭 인터페이스의 형식입니다.|  
|[multiset::generic_iterator(STL/CLR)](#generic_iterator)|컨테이너에 대 한 제네릭 인터페이스에 대 한 반복기의 형식입니다.|  
|[multiset::generic_reverse_iterator(STL/CLR)](#generic_reverse_iterator)|컨테이너에 대 한 제네릭 인터페이스에 대 한 반대 반복기의 형식입니다.|  
|[multiset::generic_value(STL/CLR)](#generic_value)|컨테이너에 대 한 제네릭 인터페이스에 대 한 요소의 형식입니다.|  
|[multiset::iterator(STL/CLR)](#iterator)|제어되는 시퀀스에 대한 반복기의 형식입니다.|  
|[multiset::key_compare(STL/CLR)](#key_compare)|두 키에 대 한 순서 지정 하는 대리자입니다.|  
|[multiset::key_type(STL/CLR)](#key_type)|정렬 키의 형식입니다.|  
|[multiset::reference(STL/CLR)](#reference)|요소에 대한 참조의 형식입니다.|  
|[multiset::reverse_iterator(STL/CLR)](#reverse_iterator)|제어되는 시퀀스에 대한 반대 반복기의 형식입니다.|  
|[multiset::size_type(STL/CLR)](#size_type)|두 요소 사이의 (음수가) 거리의 형식입니다.|  
|[multiset::value_compare(STL/CLR)](#value_compare)|두 요소 값에 대 한 순서 지정 하는 대리자입니다.|  
|[multiset::value_type(STL/CLR)](#value_type)|요소의 형식입니다.|  
  
|멤버 함수|설명|  
|---------------------|-----------------|  
|[multiset::begin(STL/CLR)](#begin)|제어되는 시퀀스의 시작을 지정합니다.|  
|[multiset::clear(STL/CLR)](#clear)|모든 요소를 제거합니다.|  
|[multiset::count(STL/CLR)](#count)|지정된 된 키와 일치 하는 요소 수를 계산 합니다.|  
|[multiset::empty(STL/CLR)](#empty)|요소가 있는지 여부를 테스트합니다.|  
|[multiset::end(STL/CLR)](#end)|제어되는 시퀀스의 끝을 지정합니다.|  
|[multiset::equal_range(STL/CLR)](#equal_range)|지정된 키와 일치하는 범위를 찾습니다.|  
|[multiset::erase(STL/CLR)](#erase)|지정된 위치에 있는 요소를 제거합니다.|  
|[multiset::find(STL/CLR)](#find)|지정된 키와 일치하는 요소를 찾습니다.|  
|[multiset::insert(STL/CLR)](#insert)|요소를 추가합니다.|  
|[multiset::key_comp(STL/CLR)](#key_comp)|두 키에 대 한 순서 지정 대리자를 복사합니다.|  
|[multiset::lower_bound(STL/CLR)](#lower_bound)|지정된 된 키와 일치 하는 범위의 시작 부분을 찾습니다.|  
|[multiset::make_value(STL/CLR)](#make_value)|값 개체를 만듭니다.|  
|[multiset::multiset(STL/CLR)](#multiset)|컨테이너 개체를 만듭니다.|  
|[multiset::rbegin(STL/CLR)](#rbegin)|제어되는 역방향 시퀀스의 시작을 지정합니다.|  
|[multiset::rend(STL/CLR)](#rend)|제어되는 역방향 시퀀스의 끝을 지정합니다.|  
|[multiset::size(STL/CLR)](#size)|요소 수를 계산합니다.|  
|[multiset::swap(STL/CLR)](#swap)|두 컨테이너의 내용을 바꿉니다.|  
|[multiset::to_array(STL/CLR)](#to_array)|제어 되는 새 배열에 복사합니다.|  
|[multiset::upper_bound(STL/CLR)](#upper_bound)|지정된 된 키와 일치 하는 범위의 끝을 찾습니다.|  
|[multiset::value_comp(STL/CLR)](#value_comp)|두 요소 값에 대 한 순서 지정 대리자를 복사합니다.|  
  
|연산자|설명|  
|--------------|-----------------|  
|[multiset::operator=(STL/CLR)](#op_as)|제어되는 시퀀스를 바꿉니다.|  
|[operator!= (multiset)(STL/CLR)](#op_neq)|있는지 여부를 확인 한 `multiset` 개체가 다른과 같지 않습니다. `multiset` 개체입니다.|  
|[operator< (multiset)(STL/CLR)](#op_lt)|있는지 여부를 확인 한 `multiset` 개체를 사용 하면 다른 노드보다 작은지 `multiset` 개체입니다.|  
|[operator<= (multiset)(STL/CLR)](#op_lteq)|있는지 여부를 확인 한 `multiset` 개체 보다 작거나 같으면 다른 `multiset` 개체입니다.|  
|[operator== (multiset)(STL/CLR)](#op_eq)|있는지 여부를 확인 한 `multiset` 개체는 다른 `multiset` 개체입니다.|  
|[operator> (multiset)(STL/CLR)](#op_gt)|있는지 여부를 확인 한 `multiset` 개체가 다른 노드보다 큰지 `multiset` 개체입니다.|  
|[operator>= (multiset)(STL/CLR)](#op_gteq)|있는지 여부를 확인 한 `multiset` 개체는 다른 보다 크거나 `multiset` 개체입니다.|  
  
## <a name="interfaces"></a>인터페이스  
  
|인터페이스|설명|  
|---------------|-----------------|  
|<xref:System.ICloneable>|개체를 복제 합니다.|  
|<xref:System.Collections.IEnumerable>|요소를 통해 시퀀스입니다.|  
|<xref:System.Collections.ICollection>|요소의 그룹을 유지 합니다.|  
|<xref:System.Collections.Generic.IEnumerable%601>|형식화 된 요소 시퀀스입니다.|  
|<xref:System.Collections.Generic.ICollection%601>|형식화 된 요소의 그룹을 유지 합니다.|  
|ITree\<키, 값 >|제네릭 컨테이너를 유지 합니다.|  
  
## <a name="remarks"></a>설명  
 개체 할당 및 개별 노드로 제어 하는 시퀀스에 대 한 저장소를 해제 합니다. 다른 한 노드의 콘텐츠를 복사 하 여 되지 노드 간의 링크를 변경 하 여 순서가 지정 된 보관 하는 나무를 균형 있게 (거의)에 요소를 삽입 합니다. 즉, 삽입 하 고 나머지 요소를 방해 하지 않고 자유롭게 요소를 제거할 수 있습니다.  
  
 형식의 개체를 저장된 하는 대리자를 호출 하 여 제어 하는 시퀀스를 정렬 하는 개체 [multiset:: key_compare (STL/CLR)](../dotnet/multiset-key-compare-stl-clr.md)합니다. Multiset; 생성할 때 저장된 대리자 개체를 지정할 수 있습니다. 기본값은 비교 없는 대리자 개체를 지정 하면 `operator<(key_type, key_type)`합니다. 멤버 함수를 호출 하 여이 저장 된 개체를 액세스할 [multiset:: key_comp (STL/CLR)](../dotnet/multiset-key-comp-stl-clr.md)`()`합니다.  
  
 이러한 대리자 개체 유형의 키에 대해 엄밀히 약한 정렬을 적용 해야 합니다 [multiset:: key_type (STL/CLR)](../dotnet/multiset-key-type-stl-clr.md)합니다. 모든 두 개의 키 즉 `X` 및 `Y`:  
  
 `key_comp()(X, Y)` 동일한 부울 결과를 반환 모든 호출 합니다.  
  
 경우 `key_comp()(X, Y)` 가 true 이면 `key_comp()(Y, X)` false 이어야 합니다.  
  
 경우 `key_comp()(X, Y)` 가 true 이면 `X` 앞에 정렬를 라고 `Y`합니다.  
  
 경우 `!key_comp()(X, Y) && !key_comp()(Y, X)` 가 true 이면 `X` 및 `Y` 순서 지정이 동일할에 있다고 합니다.  
  
 모든 요소에 대해 `X` 앞에 `Y` 제어 된 시퀀스의 `key_comp()(Y, X)` 은 false입니다. (기본 대리자 개체에 대 한 키는 결코 감소 값입니다.) 템플릿 클래스와 달리 [(STL/CLR) 설정](../dotnet/set-stl-clr.md)를 템플릿 클래스의 개체 `multiset` 모든 요소에 대 한 키가 고유한 지 필요 하지 않습니다. (키가 두 개 이상 있을 수 있음 순서 지정이 동일할.)  
  
 각 요소는 의미와 값 모두로 사용 됩니다. 시퀀스는 시퀀스 (에 오면 로그 시간)에 조회, 삽입 및 수의 요소 수 로그에 비례 하는 작업의 임의 요소 제거를 허용 하는 방식으로 표시 됩니다. 또한, 요소를 삽입할 경우 어떤 반복기도 무효화되지 않으며, 요소를 제거할 경우 제거된 요소를 가리키고 있는 반복기만 무효화됩니다.  
  
 Multiset 제어 된 시퀀스의 요소를 지정 하는 반복기를 제공 하는 인접 요소를 실행할 수를 의미 있는 양방향 반복기를 지원 합니다. 반환 된 반복기에 해당 하는 특수 헤드 노드 [multiset:: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`합니다. 있는 경우이 반복기는 제어 되는 시퀀스에서 마지막 요소를 연결할를 감소 시킬 수 있습니다. 헤드 노드에 도달 하는 multiset 반복기를 증가 시킬 수 있습니다 및 같음 비교 다음 `end()`합니다. 반환 된 반복기를 역 참조할 수 없습니다 하지만 `end()`합니다.  
  
 참조할 수 없습니다. 직접 나와 임의 액세스 반복기를 필요로 하는 숫자 위치-multiset 요소는 참고 사항  
  
 Multiset 반복기 차례로 연결 된 컨테이너에 대 한 핸들을 저장 하는 해당 연결 된 multiset 노드로에 대 한 핸들을 저장 합니다. 반복기의 관련된 컨테이너 개체와만 사용할 수 있습니다. Multiset 반복기도 연결 된 multiset 노드 일부 multiset와 연결 된 유효한 상태를 유지 합니다. 유효한 반복기 dereferencable 연결은 액세스 또는 같지 않은 것으로 지정-요소 값을 변경 하려면 사용할 수 또한 `end()`합니다.  
  
 지우거 나 요소를 제거 합니다. 저장된 된 값에 대 한 소멸자를 호출 합니다. 컨테이너를 제거 합니다. 모든 요소를 지웁니다. 따라서 요소 형식이 ref 클래스는 컨테이너 보다 수명이 깁니다 컨테이너 요소가 있는지 확인 합니다. 단, 핸들의 컨테이너 하다 `not` 해당 요소를 제거 합니다.  
  
## <a name="members"></a>멤버

## <a name="begin"></a> multiset:: begin (STL/CLR)
제어되는 시퀀스의 시작을 지정합니다.  
  
### <a name="syntax"></a>구문  
  
```  
iterator begin();  
```  
  
### <a name="remarks"></a>설명  
 멤버 함수는 제어 되는 시퀀스 또는 빈 시퀀스의 끝 바로 다음의 첫 번째 요소를 지정 하는 양방향 반복기를 반환 합니다. 지정 하는 반복기를 사용 하면는 `current` 제어 된 시퀀스의 길이가 변경 하는 경우의 상태 제어 된 시퀀스의 시작 부분을 변경할 수 있습니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_begin.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Mymultiset::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*begin() = a  
*++begin() = b  
```  

## <a name="clear"></a> multiset:: clear (STL/CLR)
모든 요소를 제거합니다.  
  
### <a name="syntax"></a>구문  
  
```  
void clear();  
```  
  
### <a name="remarks"></a>설명  
 멤버 함수 시그니처 [multiset:: erase (STL/CLR)](../dotnet/multiset-erase-stl-clr.md) `(` [multiset:: begin (STL/CLR)](../dotnet/multiset-begin-stl-clr.md) `(),` [multiset:: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md) `())`. 제어 되는 시퀀스 비어 있는지 확인 하려면 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_clear.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
  
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

## <a name="const_iterator"></a> multiset:: const_iterator (STL/CLR)
제어되는 시퀀스에 대한 상수 반복기의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef T2 const_iterator;  
```  
  
### <a name="remarks"></a>설명  
 이 형식은 지정 되지 않은 형식의 개체를 설명 `T2` 제어 되는 시퀀스에 대 한 양방향 상수 반복기로 사용할 수 있는 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_const_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Mymultiset::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="const_reference"></a> multiset:: const_reference (STL/CLR)
요소에 대한 상수 참조의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>설명  
 이 형식은 요소에 대 한 상수 참조를 설명 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_const_reference.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    Mymultiset::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        Mymultiset::const_reference cref = *cit;   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
``` 

## <a name="const_reverse_iterator"></a> multiset:: const_reverse_iterator (STL/CLR)
제어 되는 시퀀스에 대 한 상수 역방향 반복기의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef T4 const_reverse_iterator;  
```  
  
### <a name="remarks"></a>설명  
 이 형식은 지정 되지 않은 형식의 개체를 설명 `T4` 제어 되는 시퀀스에 대 한 상수 역방향 반복기로 사용할 수 있는 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Mymultiset::const_reverse_iterator crit = c1.rbegin();   
    for (; crit != c1.rend(); ++crit)   
        System::Console::Write(" {0}", *crit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  
  
## <a name="count"></a> multiset:: count (STL/CLR)
지정한 키와 일치하는 요소의 수를 찾습니다.  
  
### <a name="syntax"></a>구문  
  
```  
size_type count(key_type key);  
```  
  
#### <a name="parameters"></a>매개 변수  
 key  
 검색할 키 값입니다.  
  
### <a name="remarks"></a>설명  
 멤버 함수는 사용 순서 지정이 동일할 제어 된 시퀀스의 요소 수를 반환 `key`합니다. 지정된 된 키와 일치 하는 제어 되는 시퀀스의 현재 요소 수를 확인 하려면 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_count.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));   
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));   
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
count(L'A') = 0  
count(L'b') = 1  
count(L'C') = 0  
```  
  
## <a name="difference_type"></a> multiset:: difference_type (STL/CLR)
두 요소 사이의 부호가 있는 거리의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>설명  
 형식은 음수 수 있는 요소 수를 설명 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_difference_type.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Mymultiset::difference_type diff = 0;   
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (Mymultiset::iterator it = c1.end(); it != c1.begin(); --it)   
        --diff;   
    System::Console::WriteLine("begin()-end() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
begin()-end() = -3  
```  

## <a name="empty"></a> multiset:: empty (STL/CLR)
요소가 있는지 여부를 테스트합니다.  
  
### <a name="syntax"></a>구문  
  
```  
bool empty();  
```  
  
### <a name="remarks"></a>설명  
 멤버 함수는 빈 제어되는 시퀀스에 대해 true를 반환합니다. 동일 [multiset:: size (STL/CLR)](../dotnet/multiset-size-stl-clr.md)`() == 0`합니다. Multiset이 비어 있는지 여부를 테스트 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_empty.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
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
  
## <a name="end"></a> multiset:: end (STL/CLR)
제어되는 시퀀스의 끝을 지정합니다.  
  
### <a name="syntax"></a>구문  
  
```  
iterator end();  
```  
  
### <a name="remarks"></a>설명  
 멤버 함수는 제어 된 시퀀스의 끝 바로 다음을 가리키는 양방향 반복기를 반환합니다. 제어 된 시퀀스의 끝을 지정 하는 반복기를 가져올 사용 해당 상태 대상이 제어 된 시퀀스의 길이가 변경 하는 경우 변경 되지 않습니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_end.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last two items   
    Mymultiset::iterator it = c1.end();   
    --it;   
    System::Console::WriteLine("*-- --end() = {0}", *--it);   
    System::Console::WriteLine("*--end() = {0}", *++it);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --end() = b  
*--end() = c  
```  

## <a name="equal_range"></a> multiset:: equal_range (STL/CLR)
지정된 키와 일치하는 범위를 찾습니다.  
  
### <a name="syntax"></a>구문  
  
```  
cliext::pair<iterator, iterator> equal_range(key_type key);  
```  
  
#### <a name="parameters"></a>매개 변수  
 key  
 검색할 키 값입니다.  
  
### <a name="remarks"></a>설명  
 멤버 함수는 한 쌍의 반복기를 반환 `cliext::pair<iterator, iterator>(` [multiset:: lower_bound (STL/CLR)](../dotnet/multiset-lower-bound-stl-clr.md) `(key),` [multiset:: upper_bound (STL/CLR)](../dotnet/multiset-upper-bound-stl-clr.md)`(key))`합니다. 지정된 된 키와 일치 하는 제어 된 시퀀스의 현재 요소의 범위를 확인 하려면 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_equal_range.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
typedef Mymultiset::pair_iter_iter Pairii;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display results of failed search   
    Pairii pair1 = c1.equal_range(L'x');   
    System::Console::WriteLine("equal_range(L'x') empty = {0}",   
        pair1.first == pair1.second);   
  
// display results of successful search   
    pair1 = c1.equal_range(L'b');   
    for (; pair1.first != pair1.second; ++pair1.first)   
        System::Console::Write(" {0}", *pair1.first);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
equal_range(L'x') empty = True  
 b  
```  

## <a name="erase"></a> multiset:: erase (STL/CLR)
지정된 위치에 있는 요소를 제거합니다.  
  
### <a name="syntax"></a>구문  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
size_type erase(key_type key)  
```  
  
#### <a name="parameters"></a>매개 변수  
 첫 번째  
 범위를 지우려면의 시작입니다.  
  
 key  
 지우기 키 값입니다.  
  
 last  
 범위를 지우려면의 끝입니다.  
  
 형식에 대한 설명  
 지울 요소입니다.  
  
### <a name="remarks"></a>설명  
 가 가리키는 제어 된 시퀀스의 요소를 제거 하는 첫 번째 멤버 함수 `where`를 제거 하는 요소 뒤에 남은 첫 번째 요소를 지정 하는 반복기를 반환 하 고 또는 [multiset:: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md) `()` 이러한 요소가 없을 경우. 단일 요소를 제거 하려면 사용 합니다.  
  
 범위에서 제어 된 시퀀스의 요소를 제거 하는 두 번째 멤버 함수 [`first`, `last`), 제거 된 요소 뒤에 남은 첫 번째 요소를 지정 하는 반복기를 반환 하거나 `end()` 요소가 없는 경우 있습니다. 0 개 이상의 연속 요소를 제거 하려면 사용 합니다.  
  
 해당 키가 동일 하 게 정렬 된 제어 된 시퀀스의 모든 요소를 제거 하는 세 번째 멤버 함수를 `key`, 제거 된 요소의 수를 반환 합니다. 제거 하 고 계산 된 지정 된 키와 일치 하는 모든 요소를 사용 합니다.  
  
 각 요소 삭제 시간이의 요소 수 로그에 비례 제어 된 시퀀스의 됩니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_erase.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.insert(L'd');   
    c1.insert(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    Mymultiset::iterator it = c1.end();   
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

## <a name="find"></a> multiset:: find (STL/CLR)
지정된 키와 일치하는 요소를 찾습니다.  
  
### <a name="syntax"></a>구문  
  
```  
iterator find(key_type key);  
```  
  
#### <a name="parameters"></a>매개 변수  
 key  
 검색할 키 값입니다.  
  
### <a name="remarks"></a>설명  
 동일 하 게 정렬 된 제어 되는 시퀀스에 요소가 하나 이상 있으면 `key`, 이러한 요소 중 하나를 지정 하는 반복기를 반환 하는 멤버 함수, 그렇지 않으면 반환 [multiset:: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md) `()`. 지정된 된 키와 일치 하는 제어 된 시퀀스의 현재 요소를 찾을 수 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_find.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'A', c1.find(L'A') != c1.end());   
    System::Console::WriteLine("find {0} = {1}",   
        L'b', *c1.find(L'b'));   
    System::Console::WriteLine("find {0} = {1}",   
        L'C', c1.find(L'C') != c1.end());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
find A = False  
find b = b  
find C = False  
```  

## <a name="generic_container"></a> multiset:: generic_container (STL/CLR)
컨테이너에 대 한 제네릭 인터페이스의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef Microsoft::VisualC::StlClr::  
    ITree<GKey, GValue>  
    generic_container;  
```  
  
### <a name="remarks"></a>설명  
 이 형식은이 서식 파일 컨테이너 클래스에 대 한 제네릭 인터페이스를 설명 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_generic_container.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mymultiset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->insert(L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.insert(L'e');   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
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

## <a name="generic_iterator"></a> multiset:: generic_iterator (STL/CLR)
컨테이너에 대 한 제네릭 인터페이스와 함께 사용 하기 위해 반복기의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ContainerBidirectionalIterator<generic_value>  
    generic_iterator;  
```  
  
### <a name="remarks"></a>설명  
 형식은이 서식 파일 컨테이너 클래스에 대 한 제네릭 인터페이스와 함께 사용할 수 있는 일반 반복기를 설명 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mymultiset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Mymultiset::generic_iterator gcit = gc1->begin();   
    Mymultiset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a  
```  

## <a name="generic_reverse_iterator"></a> multiset:: generic_reverse_iterator (STL/CLR)
컨테이너에 대 한 제네릭 인터페이스와 함께 사용 하기 위해 한 반대 반복기의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ReverseRandomAccessIterator<generic_value>  
    generic_reverse_iterator;  
```  
  
### <a name="remarks"></a>설명  
 형식은이 서식 파일 컨테이너 클래스에 대 한 제네릭 인터페이스와 함께 사용할 수 있는 제네릭 역방향 반복기를 설명 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mymultiset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Mymultiset::generic_reverse_iterator gcit = gc1->rbegin();   
    Mymultiset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
c  
``` 

## <a name="generic_value"></a> multiset:: generic_value (STL/CLR)
컨테이너에 대 한 제네릭 인터페이스와 함께 사용 하기 위해 요소의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>설명  
 이 형식은 형식의 개체를 설명 `GValue` 이 서식 파일 컨테이너 클래스에 대 한 제네릭 인터페이스와 함께 사용 하기 위해 저장 된 요소 값을 설명 하는 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_generic_value.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mymultiset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Mymultiset::generic_iterator gcit = gc1->begin();   
    Mymultiset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a  
```   

## <a name="insert"></a> multiset:: insert (STL/CLR)
요소를 추가합니다.  
  
### <a name="syntax"></a>구문  
  
```  
iterator insert(value_type val);  
iterator insert(iterator where, value_type val);  
template<typename InIter>  
    void insert(InIter first, InIter last);  
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);  
```  
  
#### <a name="parameters"></a>매개 변수  
 첫 번째  
 삽입할 범위의의 시작입니다.  
  
 last  
 삽입할 범위의 끝입니다.  
  
 오른쪽  
 삽입 하는 열거형입니다.  
  
 val  
 삽입할 키 값입니다.  
  
 형식에 대한 설명  
 (힌트에만 해당)를 삽입할 컨테이너의 위치입니다.  
  
### <a name="remarks"></a>설명  
 각 멤버 함수는 나머지 피연산자에서 지정 된 시퀀스를 삽입 합니다.  
  
 첫 번째 멤버 함수는 값을 가진 요소를 삽입 `val`, 새로 삽입된 된 요소를 지정 하는 반복기를 반환 합니다. 단일 요소를 삽입 하려면 사용 합니다.  
  
 두 번째 멤버 함수는 값을 가진 요소를 삽입 `val`를 사용 하 여 `where` (성능을 향상 시키기) 힌트로 새로 삽입된 된 요소를 지정 하는 반복기를 반환 합니다. 알고 있는 요소에 인접 한 될 수 있는 단일 요소를 삽입 하려면 사용 합니다.  
  
 세 번째 멤버 함수는 시퀀스를 삽입 [`first`, `last`). 다른 시퀀스에서 복사 된 0 개 이상의 요소를 삽입 하려면 사용 합니다.  
  
 로 지정 된 시퀀스를 삽입 하는 네 번째 멤버 함수는 `right`합니다. 열거자에서 설명 하는 시퀀스를 삽입 하려면 사용 합니다.  
  
 제어 된 시퀀스의 요소 수 로그 비례 하는 시간을 사용 하는 각 요소를 삽입 합니다. 그러나 삽입 발생할 수 있습니다 분할 상환된 상수 시간에 삽입 지점에 인접 하는 요소를 지정 하는 힌트를 제공 합니다.  
  
### <a name="example"></a>예  
  
```cpp
// cliext_multiset_insert.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
    System::Console::WriteLine("insert(L'x') = {0}",   
        *c1.insert(L'x'));   
  
    System::Console::WriteLine("insert(L'b') = {0}",   
        *c1.insert(L'b'));   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    System::Console::WriteLine("insert(begin(), L'y') = {0}",   
        *c1.insert(c1.begin(), L'y'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Mymultiset c2;   
    Mymultiset::iterator it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Mymultiset c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
insert(L'x') = x  
insert(L'b') = b  
 a b b c x  
insert(begin(), L'y') = y  
 a b b c x y  
 a b b c x  
 a b b c x y  
```  

## <a name="iterator"></a> multiset:: iterator (STL/CLR)
제어되는 시퀀스에 대한 반복기의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>설명  
 이 형식은 지정 되지 않은 형식의 개체를 설명 `T1` 제어 되는 시퀀스에 대 한 양방향 반복기로 사용할 수 있는 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Mymultiset::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="key_comp"></a> multiset:: key_comp (STL/CLR)
두 키에 대 한 순서 지정 대리자를 복사합니다.  
  
### <a name="syntax"></a>구문  
  
```  
key_compare^key_comp();  
```  
  
### <a name="remarks"></a>설명  
 멤버 함수는 제어 되는 시퀀스를 정렬 하는 데 사용 되는 정렬 대리자를 반환 합니다. 두 키를 비교할를 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp 
// cliext_multiset_key_comp.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    Mymultiset::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Mymultiset c2 = cliext::greater<wchar_t>();   
    kcomp = c2.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
  
compare(L'a', L'a') = False  
compare(L'a', L'b') = False  
compare(L'b', L'a') = True  
```  

## <a name="key_compare"></a> multiset:: key_compare (STL/CLR)
두 키에 대 한 순서 지정 하는 대리자입니다.  
  
### <a name="syntax"></a>구문  
  
```  
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>  
    key_compare;  
```  
  
### <a name="remarks"></a>설명  
 형식은 키 해당 인수의 순서를 결정 하는 대리자에 대 한 동의어입니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_key_compare.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    Mymultiset::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Mymultiset c2 = cliext::greater<wchar_t>();   
    kcomp = c2.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
  
compare(L'a', L'a') = False  
compare(L'a', L'b') = False  
compare(L'b', L'a') = True  
```  

## <a name="key_type"></a> multiset:: key_type (STL/CLR)
정렬 키의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>설명  
 이 형식은 템플릿 매개 변수 `Key`의 동의어입니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_key_type.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" using key_type   
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in key_type object   
        Mymultiset::key_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="lower_bound"></a> multiset:: lower_bound (STL/CLR)
지정된 된 키와 일치 하는 범위의 시작 부분을 찾습니다.  
  
### <a name="syntax"></a>구문  
  
```  
iterator lower_bound(key_type key);  
```  
  
#### <a name="parameters"></a>매개 변수  
 key  
 검색할 키 값입니다.  
  
### <a name="remarks"></a>설명  
 멤버 함수는 첫 번째 요소를 결정 `X` 과 순서가 제어 된 시퀀스의 `key`합니다. 이러한 요소가 있는 경우 반환 [multiset:: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`; 그렇지 않으면 지정 하는 반복기를 반환 `X`합니다. 지정된 된 키와 일치 하는 제어 된 시퀀스의 요소 시퀀스의 시작 부분을 현재 찾을 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_lower_bound.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*lower_bound(L'a') = {0}",   
        *c1.lower_bound(L'a'));   
    System::Console::WriteLine("*lower_bound(L'b') = {0}",   
        *c1.lower_bound(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
lower_bound(L'x')==end() = True  
*lower_bound(L'a') = a  
*lower_bound(L'b') = b  
```  

## <a name="make_value"></a> multiset:: make_value (STL/CLR)
값 개체를 만듭니다.  
  
### <a name="syntax"></a>구문  
  
```  
static value_type make_value(key_type key);  
```  
  
#### <a name="parameters"></a>매개 변수  
 key  
 사용할 키 값입니다.  
  
### <a name="remarks"></a>설명  
 멤버 함수가 반환 하는 `value_type` 개체 키가 `key`합니다. 여러 다른 멤버 함수 사용에 적합 한 개체를 작성 하려면 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_make_value.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(Mymultiset::make_value(L'a'));   
    c1.insert(Mymultiset::make_value(L'b'));   
    c1.insert(Mymultiset::make_value(L'c'));   
  
// display contents " a b c"   
    for each (Mymultiset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="multiset"></a> multiset:: multiset (STL/CLR)
컨테이너 개체를 만듭니다.  
  
### <a name="syntax"></a>구문  
  
```  
multiset();  
explicit multiset(key_compare^ pred);  
multiset(multiset<Key>% right);  
multiset(multiset<Key>^ right);  
template<typename InIter>  
    multisetmultiset(InIter first, InIter last);  
template<typename InIter>  
    multiset(InIter first, InIter last,  
        key_compare^ pred);  
multiset(System::Collections::Generic::IEnumerable<GValue>^ right);  
multiset(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
```  
  
#### <a name="parameters"></a>매개 변수  
 첫 번째  
 삽입할 범위의의 시작입니다.  
  
 last  
 삽입할 범위의 끝입니다.  
  
 pred  
 제어 되는 시퀀스에 대 한 조건자를 정렬 합니다.  
  
 오른쪽  
 삽입할 개체 또는 범위입니다.  
  
### <a name="remarks"></a>설명  
 생성자:  
  
 `multiset();`  
  
 기본 조건자를 정렬 된 요소가 없는 제어 되는 시퀀스를 초기화 `key_compare()`합니다. 기본 조건자를 정렬 된는 빈 초기 제어 시퀀스를 지정 하려면 사용 합니다.  
  
 생성자:  
  
 `explicit multiset(key_compare^ pred);`  
  
 정렬 조건자가 있는 요소가 없는 제어 되는 시퀀스를 초기화 `pred`합니다. 지정 된 정렬 조건부와 함께 빈 초기 제어 시퀀스를 지정 하려면 사용 합니다.  
  
 생성자:  
  
 `multiset(multiset<Key>% right);`  
  
 순서와 제어 된 시퀀스를 초기화 합니다. [`right.begin()`, `right.end()`), 조건자 순서 기본값입니다. Multiset 개체에 의해 제어 되는 시퀀스의 복사본 인는 초기 제어 시퀀스를 지정 하려면 사용할 `right`, 조건자 순서 기본값입니다.  
  
 생성자:  
  
 `multiset(multiset<Key>^ right);`  
  
 순서와 제어 된 시퀀스를 초기화 합니다. [`right->begin()`, `right->end()`), 조건자 순서 기본값입니다. Multiset 개체에 의해 제어 되는 시퀀스의 복사본 인는 초기 제어 시퀀스를 지정 하려면 사용할 `right`, 조건자 순서 기본값입니다.  
  
 생성자:  
  
 `template<typename InIter> multiset(InIter first, InIter last);`  
  
 순서와 제어 된 시퀀스를 초기화 합니다. [`first`, `last`), 조건자 순서 기본값입니다. 기본 조건자를 정렬 된 제어 되는 다른 시퀀스의 복사본을 확인을 사용 합니다.  
  
 생성자:  
  
 `template<typename InIter> multiset(InIter first, InIter last, key_compare^ pred);`  
  
 순서와 제어 된 시퀀스를 초기화 합니다. [`first`, `last`), 정렬 조건부와 함께 `pred`합니다. 제어 되는 시퀀스의 사본을 지정 된 정렬 조건부와 함께 다른 시퀀스를 사용 합니다.  
  
 생성자:  
  
 `multiset(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 열거자에 지정 된 시퀀스와 제어 된 시퀀스를 초기화 `right`, 조건자 순서 기본값입니다. 제어 되는 시퀀스의 사본을 설명 하는 열거자에 따라 기본 조건자를 정렬 하는 다른 시퀀스를 사용 합니다.  
  
 생성자:  
  
 `multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 열거자에 지정 된 시퀀스와 제어 된 시퀀스를 초기화 `right`, 정렬 조건부와 함께 `pred`합니다. 제어 되는 시퀀스에서 지정 된 정렬 조건부와 함께 열거자를 설명 하는 다른 시퀀스의 복사본 수 있도록 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_construct.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
// construct an empty container   
    Mymultiset c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mymultiset c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mymultiset c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mymultiset c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Mymultiset c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Mymultiset c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Mymultiset c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mymultiset c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 a b c  
size() = 0  
 c b a  
 a b c  
 c b a  
 a b c  
 c b a  
 c b a  
 a b c  
```  

## <a name="op_as"></a> multiset:: operator = (STL/CLR)
제어되는 시퀀스를 바꿉니다.  
  
### <a name="syntax"></a>구문  
  
```  
multiset<Key>% operator=(multiset<Key>% right);  
```  
  
#### <a name="parameters"></a>매개 변수  
 오른쪽  
 복사할 컨테이너입니다.  
  
### <a name="remarks"></a>설명  
 멤버 연산자 복사본 `right` 개체에 반환 `*this`합니다. 이를 사용하여 제어되는 시퀀스를 `right`의 제어되는 시퀀스 복사본으로 대체합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_operator_as.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (Mymultiset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymultiset c2;   
    c2 = c1;   
// display contents " a b c"   
    for each (Mymultiset::value_type elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
```  

## <a name="rbegin"></a> multiset:: rbegin (STL/CLR)
제어되는 역방향 시퀀스의 시작을 지정합니다.  
  
### <a name="syntax"></a>구문  
  
```  
reverse_iterator rbegin();  
```  
  
### <a name="remarks"></a>설명  
 멤버 함수는 빈 시퀀스의 시작 부분 바로 다음 또는 제어 된 시퀀스의 마지막 요소를 지정 하는 역방향 반복기를 반환 합니다. 따라서을 지정 된 `beginning` 역방향 시퀀스의 합니다. 지정 하는 반복기를 사용 하면는 `current` 제어 된 시퀀스를 역순으로 표시 하지만 해당 상태의 시작 부분 제어 된 시퀀스의 길이가 변경 되 면 변경할 수 있습니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_rbegin.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Mymultiset::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = {0}", *rit);   
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*rbegin() = c  
*++rbegin() = b  
```  
  
## <a name="reference"></a> multiset:: reference (STL/CLR)
요소에 대한 참조의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>설명  
 이 형식은 요소에 대 한 참조를 설명 합니다.  
  
### <a name="example"></a>예  
  
```  
// cliext_multiset_reference.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    Mymultiset::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        Mymultiset::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="rend"></a> multiset:: rend (STL/CLR)
제어되는 역방향 시퀀스의 끝을 지정합니다.  
  
### <a name="syntax"></a>구문  
  
```  
reverse_iterator rend();  
```  
  
### <a name="remarks"></a>설명  
 멤버 함수는 제어 된 시퀀스의 시작 부분 바로 다음 가리키는 역방향 반복기를 반환합니다. 따라서을 지정 된 `end` 역방향 시퀀스의 합니다. 지정 하는 반복기를 사용 하면는 `current` 제어 된 시퀀스를 역순으로 표시 하지만 해당 상태의 끝 제어 된 시퀀스의 길이가 변경 되 면 변경할 수 있습니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_rend.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Mymultiset::reverse_iterator rit = c1.rend();   
    --rit;   
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);   
    System::Console::WriteLine("*--rend() = {0}", *++rit);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --rend() = b  
*--rend() = a  
```  

## <a name="reverse_iterator"></a> multiset:: reverse_iterator (STL/CLR)
제어되는 시퀀스에 대한 반대 반복기의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef T3 reverse_iterator;  
```  
  
### <a name="remarks"></a>설명  
 이 형식은 제어된 시퀀스에 대해 반대 반복기로 사용될 수 있는 지정되지 않은 `T3` 형식의 개체를 설명합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Mymultiset::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  
  
## <a name="size"></a> multiset:: size (STL/CLR)
요소 수를 계산합니다.  
  
### <a name="syntax"></a>구문  
  
```  
size_type size();  
```  
  
### <a name="remarks"></a>설명  
 멤버 함수는 제어되는 시퀀스의 길이를 반환합니다. 제어 되는 시퀀스의 현재 요소 수를 확인 하려면 사용 합니다. 모든 경우에 중요 한 여부 시퀀스 크기가 0이 아닌 참조 [multiset:: empty (STL/CLR)](../dotnet/multiset-empty-stl-clr.md)`()`합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_size.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
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
  
## <a name="size_type"></a> multiset:: size_type (STL/CLR)
두 요소 사이의 부호가 있는 거리의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef int size_type;  
```  
  
### <a name="remarks"></a>설명  
 형식은은 음수가 아닌 요소 수를 설명 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_size_type.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Mymultiset::size_type diff = 0;   
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```  

## <a name="swap"></a> multiset:: swap (STL/CLR)
두 컨테이너의 내용을 바꿉니다.  
  
### <a name="syntax"></a>구문  
  
```  
void swap(multiset<Key>% right);  
```  
  
#### <a name="parameters"></a>매개 변수  
 오른쪽  
 콘텐츠와 바꿀 컨테이너입니다.  
  
### <a name="remarks"></a>설명  
 멤버 함수는 `this` 와 `right`간에 제어되는 시퀀스를 교환합니다. 일정 한 시간에 작업을 수행 하 고 예외가 throw 됩니다. 두 컨테이너의 내용을 교환에 신속 하 게 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_swap.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    Mymultiset c2;   
    c2.insert(L'd');   
    c2.insert(L'e');   
    c2.insert(L'f');   
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
d e f  
d e f  
a b c  
```  

## <a name="to_array"></a> multiset:: to_array (STL/CLR)
제어 되는 새 배열에 복사합니다.  
  
### <a name="syntax"></a>구문  
  
```  
cli::array<value_type>^ to_array();  
```  
  
### <a name="remarks"></a>설명  
 멤버 함수는 제어 되는 시퀀스를 포함 하는 배열을 반환 합니다. 배열 형식으로 제어 되는 시퀀스의 복사본을 사용 하면 됩니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_to_array.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// copy the container and modify it   
    cli::array<wchar_t>^ a1 = c1.to_array();   
  
    c1.insert(L'd');   
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

## <a name="upper_bound"></a> multiset:: upper_bound (STL/CLR)
지정된 된 키와 일치 하는 범위의 끝을 찾습니다.  
  
### <a name="syntax"></a>구문  
  
```  
iterator upper_bound(key_type key);  
```  
  
#### <a name="parameters"></a>매개 변수  
 key  
 검색할 키 값입니다.  
  
### <a name="remarks"></a>설명  
 멤버 함수는 마지막 요소를 결정 `X` 과 순서가 제어 된 시퀀스의 `key`합니다. 이러한 요소가 존재 하거나 `X` 는 제어 된 시퀀스의 마지막 요소 반환 [multiset:: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`; 그렇지 않으면 의첫번째요소를지정하는반복기를반환`X`. 지정된 된 키와 일치 하는 제어 된 시퀀스의 현재 요소 시퀀스의 끝으로 이동 하려면 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_upper_bound.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*upper_bound(L'a') = {0}",   
        *c1.upper_bound(L'a'));   
    System::Console::WriteLine("*upper_bound(L'b') = {0}",   
        *c1.upper_bound(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
upper_bound(L'x')==end() = True  
*upper_bound(L'a') = b  
*upper_bound(L'b') = c  
```  
  
## <a name="value_comp"></a> multiset:: value_comp (STL/CLR)
두 요소 값에 대 한 순서 지정 대리자를 복사합니다.  
  
### <a name="syntax"></a>구문  
  
```  
value_compare^ value_comp();  
```  
  
### <a name="remarks"></a>설명  
 멤버 함수는 제어 되는 시퀀스를 정렬 하는 데 사용 되는 정렬 대리자를 반환 합니다. 두 요소 값 비교를 사용 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_value_comp.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    Mymultiset::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
```  

## <a name="value_compare"></a> multiset:: value_compare (STL/CLR)
두 요소 값에 대 한 순서 지정 하는 대리자입니다.  
  
### <a name="syntax"></a>구문  
  
```  
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>  
    value_compare;  
```  
  
### <a name="remarks"></a>설명  
 유형 인수 값의 순서를 결정 하는 대리자에 대 한 동의어입니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_value_compare.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    Mymultiset::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
```  

## <a name="value_type"></a> multiset:: value_type (STL/CLR)
요소의 형식입니다.  
  
### <a name="syntax"></a>구문  
  
```  
typedef generic_value value_type;  
```  
  
### <a name="remarks"></a>설명  
 이 형식은 `generic_value`의 동의어입니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_value_type.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" using value_type   
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in value_type object   
        Mymultiset::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="op_neq"></a> operator! = (multiset) (STL/CLR)
같지 않음 비교를 나열 합니다.  
  
### <a name="syntax"></a>구문  
  
```  
template<typename Key>  
    bool operator!=(multiset<Key>% left,  
        multiset<Key>% right);  
```  
  
#### <a name="parameters"></a>매개 변수  
 왼쪽  
 비교할 왼쪽 컨테이너입니다.  
  
 오른쪽  
 비교할 오른쪽 컨테이너입니다.  
  
### <a name="remarks"></a>설명  
 연산자 함수 반환 `!(left == right)`합니다. 테스트를 사용 하는지 여부를 `left` 동일 정렬 되지 않은 `right` 때 두 개의 다중 집합은 요소 별로 비교 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_operator_ne.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymultiset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
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

## <a name="op_lt"></a> 연산자&lt; (multiset) (STL/CLR)
목록 비교 보다 작습니다.  
  
### <a name="syntax"></a>구문  
  
```  
template<typename Key>  
    bool operator<(multiset<Key>% left,  
        multiset<Key>% right);  
```  
  
#### <a name="parameters"></a>매개 변수  
 왼쪽  
 비교할 왼쪽 컨테이너입니다.  
  
 오른쪽  
 비교할 오른쪽 컨테이너입니다.  
  
### <a name="remarks"></a>설명  
 연산자 함수 이면 true를 반환, 가장 낮은 위치에 대 한 `i` 를 `!(right[i] < left[i])` 도 true 하는 것이 `left[i] < right[i]`합니다. 그렇지 않으면 반환 `left->size() < right->size()` 테스트를 사용 하는지 여부를 `left` 앞에 정렬 `right` 때 두 개의 다중 집합은 요소 별로 비교 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_operator_lt.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymultiset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
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

## <a name="op_lteq"></a> 연산자&lt;= (multiset) (STL/CLR)
목록 보다 작거나 같은지 비교 합니다.  
  
### <a name="syntax"></a>구문  
  
```  
template<typename Key>  
    bool operator<=(multiset<Key>% left,  
        multiset<Key>% right);  
```  
  
#### <a name="parameters"></a>매개 변수  
 왼쪽  
 비교할 왼쪽 컨테이너입니다.  
  
 오른쪽  
 비교할 오른쪽 컨테이너입니다.  
  
### <a name="remarks"></a>설명  
 연산자 함수 반환 `!(right < left)`합니다. 테스트를 사용 하는지 여부를 `left` 후 정렬 되지 않은 `right` 때 두 개의 다중 집합은 요소 별로 비교 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_operator_le.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymultiset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
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

## <a name="op_eq"></a> 연산자 = = (multiset) (STL/CLR)
같음 비교를 나열 합니다.  
  
### <a name="syntax"></a>구문  
  
```  
template<typename Key>  
    bool operator==(multiset<Key>% left,  
        multiset<Key>% right);  
```  
  
#### <a name="parameters"></a>매개 변수  
 왼쪽  
 비교할 왼쪽 컨테이너입니다.  
  
 오른쪽  
 비교할 오른쪽 컨테이너입니다.  
  
### <a name="remarks"></a>설명  
 연산자 함수는 시퀀스에 의해 제어 하는 경우에 true를 반환 `left` 및 `right` 동일한 길이 및 각 위치에 대 한 `i`, `left[i] ==` `right[i]`합니다. 테스트를 사용 하는지 여부를 `left` 와 동일 하 게 정렬 되 `right` 때 두 개의 다중 집합은 요소 별로 비교 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_operator_eq.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymultiset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
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

## <a name="op_gt"></a> 연산자&gt; (multiset) (STL/CLR)
목록 비교 보다 큽니다.  
  
### <a name="syntax"></a>구문  
  
```  
template<typename Key>  
    bool operator>(multiset<Key>% left,  
        multiset<Key>% right);  
```  
  
#### <a name="parameters"></a>매개 변수  
 왼쪽  
 비교할 왼쪽 컨테이너입니다.  
  
 오른쪽  
 비교할 오른쪽 컨테이너입니다.  
  
### <a name="remarks"></a>설명  
 연산자 함수 반환 `right` `<` `left`합니다. 테스트를 사용 하는지 여부를 `left` 후 정렬 `right` 때 두 개의 다중 집합은 요소 별로 비교 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_operator_gt.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymultiset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
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

## <a name="op_gteq"></a> 연산자&gt;= (multiset) (STL/CLR)
보다 큰 목록 또는 같은지 비교 합니다.  
  
### <a name="syntax"></a>구문  
  
```  
template<typename Key>  
    bool operator>=(multiset<Key>% left,  
        multiset<Key>% right);  
```  
  
#### <a name="parameters"></a>매개 변수  
 왼쪽  
 비교할 왼쪽 컨테이너입니다.  
  
 오른쪽  
 비교할 오른쪽 컨테이너입니다.  
  
### <a name="remarks"></a>설명  
 연산자 함수 반환 `!(left < right)`합니다. 테스트를 사용 하는지 여부를 `left` 하기 전에 정렬 되지 않은 `right` 때 두 개의 다중 집합은 요소 별로 비교 합니다.  
  
### <a name="example"></a>예  
  
```cpp  
// cliext_multiset_operator_ge.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymultiset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
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
  