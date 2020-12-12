---
description: '자세한 정보: 컴파일러 오류 C2097'
title: 컴파일러 오류 C2097
ms.date: 11/04/2016
f1_keywords:
- C2097
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
ms.openlocfilehash: b9aa67f85ce9ba60a693500a2d7e3f69014cbba3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278612"
---
# <a name="compiler-error-c2097"></a>컴파일러 오류 C2097

잘못 된 초기화

### <a name="to-fix-by-checking-the-following-possible-causes"></a>다음과 같은 가능한 원인을 확인하여 수정하려면

1. 비상수 값을 사용 하 여 변수를 초기화 합니다.

1. 긴 주소를 사용 하 여 짧은 주소를 초기화 합니다.

1. **/Za** 를 사용 하 여 컴파일할 때 비상수 식으로 로컬 구조체, 공용 구조체 또는 배열을 초기화 합니다.

1. 쉼표 연산자를 포함 하는 식을 사용 하 여 초기화 합니다.

1. 상수와 기호화 된 식이 아닌 식으로 초기화 합니다.
