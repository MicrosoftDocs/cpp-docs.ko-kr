---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4251'
title: 컴파일러 경고(수준 1) C4251
ms.date: 04/21/2020
f1_keywords:
- C4251
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
ms.openlocfilehash: 4d08462442fd64ebef85573f5d538d6a884c8131
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266236"
---
# <a name="compiler-warning-level-1-c4251"></a>컴파일러 경고(수준 1) C4251

> '*type*': '*type1*' 클래스는 '*type2*' 클래스의 클라이언트에서 사용할 dll 인터페이스를 포함 해야 합니다.

## <a name="remarks"></a>설명

[__Declspec (dllexport)](../../cpp/dllexport-dllimport.md)로 선언 된 클래스를 내보낼 때 데이터 손상 가능성을 최소화 하려면 다음을 확인 합니다.

- 모든 정적 데이터는 DLL에서 내보낸 함수를 통해 액세스 됩니다.

- 클래스의 인라인 메서드는 정적 데이터를 수정할 수 없습니다.

- 클래스의 인라인 메서드는 CRT 함수 또는 정적 데이터를 사용 하는 다른 라이브러리 함수를 사용 하지 않습니다. 자세한 내용은 [DLL 경계를 넘어 CRT 개체를 전달할 때 발생할](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)수 있는 오류를 참조 하세요.

- 클래스의 메서드 (인라인 여부에 관계 없이)는 EXE 및 DLL의 인스턴스화에 정적 데이터 차이가 있는 형식을 사용할 수 있습니다.

DLL에서 클래스를 내보낼 때 문제를 방지할 수 있습니다. 가상 함수를 갖도록 클래스를 정의 하 고 해당 형식의 개체를 인스턴스화하고 삭제 하는 함수를 정의 합니다. 그런 다음 해당 형식에 대 한 가상 함수를 호출 하면 됩니다.

C4251는 클래스가 c + + 표준 라이브러리의 형식에서 파생 되 고, 디버그 릴리스 (**/MTd**)를 컴파일하고, 컴파일러 오류 메시지가 참조 하는 경우에는 무시할 수 있습니다 `_Container_base` .

## <a name="example"></a>예제

이 샘플에서는에서 파생 된 특수 클래스를 내보냅니다 `VecWrapper` `std::vector` .

```cpp
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllexport) VecWrapper : vector<Node *> {};   // C4251
```
