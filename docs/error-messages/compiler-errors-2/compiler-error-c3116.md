---
description: '자세한 정보: 컴파일러 오류 C3116'
title: 컴파일러 오류 C3116
ms.date: 11/04/2016
f1_keywords:
- C3116
helpviewer_keywords:
- C3116
ms.assetid: 597463e1-a5cc-4ed3-a917-eae9a61d3312
ms.openlocfilehash: ea11d851c4348725c48e408ffdd0ed6de4393e6e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115939"
---
# <a name="compiler-error-c3116"></a>컴파일러 오류 C3116

' storage 지정자 ': 인터페이스 메서드에 대 한 저장소 클래스가 잘못 되었습니다.

**`typedef`**, 또는를 **`register`** **`static`** 인터페이스 메서드의 저장소 클래스로 사용 했습니다. 이러한 저장소 클래스는 인터페이스 멤버에서 허용 되지 않습니다.

다음 샘플에서는 C3116를 생성 합니다.

```cpp
// C3116.cpp
__interface ImyInterface
{
   static void myFunc();   // C3116
};
```
