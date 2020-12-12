---
description: '자세한 정보: 컴파일러 경고 (수준 2) C4275'
title: 컴파일러 경고(수준 2) C4275
ms.date: 02/08/2019
f1_keywords:
- C4275
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
ms.openlocfilehash: 0dd212d7439b73c28a5426574b72ff8150abe93c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173651"
---
# <a name="compiler-warning-level-2-c4275"></a>컴파일러 경고(수준 2) C4275

> dll 인터페이스가 아닌 '*class_1*' 클래스는 '*class_2*' dll 인터페이스 클래스의 기본으로 사용 됩니다.

내보낸 클래스는 내보내지 않은 클래스에서 파생 되었습니다.

[__Declspec (dllexport)](../../cpp/dllexport-dllimport.md)를 사용 하 여 클래스를 내보낼 때 데이터가 손상 될 가능성을 최소화 하려면 다음을 확인 합니다.

- 모든 정적 데이터는 DLL에서 내보낸 함수를 통해 액세스 됩니다.

- 클래스의 인라인 메서드는 정적 데이터를 수정할 수 없습니다.

- 클래스의 인라인 메서드는 CRT 함수 또는 정적 데이터를 사용 하는 다른 라이브러리 함수를 사용 하지 않습니다.

- 인라인 클래스 함수는 CRT 함수 또는 정적 데이터에 액세스 하는 다른 라이브러리 함수를 사용 하지 않습니다.

- 인라인에 관계 없이 클래스의 메서드는 EXE 및 DLL의 인스턴스화에 정적 데이터 차이가 있는 형식을 사용할 수 있습니다.

가상 함수를 사용 하 여 클래스를 정의 하는 DLL을 정의 하 고 해당 형식의 개체를 인스턴스화하고 삭제 하기 위해 호출할 수 있는 함수를 정의 하 여 클래스를 내보내지 않을 수 있습니다.  그런 다음 해당 형식에 대 한 가상 함수를 호출 하면 됩니다.

C4275는 c + + 표준 라이브러리의 형식에서 파생 하 고, 디버그 릴리스 (**/MTd**)를 컴파일하고, 컴파일러 오류 메시지가 참조 하는 경우 Visual C++에서 무시 될 수 있습니다 `_Container_base` .

```cpp
// C4275.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275
```
