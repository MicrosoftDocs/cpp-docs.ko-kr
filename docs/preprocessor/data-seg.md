---
title: data_seg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- data_seg_CPP
- vc-pragma.data_seg
dev_langs:
- C++
helpviewer_keywords:
- data_seg pragma
- pragmas, data_seg
ms.assetid: 65c66466-4c98-494f-93af-106beb4caf78
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b1be97919f0f5b55d6e63eca8e59eb15e8ef9dff
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2018
ms.locfileid: "42541776"
---
# <a name="dataseg"></a>data_seg
초기화된 변수가 .obj 파일에 저장되는 데이터 세그먼트를 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
#pragma data_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>설명 

의미 *세그먼트* 하 고 *섹션* 이 항목에서 서로 바꿀 수 있습니다.  
  
OBJ 파일을 사용 하 여 볼 수 있습니다 합니다 [dumpbin](../build/reference/dumpbin-command-line.md) 응용 프로그램입니다. 초기화된 변수에 대한 .obj 파일의 기본 세그먼트는 .data입니다. 초기화되지 않은 변수는 0으로 초기화된 것으로 간주되고 .bss에 저장됩니다.  
  
**data_seg** 매개 변수 없이 세그먼트를.data로 다시 설정 합니다.  
  
*푸시* (선택 사항)  
내부 컴파일러 스택에 기록합니다. A *푸시* 있을 수 있습니다는 *식별자* 하 고 *세그먼트 이름이*합니다.  
  
*pop* (선택 사항)  
내부 컴파일러 스택 맨 위에서 기록을 제거합니다.  
  
*식별자* (선택 사항)  
와 함께 사용할 때 *푸시*, 내부 컴파일러 스택의 레코드에 이름을 할당 합니다. 와 함께 사용할 때 *pop*, 될 때까지 내부 스택에서 기록을 팝 *식별자* 가 제거 *식별자* 없는 내부 스택에서 아무 것도 팝 합니다.  
  
*식별자* 여러 레코드는 단일으로 팝 될 수 있습니다 *pop* 명령입니다.  
  
*"segment-name"*(optional)  
세그먼트의 이름입니다. 와 함께 사용할 경우 *pop*, 스택이 팝 되 고 *세그먼트 이름이* 활성 세그먼트 이름이 됩니다.  
  
*"세그먼트-클래스"* (선택 사항)  
C++ 2.0 이전 버전과의 호환성을 위해 포함됩니다. 무시됩니다.  
  
## <a name="example"></a>예  
  
```cpp  
// pragma_directive_data_seg.cpp  
int h = 1;                     // stored in .data  
int i = 0;                     // stored in .bss  
#pragma data_seg(".my_data1")  
int j = 1;                     // stored in "my_data1"  
  
#pragma data_seg(push, stack1, ".my_data2")     
int l = 2;                     // stored in "my_data2"  
  
#pragma data_seg(pop, stack1)   // pop stack1 off the stack  
int m = 3;                     // stored in "stack_data1"  
  
int main() {  
}  
```  
  
사용 하 여 할당 된 데이터 **data_seg** 해당 위치에 대 한 정보를 유지 하지 않습니다.  
  
참조 [/section](../build/reference/section-specify-section-attributes.md) 섹션을 만들 때 사용 하지 않아야 하는 이름의 목록에 대 한 합니다.  
  
상수 변수 섹션을 지정할 수도 있습니다 ([const_seg](../preprocessor/const-seg.md)), 초기화 되지 않은 데이터 ([bss_seg](../preprocessor/bss-seg.md)), 및 함수 ([code_seg](../preprocessor/code-seg.md)).  
  
## <a name="see-also"></a>참고 항목  
 
[Pragma 지시문 및 __Pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)