---
description: '자세한 정보: 컴파일러 오류 C2779'
title: 컴파일러 오류 C2779
ms.date: 11/04/2016
f1_keywords:
- C2779
helpviewer_keywords:
- C2779
ms.assetid: 4a00e492-855a-41f3-8a18-5f60ee20c2f2
ms.openlocfilehash: 88acf83feb7a5aece8f05431eec7c70869cba6a9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298047"
---
# <a name="compiler-error-c2779"></a>컴파일러 오류 C2779

' 선언 ': 속성 메서드는 비정적 데이터 멤버와만 연결 될 수 있습니다.

**`property`** 확장 특성이 정적 데이터 멤버에 잘못 적용 되었습니다.

다음 샘플에서는 C2779를 생성 합니다.

```cpp
// C2779.cpp
struct A {
   static __declspec(property(put=PutProp))
   // try the following line instead
   __declspec(property(put=PutProp))
      int prop;   // C2779
   int PutProp(void);
};
```
