---
title: 컴파일러 오류 C3464
ms.date: 11/04/2016
f1_keywords:
- C3464
helpviewer_keywords:
- C3464
ms.assetid: 0ede05dc-4486-4921-8e8c-78ab5a2e09c5
ms.openlocfilehash: b21810d6df1fbfaf5ea94d9515487b16d00af548
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58775298"
---
# <a name="compiler-error-c3464"></a>컴파일러 오류 C3464

'type' 중첩 형식은 전달할 수 없습니다.

중첩 형식에는 형식 전달이 적용되지 않습니다.

자세한 내용은 [형식 전달 (C + + /cli CLI)](../../extensions/type-forwarding-cpp-cli.md)합니다.

## <a name="example"></a>예제

다음 샘플에서는 구성 요소를 만듭니다.

```
// C3464.cpp
// compile with: /LD /clr
public ref class R {
public:
   ref class N {};
};
```

## <a name="example"></a>예제

다음 샘플에서는 C3464를 생성합니다.

```
// C3464_b.cpp
// compile with: /clr /c
#using "C3464.dll"
[assembly:TypeForwardedTo(R::N::typeid)];   // C3464
[assembly:TypeForwardedTo(R::typeid)];   // OK
```