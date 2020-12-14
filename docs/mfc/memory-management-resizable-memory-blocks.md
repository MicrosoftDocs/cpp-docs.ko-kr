---
description: '자세히 알아보기: 메모리 관리: 크기 조정 가능한 메모리 블록'
title: '메모리 관리: 크기 조정 가능한 메모리 블록'
ms.date: 11/04/2016
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
ms.openlocfilehash: bcca5617a0d59a7dd5c6a1f9c9f82cb5876f1ef5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248881"
---
# <a name="memory-management-resizable-memory-blocks"></a>메모리 관리: 크기 조정 가능한 메모리 블록

**`new`** **`delete`** [메모리 관리: 예제](memory-management-examples.md)문서에 설명 된 및 연산자는 고정 크기 메모리 블록과 개체를 할당 및 할당 취소 하는 데 유용 합니다. 경우에 따라 응용 프로그램에 크기 조정 가능한 메모리 블록이 필요할 수 있습니다. 표준 C 런타임 라이브러리 함수 [malloc](../c-runtime-library/reference/malloc.md), [realloc](../c-runtime-library/reference/realloc.md)및 free를 사용 하 여 힙에서 크기 조정 [가능한](../c-runtime-library/reference/free.md) 메모리 블록을 관리 해야 합니다.

> [!IMPORTANT]
> **`new`** 및 연산자를 **`delete`** 동일한 메모리 블록에서 크기 조정 가능한 메모리 할당 함수와 혼합 하면 MFC의 디버그 버전에서 메모리가 손상 됩니다. 를 사용 하 여 할당 된 메모리 블록에 **realloc** 를 사용 하면 안 **`new`** 됩니다. 마찬가지로, 연산자를 사용 하 여 메모리 블록을 할당 **`new`** 하 고 **free** 로 삭제 하거나 **`delete`** **malloc** 로 할당 된 메모리 블록에서 연산자를 사용 해야 합니다.

## <a name="see-also"></a>참고 항목

[메모리 관리: 힙 할당](memory-management-heap-allocation.md)
