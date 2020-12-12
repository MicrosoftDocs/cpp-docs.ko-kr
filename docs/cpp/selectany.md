---
description: 다음에 대해 자세히 알아보세요. `selectany`
title: selectany
ms.date: 11/04/2016
f1_keywords:
- selectany_cpp
helpviewer_keywords:
- __declspec keyword [C++], selectany
- selectany __declspec keyword
ms.assetid: 9c353017-5a42-4f50-b741-bd13da1ce84d
ms.openlocfilehash: e17ad5787211aacbb206d5e68ba355047711b96a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319341"
---
# `selectany`

**Microsoft 전용**

선언된 전역 데이터 항목(변수 또는 개체)이 pick-any COMDAT(패키지된 함수)임을 컴파일러에 알립니다.

## <a name="syntax"></a>Syntax

> **`__declspec( selectany )`***선언 자*

## <a name="remarks"></a>설명

링크 타임에 COMDAT의 정의가 여러 개 표시되면 링커가 그 중 하나를 선택하고 나머지는 무시합니다. 링커 옵션 [`/OPT:REF`](../build/reference/opt-optimizations.md) (최적화)을 선택 하면 COMDAT 제거는 링커 출력에서 참조 되지 않은 모든 데이터 항목을 제거 하기 위해 발생 합니다.

선언에서 전역 함수 또는 정적 메서드에 의한 생성자 및 할당은 참조를 만들지 않으며 /OPT:REF 제거를 막지 않습니다. 데이터에 대한 다른 참조가 없을 경우 그러한 코드로 인해 의도하지 않은 결과가 발생해서는 안 됩니다.

동적으로 초기화 되는 전역 개체의 경우 **`selectany`** 참조 되지 않은 개체의 초기화 코드도 삭제 합니다.

보통 EXE 또는 DLL 프로젝트에서 한 번만 전역 데이터 항목을 초기화할 수 있습니다. **`selectany`** 두 개 이상의 소스 파일에 동일한 헤더가 나타날 때 헤더에 정의 된 전역 데이터를 초기화 하는 데 사용할 수 있습니다. **`selectany`** 는 C 및 c + + 컴파일러에서 사용할 수 있습니다.

> [!NOTE]
> **`selectany`** 외부에 표시 되는 글로벌 데이터 항목의 실제 초기화에만 적용할 수 있습니다.

## <a name="example-selectany-attribute"></a>예: `selectany` 특성

이 코드에서는 특성을 사용 하는 방법을 보여 줍니다 **`selectany`** .

```cpp
//Correct - x1 is initialized and externally visible
__declspec(selectany) int x1=1;

//Incorrect - const is by default static in C++, so
//x2 is not visible externally (This is OK in C, since
//const is not by default static in C)
const __declspec(selectany) int x2 =2;

//Correct - x3 is extern const, so externally visible
extern const __declspec(selectany) int x3=3;

//Correct - x4 is extern const, so it is externally visible
extern const int x4;
const __declspec(selectany) int x4=4;

//Incorrect - __declspec(selectany) is applied to the uninitialized
//declaration of x5
extern __declspec(selectany) int x5;

// OK: dynamic initialization of global object
class X {
public:
X(int i){i++;};
int i;
};

__declspec(selectany) X x(1);
```

## <a name="example-use-selectany-attribute-to-ensure-data-comdat-folding"></a>예: `selectany` 특성을 사용 하 여 데이터 COMDAT 정리 확인

이 코드에서는 **`selectany`** 링커 옵션도 사용할 때 특성을 사용 하 여 데이터 COMDAT 정리를 확인 하는 방법을 보여 줍니다 [`/OPT:ICF`](../build/reference/opt-optimizations.md) . 데이터는로 표시 되 **`selectany`** 고 **`const`** (읽기 전용) 섹션에 배치 되어야 합니다. 읽기 전용 섹션을 명시적으로 지정해야 합니다.

```cpp
// selectany2.cpp
// in the following lines, const marks the variables as read only
__declspec(selectany) extern const int ix = 5;
__declspec(selectany) extern const int jx = 5;
int main() {
   int ij;
   ij = ix + jx;
}
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[`__declspec`](../cpp/declspec.md)<br/>
[키워드](../cpp/keywords-cpp.md)
