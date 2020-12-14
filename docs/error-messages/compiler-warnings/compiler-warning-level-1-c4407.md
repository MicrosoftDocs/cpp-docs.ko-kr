---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4407'
title: 컴파일러 경고(수준 1) C4407
ms.date: 11/04/2016
f1_keywords:
- C4407
helpviewer_keywords:
- C4407
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
ms.openlocfilehash: ea743c5df5f84e99ad89e44a08844b3e59593c1d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311099"
---
# <a name="compiler-warning-level-1-c4407"></a>컴파일러 경고(수준 1) C4407

멤버 표현에 대 한 다른 포인터 간에 캐스트 하는 경우 컴파일러에서 잘못 된 코드를 생성할 수 있습니다.

잘못 된 캐스트가 검색 되었습니다.

C4407는 Visual Studio 2005에서 수행 된 컴파일러 규칙 작업으로 인해 생성 될 수 있습니다. 이제 멤버에 대 한 포인터에 정규화 된 이름과 연산자 주소 (&)가 필요 합니다.

C4407는 다중 상속 포인터를 멤버에 대 한 단일 상속 포인터로 캐스팅 하는 경우에 발생할 수 있습니다. 경우에 따라이 작업을 수행할 수 있지만 단일 상속 포인터 멤버 표시에 충분 한 정보가 포함 되어 있지 않기 때문입니다. **/Vmm** 을 사용 하 여 컴파일하는 것이 도움이 될 수 있습니다. 자세한 내용은/cvers, [/cvers,/Vmv (범용 표시)](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)를 참조 하세요. 기본 클래스를 다시 정렬 해 볼 수도 있습니다. 기본 클래스가 파생 된에서 0이 아닌 오프셋에 있기 때문에 컴파일러는 변환에서 정보의 손실을 감지 합니다.

다음 샘플에서는 C4407를 생성 합니다.

```cpp
// C4407.cpp
// compile with: /W1 /c
struct C1 {};
struct C2 {};
struct C3 : C1, C2 {};

typedef void(C3::*PMF_C3)();
typedef void(C2::*PMF_C2)();

PMF_C2 f1(PMF_C3 pmf) {
   return (PMF_C2)pmf;   // C4407, change type of cast,
   // or reverse base class inheritance of C3 (i.e. : C2, C1)
}
```
