---
description: '자세한 정보: 참조 형식에 대 한 c + + 스택 의미 체계'
title: 참조 형식에 대한 C++ 스택 의미 체계
ms.date: 11/04/2016
helpviewer_keywords:
- reference types, C++ stack semantics for
ms.assetid: 319a1304-f4a4-4079-8b84-01cec847d531
ms.openlocfilehash: a7f377225e70eff4093d4b9820a3d14644b96f58
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124321"
---
# <a name="c-stack-semantics-for-reference-types"></a>참조 형식에 대한 C++ 스택 의미 체계

Visual Studio 2005 이전에는 참조 형식의 인스턴스는 **`new`** 가비지 수집 된 힙에서 개체를 만든 연산자를 사용 해야만 만들 수 있습니다. 그러나 이제 스택에 네이티브 형식의 인스턴스를 만드는 데 사용 하는 것과 동일한 구문을 사용 하 여 참조 형식의 인스턴스를 만들 수 있습니다. 따라서 참조 형식의 개체를 만들기 위해 [ref new, gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md) 를 사용할 필요가 없습니다. 개체가 범위를 벗어나면 컴파일러가 개체의 소멸자를 호출 합니다.

## <a name="remarks"></a>설명

스택 의미 체계를 사용 하 여 참조 형식의 인스턴스를 만드는 경우 컴파일러는를 사용 하 여 가비지 수집 된 힙에 대 한 인스턴스를 내부적으로 만듭니다 **`gcnew`** .

함수의 시그니처 또는 반환 형식에 값 형식 참조 형식의 인스턴스가 포함 된 경우 함수는 특수 한 처리 (modreq 포함)를 요구 하는 메타 데이터에 표시 됩니다. 이 특수 처리는 현재 Visual C++ 클라이언트만 제공 합니다. 다른 언어에서는 현재 스택 의미 체계를 사용 하 여 생성 된 참조 형식을 사용 하는 함수 또는 데이터 사용을 지원 하지 않습니다.

**`gcnew`** 스택 의미 체계 대신 (동적 할당)를 사용 하는 한 가지 이유는 형식에 소멸자가 없는 경우입니다. 또한 함수를 Visual C++ 이외의 언어에서 사용 하려는 경우 함수 시그니처에서 스택 의미 체계를 사용 하 여 만든 참조 형식을 사용할 수 없습니다.

컴파일러는 참조 형식에 대 한 복사 생성자를 생성 하지 않습니다. 따라서 시그니처에서 값으로 참조 형식을 사용 하는 함수를 정의 하는 경우 참조 형식에 대 한 복사 생성자를 정의 해야 합니다. 참조 형식의 복사 생성자에는 다음과 같은 형식의 시그니처가 있습니다 `R(R%){}` .

컴파일러는 참조 형식에 대 한 기본 할당 연산자를 생성 하지 않습니다. 할당 연산자를 사용 하면 스택 의미 체계를 사용 하 여 개체를 만들고 스택 의미 체계를 사용 하 여 만든 기존 개체를 사용 하 여 개체를 초기화할 수 있습니다. 참조 형식에 대 한 할당 연산자에는 다음과 같은 형식의 시그니처가 있습니다 `void operator=( R% ){}` .

형식의 소멸자가 중요 한 리소스를 해제 하 고 참조 형식에 스택 의미 체계를 사용 하는 경우에는 소멸자를 명시적으로 호출할 필요가 없습니다 **`delete`** . 참조 형식의 소멸자에 대 한 자세한 내용은 [방법: 클래스 및 구조체 정의 및 사용 (c + +/cli)의 소멸자 및 종료자](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)를 참조 하세요.

컴파일러에서 생성 된 할당 연산자는 일반적인 표준 c + + 규칙에 따라 다음과 같이 추가 됩니다.

- 참조 형식에 대 한 핸들 형식의 비정적 데이터 멤버는 단순 복사 됩니다 (형식이 포인터인 비정적 데이터 멤버 처럼 처리 됨).

- 형식이 값 형식인 비정적 데이터 멤버는 모두 단순 복사 됩니다.

- 형식이 참조 형식의 인스턴스인 비정적 데이터 멤버는 참조 형식의 복사 생성자에 대 한 호출을 호출 합니다.

또한 컴파일러는 `%` 스택 의미 체계를 사용 하 여 만든 참조 형식의 인스턴스를 내부 핸들 형식으로 변환 하는 단항 연산자를 제공 합니다.

다음 참조 형식은 스택 의미 체계에서 사용할 수 없습니다.

- [delegate(C++ 구성 요소 확장)](../extensions/delegate-cpp-component-extensions.md)

- [배열](../extensions/arrays-cpp-component-extensions.md)

- <xref:System.String>

## <a name="example"></a>예제

### <a name="description"></a>설명

다음 코드 샘플에서는 스택 의미 체계를 사용 하 여 참조 형식의 인스턴스를 선언 하는 방법, 할당 연산자 및 복사 생성자가 작동 하는 방법, 스택 의미 체계를 사용 하 여 만든 참조 형식으로 추적 참조를 초기화 하는 방법을 보여 줍니다.

### <a name="code"></a>코드

```cpp
// stack_semantics_for_reference_types.cpp
// compile with: /clr
ref class R {
public:
   int i;
   R(){}

   // assignment operator
   void operator=(R% r) {
      i = r.i;
   }

   // copy constructor
   R(R% r) : i(r.i) {}
};

void Test(R r) {}   // requires copy constructor

int main() {
   R r1;
   r1.i = 98;

   R r2(r1);   // requires copy constructor
   System::Console::WriteLine(r1.i);
   System::Console::WriteLine(r2.i);

   // use % unary operator to convert instance using stack semantics
   // to its underlying handle
   R ^ r3 = %r1;
   System::Console::WriteLine(r3->i);

   Test(r1);

   R r4;
   R r5;
   r5.i = 13;
   r4 = r5;   // requires a user-defined assignment operator
   System::Console::WriteLine(r4.i);

   // initialize tracking reference
   R % r6 = r4;
   System::Console::WriteLine(r6.i);
}
```

### <a name="output"></a>출력

```Output
98
98
98
13
13
```

## <a name="see-also"></a>참조

[클래스 및 구조체](../extensions/classes-and-structs-cpp-component-extensions.md)
