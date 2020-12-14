---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4744'
title: 컴파일러 경고(수준 1) C4744
ms.date: 11/04/2016
f1_keywords:
- C4744
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
ms.openlocfilehash: d7be7c44d0e5abb1d0e3618ffa6ed1778a6410c7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228458"
---
# <a name="compiler-warning-level-1-c4744"></a>컴파일러 경고(수준 1) C4744

' v a l u e '에 ' file1 ' 및 ' file2 ' (' type1 ' 및 ' type2 ')의 형식이 다릅니다.

두 파일에서 참조 또는 정의 된 외부 변수는 해당 파일에서 서로 다른 형식을 갖습니다.  해결 하려면 형식 정의를 동일 하 게 만들거나 파일 중 하나에서 변수 이름을 변경 합니다.

C4744는 파일이./GL로 컴파일되는 경우에만 내보내집니다.  자세한 내용은 [/GL(전체 프로그램 최적화)](../../build/reference/gl-whole-program-optimization.md)을 참조하세요.

> [!NOTE]
> C4744는 c + +에서 변수 이름이 형식 정보로 데코 레이트 되기 때문에 일반적으로 C (c + +가 아닌) 파일에서 발생 합니다.  샘플 (아래)이 c + +로 컴파일되면 링커 오류 LNK2019가 표시 됩니다.

## <a name="examples"></a>예제

이 샘플에는 첫 번째 정의가 포함 되어 있습니다.

```c
// C4744.c
// compile with: /c /GL
int global;
```

다음 샘플에서는 C4744를 생성 합니다.

```c
// C4744b.c
// compile with: C4744.c /GL /W1
// C4744 expected
#include <stdio.h>

extern unsigned global;

main()
{
    printf_s("%d\n", global);
}
```
