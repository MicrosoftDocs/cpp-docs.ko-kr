---
description: '자세한 정보: 컴파일러 오류 C2818'
title: 컴파일러 오류 C2818
ms.date: 11/04/2016
f1_keywords:
- C2818
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
ms.openlocfilehash: e258387af290a8070c1c66a56a7523b46482cf99
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194789"
---
# <a name="compiler-error-c2818"></a>컴파일러 오류 C2818

오버 로드 된 ' operator-> '의 응용 프로그램이 ' type ' 형식을 통해 재귀적으로 적용 됩니다.

클래스 멤버 액세스 연산자를 재정의 하는 경우 재귀 **`return`** 문이 포함 됩니다. `->`재귀를 사용 하 여 연산자를 다시 정의 하려면 재귀 루틴을 operator override 함수에서 호출 되는 별도의 함수로 이동 해야 합니다.
