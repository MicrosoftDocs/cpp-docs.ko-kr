---
description: '자세한 정보: 컴파일러 오류 C2439'
title: 컴파일러 오류 C2439
ms.date: 11/04/2016
f1_keywords:
- C2439
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
ms.openlocfilehash: 6493fb634581646c20a8d856658fe728ae27364c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189810"
---
# <a name="compiler-error-c2439"></a>컴파일러 오류 C2439

' identifier ': 멤버를 초기화할 수 없습니다.

클래스, 구조체 또는 공용 구조체 멤버를 초기화할 수 없습니다.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>다음과 같은 가능한 원인을 확인하여 수정하려면

1. 간접 기본 클래스 또는 구조체를 초기화 하는 중입니다.

1. 클래스 또는 구조체의 상속 된 멤버를 초기화 하려고 합니다. 상속 된 멤버는 클래스 또는 구조체의 생성자에 의해 초기화 되어야 합니다.
