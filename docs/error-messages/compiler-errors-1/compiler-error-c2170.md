---
description: '자세한 정보: 컴파일러 오류 C2170'
title: 컴파일러 오류 C2170
ms.date: 11/04/2016
f1_keywords:
- C2170
helpviewer_keywords:
- C2170
ms.assetid: d5c663f0-2459-4e11-a8bf-a52b62f3c71d
ms.openlocfilehash: 2f6093221d214aa12f6b90f40dde14518e44e08e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322260"
---
# <a name="compiler-error-c2170"></a>컴파일러 오류 C2170

' identifier ': 함수로 선언 되지 않았으므로 내장 함수 일 수 없습니다.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>다음과 같은 가능한 원인을 확인하여 수정하려면

1. Pragma `intrinsic` 는 함수 이외의 항목에 사용 됩니다.

1. Pragma `intrinsic` 는 내장 형식이 없는 함수에 사용 됩니다.
