---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4092'
title: 컴파일러 경고 (수준 4) C4092
ms.date: 11/04/2016
f1_keywords:
- C4092
helpviewer_keywords:
- C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
ms.openlocfilehash: 70b2d94304863610ede64a30bcb1bb6d407f2e12
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262013"
---
# <a name="compiler-warning-level-4-c4092"></a>컴파일러 경고 (수준 4) C4092

> sizeof는 ' unsigned long '을 반환 합니다.

연산자의 피연산자가 **`sizeof`** 매우 크기 때문에를 **`sizeof`** 반환 했습니다 **`unsigned long`** . 이 경고는 Microsoft 확장 ()에서 발생 합니다 [`/Ze`](../../build/reference/za-ze-disable-language-extensions.md) . ANSI 호환성 ( **`/Za`** )에서 결과가 대신 잘립니다.
