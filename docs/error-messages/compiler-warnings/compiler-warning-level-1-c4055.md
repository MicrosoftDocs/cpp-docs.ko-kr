---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4055'
title: 컴파일러 경고(수준 1) C4055
ms.date: 11/04/2016
f1_keywords:
- C4055
helpviewer_keywords:
- C4055
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
ms.openlocfilehash: 0bb324b096623c8a5118999706f6f3d32d38e67a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267679"
---
# <a name="compiler-warning-level-1-c4055"></a>컴파일러 경고(수준 1) C4055

> '*conversion*': '*type1*' 데이터 포인터에서 '*type2*' 함수 포인터로

## <a name="remarks"></a>설명

**사용 되지 않음:** 이 경고는 Visual Studio 2017 이상 버전에서 생성 되지 않습니다.

데이터 포인터가 함수 포인터로 잘못 캐스팅된 것 같습니다. /Za가 지정된 경우에는 수준 1이고 /Ze가 지정된 경우에는 수준 4입니다.

## <a name="example"></a>예제

다음 샘플에서는 C4055를 생성합니다.

```C
// C4055.c
// compile with: /Za /W1 /c
typedef int (*PFUNC)();
int *pi;
PFUNC f() {
   return (PFUNC)pi;   // C4055
}
```

/Ze가 지정된 경우에는 이 경고가 수준 4입니다.

```C
// C4055b.c
// compile with: /W4 /c
typedef int (*PFUNC)();
int *pi;
PFUNC f() {
return (PFUNC)pi;   // C4055
}
```
