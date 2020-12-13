---
description: '다음에 대 한 자세한 정보: 정의 및 선언 (c + +)'
title: 선언 및 정의 (C++)
ms.date: 11/04/2016
ms.assetid: 56b809c0-e602-4f18-9ca5-cd7a8fbaaf30
ms.openlocfilehash: c22274534193011c1c5ec26aedbece339a9302b4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339438"
---
# <a name="definitions-and-declarations-c"></a>선언 및 정의 (C++)

**Microsoft 전용**

DLL 인터페이스는 시스템의 일부 프로그램에서 내보내지는 것으로 알려진 모든 항목 (함수 및 데이터)을 참조 합니다. 즉, 또는로 선언 된 모든 항목입니다 **`dllimport`** **`dllexport`** . DLL 인터페이스에 포함 된 모든 선언은 또는 특성을 지정 해야 합니다 **`dllimport`** **`dllexport`** . 그러나 정의는 특성만 지정 해야 합니다 **`dllexport`** . 예를 들어, 다음 함수 정의는 컴파일러 오류를 생성합니다.

```
__declspec( dllimport ) int func() {   // Error; dllimport
                                       // prohibited on definition.
   return 1;
}
```

다음 코드도 오류를 생성합니다.

```
__declspec( dllimport ) int i = 10;  // Error; this is a definition.
```

그러나 다음은 올바른 구문입니다.

```
__declspec( dllexport ) int i = 10;  // Okay--export definition
```

는를 사용 **`dllexport`** 하 여 정의를 암시 하지만는 **`dllimport`** 선언을 의미 합니다. **`extern`** 키워드를과 함께 사용 하 여 선언을 강제 해야 합니다. **`dllexport`** 그렇지 않으면 정의가 암시 됩니다. 따라서 다음 예제는 올바릅니다.

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllExport int k; // These are both correct and imply a
DllImport int j;        // declaration.
```

다음 예제를 보면 위의 예제를 쉽게 이해할 수 있습니다.

```
static __declspec( dllimport ) int l; // Error; not declared extern.

void func() {
    static __declspec( dllimport ) int s;  // Error; not declared
                                           // extern.
    __declspec( dllimport ) int m;         // Okay; this is a
                                           // declaration.
    __declspec( dllexport ) int n;         // Error; implies external
                                           // definition in local scope.
    extern __declspec( dllimport ) int i;  // Okay; this is a
                                           // declaration.
    extern __declspec( dllexport ) int k;  // Okay; extern implies
                                           // declaration.
    __declspec( dllexport ) int x = 5;     // Error; implies external
                                           // definition in local scope.
}
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[dllexport, dllimport](../cpp/dllexport-dllimport.md)
