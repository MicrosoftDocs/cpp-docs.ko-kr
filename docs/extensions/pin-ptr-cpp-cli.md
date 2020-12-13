---
description: '자세한 정보: pin_ptr (c + +/CLI)'
title: pin_ptr(C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- pin_ptr_cpp
- stdcli::language::pin_ptr
- pin_ptr
helpviewer_keywords:
- pinning pointers
- pin_ptr keyword [C++]
ms.assetid: 6c2e6c73-4ec2-4dce-8e1f-ccf3a9f9d0aa
ms.openlocfilehash: c7439b1e8bd1030a5f1326d24b38c47af5bb4874
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341076"
---
# <a name="pin_ptr-ccli"></a>pin_ptr(C++/CLI)

공용 언어 런타임에서만 사용되는 ‘고정 포인터’를 선언합니다.

## <a name="all-runtimes"></a>모든 런타임

(이 언어 기능에는 모든 런타임에 적용되는 설명이 없습니다.)

## <a name="windows-runtime"></a>Windows 런타임

Windows 런타임에서는 이 언어 기능이 지원되지 않습니다.

## <a name="common-language-runtime"></a>공용 언어 런타임

‘고정 포인터’는 가리키는 개체가 가비지 수집된 힙에서 이동하지 않도록 하는 내부 포인터입니다. 즉, 공용 언어 런타임에서 고정 포인터의 값을 변경하지 않습니다. 비관리형 함수 호출을 확인하는 동안 주소가 예기치 않게 변경되지 않도록 관리형 클래스의 주소를 비관리형 함수에 전달하는 경우에 필요합니다.

### <a name="syntax"></a>구문

```cpp
[cli::]pin_ptr<cv_qualifiertype>var = &initializer;
```

### <a name="parameters"></a>매개 변수

*cv_qualifier*<br/>
**`const`** 또는 **`volatile`** 한정자입니다. 기본적으로 고정 포인터는 **`volatile`** 입니다. 중복 되지만 고정 포인터를 선언 하는 데 오류가 발생 하지는 않습니다 **`volatile`** .

*type*<br/>
‘이니셜라이저’의 형식입니다.

*var*<br/>
**pin_ptr** 변수의 이름입니다.

*initializer*<br/>
참조 형식의 멤버, 관리되는 배열의 요소 또는 네이티브 포인터에 할당할 수 있는 다른 모든 개체입니다.

### <a name="remarks"></a>설명

**pin_ptr** 은 네이티브 포인터 기능의 상위 집합을 나타냅니다. 따라서 네이티브 포인터에 할당할 수 있으면 **pin_ptr** 에도 할당할 수 있습니다. 내부 포인터는 네이티브 포인터로서 비교 및 포인터 산술을 포함한 동일한 일련의 작업을 수행할 수 있습니다.

관리형 클래스의 개체 또는 하위 개체를 고정할 수 있으며, 이 경우 공용 언어 런타임에서 가비지 수집 중에 개체를 이동하지 않습니다. 이 포인터는 주로 관리형 데이터에 대한 포인터를 비관리형 함수 호출의 실제 매개 변수로 전달하는 데 사용됩니다. 수집 주기 중에 런타임에서는 고정 포인터에 대해 생성된 메타데이터를 검사하고, 포인터가 가리키는 항목을 이동하지 않습니다.

개체를 고정하면 해당 값 필드, 즉 기본 형식 또는 값 형식의 필드도 고정됩니다. 그러나 추적 핸들(`%`)을 통해 선언된 필드는 고정되지 않습니다.

관리형 개체에 정의된 하위 개체를 고정하면 전체 개체를 고정하는 효과가 있습니다.

새 값을 가리키도록 고정 포인터를 다시 할당하는 경우 이전에 가리킨 인스턴스는 더 이상 고정된 것으로 간주되지 않습니다.

**pin_ptr** 이 가리키는 동안에만 개체가 고정됩니다. 고정 포인터가 범위를 벗어나거나 [nullptr](nullptr-cpp-component-extensions.md)로 설정되면 개체가 더 이상 고정되지 않습니다. **pin_ptr** 이 범위를 벗어나면 가비지 수집기가 힙에서 고정된 개체를 이동할 수 있습니다. 여전히 해당 개체를 가리키는 네이티브 포인터는 업데이트되지 않으며, 네이티브 포인터 중 하나를 역참조하면 복구할 수 없는 예외가 발생할 수 있습니다.

개체를 가리키는 고정 포인터가 없으면(모든 고정 포인터가 범위를 벗어났거나, 다른 개체를 가리키도록 다시 할당되었거나, [nullptr](nullptr-cpp-component-extensions.md)이 할당됨) 개체가 고정되지 않습니다.

고정 포인터는 참조 핸들, 값 형식, boxed 형식 핸들, 관리형 형식의 멤버 또는 관리형 배열의 요소를 가리킬 수 있습니다. 참조 형식은 가리킬 수 없습니다.

네이티브 개체를 가리키는 **pin_ptr** 의 주소를 사용하면 정의되지 않은 동작이 발생합니다.

고정 포인터는 스택에 비정적 지역 변수로만 선언할 수 있습니다.

고정 포인터를 다음 용도로 사용할 수 없습니다.

- 함수 매개 변수

- 함수의 반환 형식

- 클래스의 멤버

- 캐스트의 대상 유형

**pin_ptr** 은 `cli` 네임스페이스에 있습니다. 자세한 내용은 [Platform, default 및 cli 네임스페이스](platform-default-and-cli-namespaces-cpp-component-extensions.md)를 참조하세요.

내부 포인터에 대한 자세한 내용은 [interior_ptr(C++/CLI)](interior-ptr-cpp-cli.md)을 참조하세요.

포인터 고정에 대 한 자세한 내용은 [방법: 포인터 및 배열 고정](how-to-pin-pointers-and-arrays.md) 및 [방법: 고정 포인터 및 값 형식 선언](how-to-declare-pinning-pointers-and-value-types.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/clr`

### <a name="examples"></a>예제

다음 예제에서는 **pin_ptr** 을 사용하여 배열의 첫 번째 요소 위치를 제한합니다.

```cpp
// pin_ptr_1.cpp
// compile with: /clr
using namespace System;
#define SIZE 10

#pragma unmanaged
// native function that initializes an array
void native_function(int* p) {
   for(int i = 0 ; i < 10 ; i++)
    p[i] = i;
}
#pragma managed

public ref class A {
private:
   array<int>^ arr;   // CLR integer array

public:
   A() {
      arr = gcnew array<int>(SIZE);
   }

   void load() {
   pin_ptr<int> p = &arr[0];   // pin pointer to first element in arr
   int* np = p;   // pointer to the first element in arr
   native_function(np);   // pass pointer to native function
   }

   int sum() {
      int total = 0;
      for (int i = 0 ; i < SIZE ; i++)
         total += arr[i];
      return total;
   }
};

int main() {
   A^ a = gcnew A;
   a->load();   // initialize managed array using the native function
   Console::WriteLine(a->sum());
}
```

```Output
45
```

다음 예제에서는 내부 포인터를 고정 포인터로 변환할 수 있으며, 피연산자가 관리형 힙에 있는 경우 address-of 연산자(`&`)의 반환 형식이 내부 포인터임을 보여 줍니다.

```cpp
// pin_ptr_2.cpp
// compile with: /clr
using namespace System;

ref struct G {
   G() : i(1) {}
   int i;
};

ref struct H {
   H() : j(2) {}
   int j;
};

int main() {
   G ^ g = gcnew G;   // g is a whole reference object pointer
   H ^ h = gcnew H;

   interior_ptr<int> l = &(g->i);   // l is interior pointer

   pin_ptr<int> k = &(h->j);   // k is a pinning interior pointer

   k = l;   // ok
   Console::WriteLine(*k);
};
```

```Output
1
```

다음 예제에서는 고정 포인터를 다른 형식으로 캐스팅할 수 있음을 보여 줍니다.

```cpp
// pin_ptr_3.cpp
// compile with: /clr
using namespace System;

ref class ManagedType {
public:
   int i;
};

int main() {
   ManagedType ^mt = gcnew ManagedType;
   pin_ptr<int> pt = &mt->i;
   *pt = 8;
   Console::WriteLine(mt->i);

   char *pc = ( char* ) pt;
   *pc = 255;
   Console::WriteLine(mt->i);
}
```

```Output
8
255
```
