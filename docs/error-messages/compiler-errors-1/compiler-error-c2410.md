---
description: '자세한 정보: 컴파일러 오류 C2410'
title: 컴파일러 오류 C2410
ms.date: 11/04/2016
f1_keywords:
- C2410
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
ms.openlocfilehash: 921ccdcff64bca28c3a771dd0931b8b7abf83e52
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341895"
---
# <a name="compiler-error-c2410"></a>컴파일러 오류 C2410

' identifier ': ' context '의 멤버 이름이 모호 합니다.

식별자가이 컨텍스트에서 둘 이상의 구조체 또는 공용 구조체의 멤버입니다.

오류를 발생 시킨 피연산자에서 구조체 또는 공용 구조체 지정자를 사용 합니다. 구조체 또는 공용 구조체 지정자는 형식의 식별자 또는 **`struct`** **`union`** **`typedef`** 참조 되는 구조체 또는 공용 구조체와 동일한 형식의 이름 또는 변수입니다. 피연산자를 사용 하려면 지정자는 첫 번째 멤버 선택 연산자 (.)의 왼쪽 피연산자 여야 합니다.
