---
description: '자세한 정보: 컴파일러 오류 C2212'
title: 컴파일러 오류 C2212
ms.date: 11/04/2016
f1_keywords:
- C2212
helpviewer_keywords:
- C2212
ms.assetid: 3fdab304-272c-4d07-bfd4-fad75170e536
ms.openlocfilehash: 614c93cf2c933cbdf043108c35bc06260a123ce1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245605"
---
# <a name="compiler-error-c2212"></a>컴파일러 오류 C2212

' identifier ': 함수에 대 한 포인터에 __based 사용할 수 없습니다.

함수에 대 한 포인터는 선언할 수 없습니다 **`__based`** . 코드 기반 데이터가 필요한 경우 키워드나 pragma를 사용 합니다 **`__declspec`** `data_seg` .
