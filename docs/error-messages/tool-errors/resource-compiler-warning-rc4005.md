---
description: '자세한 정보: 리소스 컴파일러 경고 RC4005'
title: 리소스 컴파일러 오류 RC4005
ms.date: 11/04/2016
f1_keywords:
- RC4005
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
ms.openlocfilehash: 138037e48356448550308abee8dc43cd06b9ac06
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97237129"
---
# <a name="resource-compiler-warning-rc4005"></a>리소스 컴파일러 오류 RC4005

' identifier ': 매크로 재정의

식별자는 두 번 정의 됩니다. 컴파일러가 두 번째 매크로 정의를 사용 했습니다.

이 경고는 명령줄에서 지시문을 사용 하 여 코드에 매크로를 정의 하는 경우에 발생할 수 있습니다 `#define` . 포함 파일에서 가져온 매크로로 인해 발생할 수도 있습니다.

이 경고를 제거 하려면 정의 중 하나를 제거 하거나 `#undef` 두 번째 정의 앞에 지시어를 사용 합니다.
