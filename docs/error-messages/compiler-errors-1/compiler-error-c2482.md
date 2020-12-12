---
description: '자세한 정보: 컴파일러 오류 C2482'
title: 컴파일러 오류 C2482
ms.date: 09/15/2017
f1_keywords:
- C2482
helpviewer_keywords:
- C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
ms.openlocfilehash: 1ffde4d7ea9f4eccdd643b3ac6efe0545775816a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123931"
---
# <a name="compiler-error-c2482"></a>컴파일러 오류 C2482

>'*identifier*': 관리 되는/WinRT 코드에는 ' thread ' 데이터의 동적 초기화를 사용할 수 없습니다.

## <a name="remarks"></a>설명

관리 되는 또는 WinRT 코드에서 [__declspec (thread)](../../cpp/thread.md) 저장소 클래스 한정자 특성 또는 [thread_local](../../cpp/storage-classes-cpp.md#thread_local) 저장소 클래스 지정자를 사용 하 여 선언 된 변수는 런타임에 평가가 필요한 식으로 초기화할 수 없습니다. 정적 식은 `__declspec(thread)` 이러한 런타임 환경에서 또는 데이터를 초기화 하는 데 필요 **`thread_local`** 합니다.

## <a name="example"></a>예제

다음 샘플에서는 관리 (**/clr**) 및 WinRT (**/zw**) 코드에서 C2482를 생성 합니다.

```cpp
// C2482.cpp
// For managed example, compile with: cl /EHsc /c /clr C2482.cpp
// For WinRT example, compile with: cl /EHsc /c /ZW C2482.cpp
#define Thread __declspec( thread )
Thread int tls_i1 = tls_i1;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i2 = sizeof( tls_i2 );   // Okay in C and C++
```

이 문제를 해결 하려면 상수, 또는 정적 식을 사용 하 여 스레드 로컬 저장소를 초기화 **`constexpr`** 합니다. 스레드별 초기화를 별도로 수행 합니다.
