---
title: 컴파일러 오류 C2482
ms.date: 09/15/2017
f1_keywords:
- C2482
helpviewer_keywords:
- C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
ms.openlocfilehash: 5afa81369b2cf329baae02bc1309587015946409
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205155"
---
# <a name="compiler-error-c2482"></a>컴파일러 오류 C2482

>'*identifier*': 관리 되는/WinRT 코드에는 ' thread ' 데이터의 동적 초기화를 사용할 수 없습니다.

## <a name="remarks"></a>주의

관리 되는 또는 WinRT 코드에서 [__declspec (thread)](../../cpp/thread.md) 저장소 클래스 한정자 특성 또는 [thread_local](../../cpp/storage-classes-cpp.md#thread_local) 저장소 클래스 지정자를 사용 하 여 선언 된 변수는 런타임에 평가가 필요한 식으로 초기화할 수 없습니다. 정적 식은 이러한 런타임 환경에서 `__declspec(thread)` 또는 `thread_local` 데이터를 초기화 하는 데 필요 합니다.

## <a name="example"></a>예제

다음 샘플에서는 관리 ( **/clr**) 및 WinRT ( **/zw**) 코드에서 C2482를 생성 합니다.

```cpp
// C2482.cpp
// For managed example, compile with: cl /EHsc /c /clr C2482.cpp
// For WinRT example, compile with: cl /EHsc /c /ZW C2482.cpp
#define Thread __declspec( thread )
Thread int tls_i1 = tls_i1;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i2 = sizeof( tls_i2 );   // Okay in C and C++
```

이 문제를 해결 하려면 상수, **constexpr**또는 정적 식을 사용 하 여 스레드 로컬 저장소를 초기화 합니다. 스레드별 초기화를 별도로 수행 합니다.
