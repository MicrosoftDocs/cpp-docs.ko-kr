---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4742'
title: 컴파일러 경고(수준 1) C4742
ms.date: 07/22/2020
f1_keywords:
- C4742
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
ms.openlocfilehash: 009c8b894b9c53d3a0c802dbb0f5786fc9934b57
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228523"
---
# <a name="compiler-warning-level-1-c4742"></a>컴파일러 경고(수준 1) C4742

> '*n a m* e '의 맞춤이 *' file1*' 및 '*file2*'의 차이가 있습니다. *number1* 및 *number2*

두 파일에서 참조 또는 정의 된 외부 변수는 해당 파일에서 서로 다른 맞춤을 갖습니다.

## <a name="remarks"></a>설명

이 경고는 컴파일러에서 **`alignof`** *file1* 의 변수가 file2의 변수와 다른 것을 발견할 때 내보내집니다 **`alignof`** .  다른 파일에서 변수를 선언 하거나 다른 파일에서 일치 하지 않는 형식을 사용 하 여 호환 되지 않는 형식을 사용 하는 경우이 문제가 발생할 수 있습니다 `#pragma pack` .

이 경고를 해결 하려면 동일한 유형 정의를 사용 하거나 변수에 다른 이름을 사용 합니다.

자세한 내용은 [`pack`](../../preprocessor/pack.md) 및 [ `alignof` 연산자](../../cpp/alignof-operator.md)를 참조 하세요.

## <a name="example"></a>예제

이 파일은 형식을 정의 하는 첫 번째 파일입니다.

```c
// C4742a.c
// compile with: /c
struct X {
   char x, y, z, w;
} global;
```

다음 샘플에서는 C4742를 생성 합니다.

```c
// C4742b.c
// compile with: C4742a.c /W1 /GL
// C4742 expected
extern struct X {
   int a;
} global;

int main() {
   global.a = 0;
}
```
