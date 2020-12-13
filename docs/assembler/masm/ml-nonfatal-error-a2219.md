---
description: '자세한 정보: ML 심각 하지 않은 오류 A2219'
title: ML 심각하지 않은 오류 A2219
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2219
helpviewer_keywords:
- A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
ms.openlocfilehash: 3b9fd2f397f702a32784cd696bcbc3a72f35cf95
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97128312"
---
# <a name="ml-nonfatal-error-a2219"></a>ML 심각하지 않은 오류 A2219

> 해제 코드의 오프셋에 대 한 맞춤이 잘못 되었습니다.

## <a name="remarks"></a>설명

[ &period; Allocstack](dot-allocstack.md) 및 [ &period; savereg](dot-savereg.md) 의 피연산자는 8의 배수 여야 합니다.  [ &period; SAVEXMM128](dot-savexmm128.md) 및 [ &period; setframe](dot-setframe.md) 의 피연산자는 16의 배수 여야 합니다.

## <a name="see-also"></a>참고 항목

[ML 오류 메시지](ml-error-messages.md)
