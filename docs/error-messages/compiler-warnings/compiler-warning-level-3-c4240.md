---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4240'
title: 컴파일러 경고(수준 3) C4240
ms.date: 11/04/2016
f1_keywords:
- C4240
helpviewer_keywords:
- C4240
ms.assetid: a2657cdb-18e1-493f-882b-4e10c0bca71d
ms.openlocfilehash: 95e704b6ad91ff77c4def0b4fa1fe8fad002e5ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344200"
---
# <a name="compiler-warning-level-3-c4240"></a>컴파일러 경고(수준 3) C4240

비표준 확장이 사용 됨: ' classname '에 대 한 액세스가 이제 ' 액세스 지정자 '로 정의 되었습니다. 이전에 ' access 지정자 '로 정의 되었습니다.

ANSI 호환성 ([/za](../../build/reference/za-ze-disable-language-extensions.md))에서 중첩 된 클래스에 대 한 액세스를 변경할 수 없습니다. 기본 Microsoft 확장 (/Ze)에서이 경고를 사용할 수 있습니다.

## <a name="example"></a>예제

```cpp
// C4240.cpp
// compile with: /W3
class X
{
private:
   class N;
public:
   class N
   {   // C4240
   };
};

int main()
{
}
```
