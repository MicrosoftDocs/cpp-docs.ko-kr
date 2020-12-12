---
description: '자세한 정보: 컴파일러 오류 C2569'
title: 컴파일러 오류 C2569
ms.date: 11/04/2016
f1_keywords:
- C2569
helpviewer_keywords:
- C2569
ms.assetid: 092bed1e-f631-436c-9586-7750629f6fac
ms.openlocfilehash: bf6b0670cfd90cadc939010a75f9faa9c7c25c30
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209037"
---
# <a name="compiler-error-c2569"></a>컴파일러 오류 C2569

' EnumOrUnion ': 열거형/공용 구조체를 기본 클래스로 사용할 수 없습니다.

지정 된 공용 구조체 또는 열거형에서 형식을 파생 시켜야 하는 경우 공용 구조체 또는 열거형을 클래스나 구조체로 변경 합니다.

다음 샘플에서는 C2569를 생성 합니다.

```cpp
// C2569.cpp
// compile with: /c
union ubase {};
class cHasPubUBase : public ubase {};   // C2569
// OK
struct sbase {};
class cHasPubUBase : public sbase {};
```
