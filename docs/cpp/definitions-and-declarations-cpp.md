---
title: 선언 및 정의 (C++)
ms.date: 11/04/2016
ms.assetid: 56b809c0-e602-4f18-9ca5-cd7a8fbaaf30
ms.openlocfilehash: 987e27bdf35eba7d9380fc546c15b93b3179333b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392247"
---
# <a name="definitions-and-declarations-c"></a>선언 및 정의 (C++)

**Microsoft 전용**

DLL 인터페이스 시스템의 일부 프로그램에서 내보내지는 것으로 알려진 모든 항목 (함수 및 데이터)를 가리킵니다. 로 선언 되는 모든 항목, 즉 **dllimport** 하거나 **dllexport**합니다. DLL 인터페이스에 포함 된 모든 선언은 지정 해야 합니다는 **dllimport** 하거나 **dllexport** 특성입니다. 그러나 정의 지정 해야 합니다 **dllexport** 특성입니다. 예를 들어, 다음 함수 정의는 컴파일러 오류를 생성합니다.

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

사용 **dllexport** 는 정의 암시 하는 동안 **dllimport** 가 선언을 암시 합니다. 사용 해야 합니다 **extern** 키워드를 사용 **dllexport** 선언을; 강제 적용 그렇지 않으면 정의가 암시 됩니다. 따라서 다음 예제는 올바릅니다.

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

## <a name="see-also"></a>참고자료

[dllexport, dllimport](../cpp/dllexport-dllimport.md)