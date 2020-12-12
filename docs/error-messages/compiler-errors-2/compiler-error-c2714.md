---
description: '자세한 정보: 컴파일러 오류 C2714'
title: 컴파일러 오류 C2714
ms.date: 07/22/2020
f1_keywords:
- C2714
helpviewer_keywords:
- C2714
ms.assetid: 401a5a42-660c-4bad-9d63-1a2d092bc489
ms.openlocfilehash: 7bea0fc27de49f5767b8b250254f255964423cdc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320833"
---
# <a name="compiler-error-c2714"></a>컴파일러 오류 C2714

> `alignof(void)` 허용 되지 않음

잘못 된 값이 연산자에 전달 되었습니다.

## <a name="remarks"></a>설명

자세한 내용은 [ `alignof` operator](../../cpp/alignof-operator.md) 를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C2714를 생성 합니다.

```cpp
// C2714.cpp
int main() {
   return alignof(void);   // C2714
   return alignof(char);   // OK
}
```
