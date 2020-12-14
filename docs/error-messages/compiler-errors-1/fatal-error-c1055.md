---
description: '자세한 정보: 심각한 오류 C1055'
title: 심각한 오류 C1055
ms.date: 11/04/2016
f1_keywords:
- C1055
helpviewer_keywords:
- C1055
ms.assetid: a9fb9190-d7eb-4d5f-b1a2-a41e584a28c1
ms.openlocfilehash: f85d3bc19b9dcd2ba3f4338e78c55cc7aa549fb6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251650"
---
# <a name="fatal-error-c1055"></a>심각한 오류 C1055

컴파일러 한계: 키가 부족 합니다.

소스 파일에 기호가 너무 많습니다. 컴파일러에서 기호 테이블에 대 한 해시 키가 부족 합니다.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>아래의 해결 방법 따라 수정합니다.

1. 소스 파일을 더 작은 파일로 분할 합니다.

1. 불필요 한 헤더 파일을 제거 합니다.

1. 새 변수를 만드는 대신 임시 및 전역 변수를 다시 사용 합니다.
