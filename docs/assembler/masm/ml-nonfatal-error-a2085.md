---
description: '자세한 정보: ML 심각 하지 않은 오류 A2085'
title: ML 심각하지 않은 오류 A2085
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2085
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
ms.openlocfilehash: 3a2cd89b373f761beb3fc0de01a1bea3ec7bf82e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97128547"
---
# <a name="ml-nonfatal-error-a2085"></a>ML 심각하지 않은 오류 A2085

**명령 또는 레지스터가 현재 CPU 모드에서 허용 되지 않습니다.**

현재 프로세서 모드에 대해 유효 하지 않은 명령, 레지스터 또는 키워드를 사용 하려고 한 경우

예를 들어 32 비트 레지스터에는 [386](dot-386.md) 이상이 필요 합니다. CR0 레지스터와 같은 컨트롤 레지스터에는 특권 모드 [. 386p](dot-386p.md) 이상이 필요 합니다. 이 오류는를 필요로 하는 **NEAR32**, **FAR32** 및 **FLAT** 키워드에 대해서도 생성 됩니다. **386** 이상.

## <a name="see-also"></a>참고 항목

[ML 오류 메시지](ml-error-messages.md)
