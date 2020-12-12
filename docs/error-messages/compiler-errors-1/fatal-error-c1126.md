---
description: '자세한 정보: 심각한 오류 C1126'
title: 심각한 오류 C1126
ms.date: 11/04/2016
f1_keywords:
- C1126
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
ms.openlocfilehash: d6898b65bafa6862c77b10aa362ffc0a0df6e597
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181009"
---
# <a name="fatal-error-c1126"></a>심각한 오류 C1126

' identifier ': 자동 할당이 크기를 초과 합니다.

함수의 지역 변수에 할당 된 공간 (스왑 가능 함수에 대 한 추가 20 바이트와 같이 컴파일러에서 사용 하는 제한 된 크기의 공간)이 제한을 초과 합니다.

이 오류를 해결 하려면 `malloc` 또는 **`new`** 를 사용 하 여 많은 양의 데이터를 할당 합니다.
