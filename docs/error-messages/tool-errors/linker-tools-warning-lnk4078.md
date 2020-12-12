---
description: '자세한 정보: 링커 도구 경고 LNK4078'
title: 링커 도구 경고 LNK4078
ms.date: 11/04/2016
f1_keywords:
- LNK4078
helpviewer_keywords:
- LNK4078
ms.assetid: 5a16796d-6caf-42d9-8f65-b042843eafb8
ms.openlocfilehash: 3fd22316d0775561c18fc2662c2f2ca843e64977
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210129"
---
# <a name="linker-tools-warning-lnk4078"></a>링커 도구 경고 LNK4078

여러 특성을 가진 여러 ' section name ' 섹션이 있습니다.

링크가 이름이 같지만 특성이 다른 둘 이상의 섹션을 찾았습니다.

이 경고는 이전 버전의 LINK 또는 LIB에서 만든 가져오기 라이브러리나 내보내기 파일에 의해 발생할 수 있습니다.

파일을 다시 만들고 다시 링크 합니다.

## <a name="example"></a>예제

LNK4078은 주요 변경 내용으로 인해 발생할 수도 있습니다. x 86의 [init_seg](../../preprocessor/init-seg.md) 에 의해 이름이 지정 된 섹션은 읽기/쓰기가 가능 합니다. 이제 읽기 전용입니다.

다음 샘플에서는 LNK4078를 생성 합니다.

```cpp
// LNK4078.cpp
// compile with: /W1
// LNK4078 expected
#include <stdio.h>
#pragma warning(disable : 4075)
typedef void (__cdecl *PF)(void);
int cxpf = 0;   // number of destructors to call
PF pfx[200];   // pointers to destructors.

struct A { A() {} };

int myexit (PF pf) { return 0; }

#pragma section(".mine$a", read, write)
// try the following line instead
// #pragma section(".mine$a", read)
__declspec(allocate(".mine$a")) int ii = 1;

#pragma section(".mine$z", read, write)
// try the following line instead
// #pragma section(".mine$z", read)
__declspec(allocate(".mine$z")) int i = 1;

#pragma data_seg()
#pragma init_seg(".mine$m", myexit)
A bbbb;
A cccc;
int main() {}
```
