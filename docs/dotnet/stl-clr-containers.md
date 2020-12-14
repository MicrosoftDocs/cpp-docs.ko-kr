---
description: '자세한 정보: STL/CLR 컨테이너'
title: STL/CLR 컨테이너
ms.date: 09/18/2018
ms.topic: reference
helpviewer_keywords:
- STL/CLR, containers
- containers, STL/CLR
ms.assetid: 34ca8031-2041-46b9-aed9-29082d1972ea
ms.openlocfilehash: 945533f616abe37763d9963d46d87f02a3c077fa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335343"
---
# <a name="stlclr-containers"></a>STL/CLR 컨테이너

STL/CLR 라이브러리는 c + + 표준 라이브러리에 있는 것과 유사한 컨테이너로 구성 되지만 .NET Framework의 관리 되는 환경에서 실행 됩니다. 실제 c + + 표준 라이브러리를 사용 하 여 최신 상태로 유지 되지 않으며 레거시 지원을 위해 유지 관리 됩니다.

이 문서에서는 STL/CLR의 컨테이너에 대 한 개요를 제공 합니다. 예를 들어 컨테이너 요소에 대 한 요구 사항, 컨테이너에 삽입할 수 있는 요소 형식, 컨테이너의 요소에 대 한 소유권 문제 등이 있습니다. 해당 하는 경우 네이티브 c + + 표준 라이브러리와 STL/CLR의 차이점을 언급 합니다.

## <a name="requirements-for-container-elements"></a>컨테이너 요소에 대한 요구 사항

STL/CLR 컨테이너에 삽입 된 모든 요소는 특정 지침을 준수 해야 합니다. 자세한 내용은 [STL/CLR 컨테이너 요소에 대 한 요구 사항](../dotnet/requirements-for-stl-clr-container-elements.md)을 참조 하세요.

## <a name="valid-container-elements"></a>유효한 컨테이너 요소

STL/CLR 컨테이너는 다음 두 가지 유형의 요소 중 하나를 보유할 수 있습니다.

- 참조 형식에 대 한 핸들입니다.

- 참조 형식.

- Unboxed 값 형식입니다.

STL/CLR 컨테이너에는 boxed 값 형식을 삽입할 수 없습니다.

### <a name="handles-to-reference-types"></a>참조 형식에 대 한 핸들

참조 형식에 대 한 핸들을 STL/CLR 컨테이너에 삽입할 수 있습니다. CLR을 대상으로 하는 c + +의 핸들은 native c + +의 포인터와 유사 합니다. 자세한 내용은 [개체 연산자에 대 한 핸들 (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)을 참조 하세요.

#### <a name="example"></a>예제

다음 예제에서는 [cliext:: set](../dotnet/set-stl-clr.md)에 Employee 개체에 대 한 핸들을 삽입 하는 방법을 보여 줍니다.

```cpp
// cliext_container_valid_reference_handle.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

ref class Employee
{
public:
    // STL/CLR containers might require a public constructor, so it
    // is a good idea to define one.
    Employee() :
        name(nullptr),
        employeeNumber(0) { }

    // All STL/CLR containers require a public copy constructor.
    Employee(const Employee% orig) :
        name(orig.name),
        employeeNumber(orig.employeeNumber) { }

    // All STL/CLR containers require a public assignment operator.
    Employee% operator=(const Employee% orig)
    {
        if (this != %orig)
        {
            name = orig.name;
            employeeNumber = orig.employeeNumber;
        }

        return *this;
    }

    // All STL/CLR containers require a public destructor.
    ~Employee() { }

    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee^ empl1419 = gcnew Employee();
    empl1419->Name = L"Darin Lockert";
    empl1419->EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee^>^ emplSet = gcnew set<Employee^>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee^ empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl->EmployeeNumber, empl->Name);
    }

    return 0;
}
```

### <a name="reference-types"></a>참조 형식

참조 형식에 대 한 핸들 대신 참조 형식을 STL/CLR 컨테이너에 삽입할 수도 있습니다. 여기서 주요 차이점은 참조 형식의 컨테이너를 삭제 하면 해당 컨테이너 내의 모든 요소에 대해 소멸자가 호출 된다는 것입니다. 참조 형식에 대 한 핸들의 컨테이너에서는 이러한 요소에 대 한 소멸자가 호출 되지 않습니다.

#### <a name="example"></a>예제

다음 예제에서는 Employee 개체를에 삽입 하는 방법을 보여 줍니다 `cliext::set` .

```cpp
// cliext_container_valid_reference.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

ref class Employee
{
public:
    // STL/CLR containers might require a public constructor, so it
    // is a good idea to define one.
    Employee() :
        name(nullptr),
        employeeNumber(0) { }

    // All STL/CLR containers require a public copy constructor.
    Employee(const Employee% orig) :
        name(orig.name),
        employeeNumber(orig.employeeNumber) { }

    // All STL/CLR containers require a public assignment operator.
    Employee% operator=(const Employee% orig)
    {
        if (this != %orig)
        {
            name = orig.name;
            employeeNumber = orig.employeeNumber;
        }

        return *this;
    }

    // All STL/CLR containers require a public destructor.
    ~Employee() { }

    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee empl1419;
    empl1419.Name = L"Darin Lockert";
    empl1419.EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee>^ emplSet = gcnew set<Employee>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee^ empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl->EmployeeNumber, empl->Name);
    }

    return 0;
}
```

### <a name="unboxed-value-types"></a>Unboxed 값 형식

STL/CLR 컨테이너에 unboxed 값 형식을 삽입할 수도 있습니다. Unboxed 값 형식은 참조 형식에 *boxing* 되지 않은 값 형식입니다.

값 형식 요소는와 같은 표준 값 형식 중 하나일 수 있으며, **`int`** 와 같은 사용자 정의 값 형식일 수도 있습니다 **`value class`** . 자세한 내용은 [클래스 및 구조체](../extensions/classes-and-structs-cpp-component-extensions.md) 를 참조 하세요.

#### <a name="example"></a>예제

다음 예에서는 Employee 클래스를 값 형식으로 설정 하 여 첫 번째 예제를 수정 합니다. 그런 다음이 값 형식은 `cliext::set` 첫 번째 예제와 마찬가지로에 삽입 됩니다.

```cpp
// cliext_container_valid_valuetype.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

value class Employee
{
public:
    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee empl1419;
    empl1419.Name = L"Darin Lockert";
    empl1419.EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee>^ emplSet = gcnew set<Employee>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl.EmployeeNumber, empl.Name);
    }

    return 0;
}
```

값 형식에 대 한 핸들을 컨테이너에 삽입 하려고 하면 [컴파일러 오류 C3225](../error-messages/compiler-errors-2/compiler-error-c3225.md) 이 생성 됩니다.

### <a name="performance-and-memory-implications"></a>성능 및 메모리 영향

핸들을 사용 하 여 형식 또는 값 형식을 컨테이너 요소로 참조 하는지 여부를 결정할 때 몇 가지 요인을 고려해 야 합니다. 값 형식을 사용 하기로 결정 한 경우 요소가 컨테이너에 삽입 될 때마다 요소의 복사본이 생성 됩니다. 작은 개체의 경우에는이 문제가 문제가 되지 않지만 삽입 중인 개체가 클 경우 성능이 저하 될 수 있습니다. 또한 값 형식을 사용 하는 경우 각 컨테이너에는 요소의 자체 복사본이 있으므로 한 요소를 여러 컨테이너에 동시에 저장할 수 없습니다.

핸들을 사용 하 여 형식을 참조 하기로 결정 한 경우에는 요소가 컨테이너에 삽입 될 때 요소의 복사본을 만들 필요가 없기 때문에 성능이 향상 될 수 있습니다. 또한 값 형식과 달리 동일한 요소가 여러 컨테이너에 있을 수 있습니다. 그러나 핸들을 사용 하기로 결정 한 경우 핸들이 유효 하 고 참조 하는 개체가 프로그램의 다른 위치에서 삭제 되지 않았는지 확인 해야 합니다.

## <a name="ownership-issues-with-containers"></a>컨테이너의 소유권 문제

STL/CLR의 컨테이너는 값 의미 체계에 적용 됩니다. 컨테이너에 요소를 삽입할 때마다 해당 요소의 복사본이 삽입 됩니다. 참조와 유사한 의미 체계를 가져오려는 경우 개체 자체가 아니라 개체에 핸들을 삽입할 수 있습니다.

핸들 개체 컨테이너의 clear 또는 clear 메서드를 호출 하는 경우 핸들이 참조 하는 개체가 메모리에서 해제 되지 않습니다. 개체를 명시적으로 삭제 하거나, 이러한 개체가 관리 되는 힙에 있으므로 가비지 수집기에서 개체가 더 이상 사용 되지 않는 것으로 확인 되 면 메모리를 확보할 수 있도록 허용 해야 합니다.

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
