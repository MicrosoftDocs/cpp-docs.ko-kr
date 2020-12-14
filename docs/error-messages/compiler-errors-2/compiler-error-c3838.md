---
description: '자세한 정보: 컴파일러 오류 C3838'
title: 컴파일러 오류 C3838
ms.date: 11/04/2016
f1_keywords:
- C3838
helpviewer_keywords:
- C3838
ms.assetid: d6f470c2-131a-4a8c-843a-254acd43da83
ms.openlocfilehash: 9ea5f250b7a881ab9be6724f84dac418eefc705e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249149"
---
# <a name="compiler-error-c3838"></a>컴파일러 오류 C3838

' t r u e '에서 명시적으로 상속할 수 없습니다.

지정 된가 `type` 모든 클래스의 기본 클래스로 작동할 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3838를 생성 합니다.

```cpp
// C3838a.cpp
// compile with: /clr /c
public ref class B : public System::Enum {};   // C3838
```
