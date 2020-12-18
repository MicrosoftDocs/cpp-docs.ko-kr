---
description: '자세한 정보: 0 메모리 할당'
title: 0 메모리 할당
ms.date: 11/04/2016
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
ms.openlocfilehash: 7971d9e097d00607af2acf4590ff3daaf67f7127
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280146"
---
# <a name="allocating-zero-memory"></a>0 메모리 할당

**ANSI 4.10.3** 요청된 크기가 0인 경우 `calloc`, `malloc` 또는 `realloc` 함수의 동작

`calloc`, `malloc` 및 `realloc` 함수는 0을 인수로 수락합니다. 실제 메모리가 할당되지는 않지만 유효한 포인터가 반환되고 이후에 realloc을 사용하여 메모리 블록을 수정할 수 있습니다.

## <a name="see-also"></a>참조

[라이브러리 함수](../c-language/library-functions.md)
