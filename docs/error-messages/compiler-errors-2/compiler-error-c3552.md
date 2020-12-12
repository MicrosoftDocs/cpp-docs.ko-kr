---
description: '자세한 정보: 컴파일러 오류 C3552'
title: 컴파일러 오류 C3552
ms.date: 11/04/2016
f1_keywords:
- C3552
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
ms.openlocfilehash: aca1474f53c8ac1a8257b23d0042550b76b3c0e8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97223258"
---
# <a name="compiler-error-c3552"></a>컴파일러 오류 C3552

'typename': 컴파일하면 지정되는 반환 형식은 'auto'를 포함할 수 없습니다.

**`auto`** 키워드를 함수 반환 형식에 대 한 자리 표시자로 사용 하는 경우 런타임에 지정 된 반환 형식을 제공 해야 합니다. 그러나 다른 키워드를 사용 **`auto`** 하 여 런타임에 지정 된 반환 형식을 지정할 수는 없습니다. 예를 들어 다음 코드 조각은 C3552 오류를 생성합니다.

`auto myFunction->auto; // C3552`
