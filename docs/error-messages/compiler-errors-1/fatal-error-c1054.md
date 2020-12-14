---
description: '자세한 정보: 심각한 오류 C1054'
title: 심각한 오류 C1054
ms.date: 11/04/2016
f1_keywords:
- C1054
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
ms.openlocfilehash: 1bfe8718fcb0d3edb172f0f5a89bb2f479e56137
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251663"
---
# <a name="fatal-error-c1054"></a>심각한 오류 C1054

컴파일러 한계: 이니셜라이저가 너무 많이 중첩 되었습니다.

코드는 초기화 되는 형식의 조합에 따라 이니셜라이저의 중첩 한도 (10-15 수준)를 초과 합니다.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>아래의 해결 방법 따라 수정합니다.

1. 초기화 되는 데이터 형식을 단순화 하 여 중첩을 줄입니다.

1. 선언 후 별도의 문에서 변수를 초기화 합니다.
