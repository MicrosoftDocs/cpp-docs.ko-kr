---
description: '자세한 정보: 심각한 오류 C1005'
title: 심각한 오류 C1005
ms.date: 11/04/2016
f1_keywords:
- C1005
helpviewer_keywords:
- C1005
ms.assetid: 150daf8e-a38a-4669-9c1a-a05b5a1f65ef
ms.openlocfilehash: c57856a09aa3473c7f5ba3049a2962fb4553e4e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262674"
---
# <a name="fatal-error-c1005"></a>심각한 오류 C1005

버퍼에 비해 문자열이 너무 깁니다.

컴파일러 중간 파일의 문자열에서 버퍼를 오버플로했습니다.

[/Fd](../../build/reference/fd-program-database-file-name.md) 또는 [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) 컴파일러 옵션으로 전달한 매개 변수가 256바이트보다 큰 경우 이 오류가 표시될 수 있습니다.
