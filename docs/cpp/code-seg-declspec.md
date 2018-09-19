---
title: code_seg (__declspec) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- code_seg_cpp
dev_langs:
- C++
helpviewer_keywords:
- code_seg __declspec keyword
ms.assetid: ad3c1105-15d3-4e08-b7b9-e4bd9d7b6aa0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6dcf387283aa0d4cdb282760c4ee170a0205172d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068821"
---
# <a name="codeseg-declspec"></a>code_seg (__declspec)

**Microsoft 전용**

합니다 **code_seg** 선언 특성 함수 또는 클래스 멤버 함수의 개체 코드가 저장 될.obj 파일의 실행 텍스트 세그먼트의 이름을 지정 합니다.

## <a name="syntax"></a>구문

```
__declspec(code_seg("segname")) declarator
```

## <a name="remarks"></a>설명

`__declspec(code_seg(...))` 특성을 사용하면 메모리에 개별적으로 페이징 또는 잠글 수 있는 별도의 명명된 세그먼트에 코드를 배치할 수 있습니다. 이 특성을 사용하여 인스턴스화한 템플릿과 컴파일러에서 생성된 코드의 배치를 제어할 수 있습니다.

A *세그먼트* 단위로 메모리에 로드 된.obj 파일에서 데이터의 명명 된 블록입니다. A *텍스트 세그먼트* 실행 코드가 포함 된 세그먼트입니다. 용어 *섹션* 세그먼트 함께 서로 교환해 서 주로 사용 됩니다.

`declarator`가 지정될 때 생성되는 개체 코드는 좁은 문자열 리터럴인 `segname`에서 지정한 텍스트 세그먼트에 배치됩니다. 이름을 `segname` 지정할 필요가 없습니다를 [섹션](../preprocessor/section.md) pragma 선언에서 사용할 수 있습니다. 기본적으로 `code_seg`가 지정되지 않으면 개체 코드가 .text라는 세그먼트에 배치됩니다. A **code_seg** 기존 특성 재정의 [#pragma code_seg](../preprocessor/code-seg.md) 지시문입니다. A **code_seg** 멤버 함수에 적용 된 특성 재정의 **code_seg** 특성은 바깥쪽 클래스에 적용 합니다.

엔터티의 경우는 **code_seg** 특성, 모든 선언 및 정의 동일한 엔터티의 동일한 있어야 **code_seg** 특성입니다. 기본 클래스에는 **code_seg** 특성을 파생 클래스에 동일한 특성이 있어야 합니다.

경우는 **code_seg** 특성 네임 스페이스 범위 함수 또는 멤버 함수에 적용 되 면 해당 함수의 개체 코드가 지정된 된 텍스트 세그먼트에 배치 됩니다. 이 특성이 클래스에 적용되면 컴파일러 생성 특수 멤버 함수를 포함하는 클래스와 중첩된 클래스의 모든 멤버 함수가 지정된 세그먼트에 배치됩니다. 로컬로 클래스를 정의-멤버 함수 본문에 정의 된 클래스 예를 들어-상속 하지 않습니다 합니다 **code_seg** 바깥쪽 범위의 특성입니다.

경우는 **code_seg** 특성 템플릿 클래스 또는 템플릿 함수에 적용 되 면 템플릿의 모든 암시적 특수화가 지정된 된 세그먼트에 배치 됩니다. 명시적 또는 부분 특수화를 상속 하지 않는 합니다 **code_seg** 기본 템플릿에서 특성입니다. 동일 하거나 다른 지정할 수 있습니다 **code_seg** 특수화에는 특성입니다. A **code_seg** 특성은 명시적 템플릿 인스턴스화에 적용할 수 없습니다.

기본적으로 특수 멤버 함수 등 컴파일러에서 생성된 코드는 .text 세그먼트에 배치됩니다. `#pragma code_seg` 지시문은 이 기본값을 재정의하지 않습니다. 사용 된 **code_seg** 클래스, 클래스 템플릿 또는 함수 템플릿은 컴파일러에서 생성 된 코드는 배치는 컨트롤에 대 한 특성입니다.

람다 식은 상속 **code_seg** 는 바깥쪽 범위에서 특성입니다. 람다에 대 한 세그먼트를 지정 하려면 적용을 **code_seg** 특성 매개 변수 선언 절 뒤 및 하기 전에 변경할 수 또는 예외 사양, 모든 후행 반환 형식 사양 및 람다 본문입니다. 자세한 내용은 [람다 식 구문](../cpp/lambda-expression-syntax.md)합니다. 이 예제에서는 PagedMem이라는 세그먼트에 람다를 정의합니다.

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

여러 세그먼트에 특정 멤버 함수, 특히 가상 멤버 함수를 배치할 때 주의해야 합니다. 기본 클래스 메서드가 페이징되지 않은 세그먼트에 상주할 때 페이징된 세그먼트에 상주하는 파생된 클래스에 가상 함수를 정의하는 경우 다른 기본 클래스 메서드 또는 사용자 코드는 가상 메서드를 호출해도 페이지 오류가 트리거되지 않는다고 가정할 수 있습니다.

## <a name="example"></a>예제

이 예제에서는 어떻게를 **code_seg** 특성 컨트롤 세그먼트 배치 하면 암시적 및 명시적 템플릿 특수화는:

```cpp
// code_seg.cpp
// Compile: cl /EHsc /W4 code_seg.cpp

// Base template places object code in Segment_1 segment
template<class T>
class __declspec(code_seg("Segment_1")) Example
{
public:
   virtual void VirtualMemberFunction(T /*arg*/) {}
};

// bool specialization places code in default .text segment
template<>
class Example<bool>
{
public:
   virtual void VirtualMemberFunction(bool /*arg*/) {}
};

// int specialization places code in Segment_2 segment
template<>
class __declspec(code_seg("Segment_2")) Example<int>
{
public:
   virtual void VirtualMemberFunction(int /*arg*/) {}
};

// Compiler warns and ignores __declspec(code_seg("Segment_3"))
// in this explicit specialization
__declspec(code_seg("Segment_3")) Example<short>; // C4071

int main()
{
   // implicit double specialization uses base template's
   // __declspec(code_seg("Segment_1")) to place object code
   Example<double> doubleExample{};
   doubleExample.VirtualMemberFunction(3.14L);

   // bool specialization places object code in default .text segment
   Example<bool> boolExample{};
   boolExample.VirtualMemberFunction(true);

   // int specialization uses __declspec(code_seg("Segment_2"))
   // to place object code
   Example<int> intExample{};
   intExample.VirtualMemberFunction(42);
}
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참고자료

[__declspec](../cpp/declspec.md)<br/>
[키워드](../cpp/keywords-cpp.md)