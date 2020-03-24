---
title: selectany
ms.date: 11/04/2016
f1_keywords:
- selectany_cpp
helpviewer_keywords:
- __declspec keyword [C++], selectany
- selectany __declspec keyword
ms.assetid: 9c353017-5a42-4f50-b741-bd13da1ce84d
ms.openlocfilehash: 38346e41c1e943e9bfda70668a163c630a0b9599
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178875"
---
# <a name="selectany"></a>selectany

**Microsoft 전용**

선언된 전역 데이터 항목(변수 또는 개체)이 pick-any COMDAT(패키지된 함수)임을 컴파일러에 알립니다.

## <a name="syntax"></a>구문

```
__declspec( selectany ) declarator
```

## <a name="remarks"></a>주의

링크 타임에 COMDAT의 정의가 여러 개 표시되면 링커가 그 중 하나를 선택하고 나머지는 무시합니다. 링커 옵션 [/opt: REF](../build/reference/opt-optimizations.md) (최적화)를 선택 하면 COMDAT 제거는 링커 출력에서 참조 되지 않은 모든 데이터 항목을 제거 하기 위해 발생 합니다.

선언에서 전역 함수 또는 정적 메서드에 의한 생성자 및 할당은 참조를 만들지 않으며 /OPT:REF 제거를 막지 않습니다. 데이터에 대한 다른 참조가 없을 경우 그러한 코드로 인해 의도하지 않은 결과가 발생해서는 안 됩니다.

동적으로 초기화 되는 전역 개체의 경우 **selectany** 는 참조 되지 않은 개체의 초기화 코드도 삭제 합니다.

보통 EXE 또는 DLL 프로젝트에서 한 번만 전역 데이터 항목을 초기화할 수 있습니다. **selectany** 는 둘 이상의 소스 파일에 동일한 헤더가 나타날 때 헤더로 정의 된 글로벌 데이터를 초기화 하는 데 사용할 수 있습니다. **selectany** 는 C와 C++ 컴파일러 모두에서 사용할 수 있습니다.

> [!NOTE]
>  **selectany** 는 외부에 표시 되는 글로벌 데이터 항목의 실제 초기화에만 적용할 수 있습니다.

## <a name="example"></a>예제

이 코드는 **selectany** 특성을 사용 하는 방법을 보여 줍니다.

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

## <a name="example"></a>예제

이 코드는 [/opt: ICF](../build/reference/opt-optimizations.md) 링커 옵션을 사용 하는 경우 **selectany** 특성을 사용 하 여 데이터 COMDAT 정리를 확인 하는 방법을 보여 줍니다. 데이터를 **selectany** 로 표시 하 고 **const** (readonly) 섹션에 배치 해야 합니다. 읽기 전용 섹션을 명시적으로 지정해야 합니다.

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

## <a name="see-also"></a>참고 항목

[__declspec](../cpp/declspec.md)<br/>
[키워드](../cpp/keywords-cpp.md)
