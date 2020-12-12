---
description: '자세히 알아보기: 메모리 관리: 힙 할당'
title: '메모리 관리: 힙 할당'
ms.date: 11/04/2016
helpviewer_keywords:
- memory [MFC], detecting leaks
- delete operator [MFC], using with debug MFC
- heap allocation [MFC], described
- memory allocation [MFC], heap memory
- memory leaks [MFC], detecting
- new operator [MFC], using with debug MFC
- heap allocation [MFC]
- detecting memory leaks [MFC]
ms.assetid: a5d949c6-1b79-476e-9c66-513a558203d9
ms.openlocfilehash: bb9035d1346f1d3bbff53a03da9b4cf1d946a7ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259658"
---
# <a name="memory-management-heap-allocation"></a>메모리 관리: 힙 할당

힙은 프로그램의 메모리 할당 요구에 예약 되어 있습니다. 프로그램 코드와 스택에서 분리 된 영역입니다. 일반적인 C 프로그램은 함수 **malloc** 및 **free** 를 사용 하 여 힙 메모리를 할당 및 할당 취소 합니다. MFC의 디버그 버전은 c + + 기본 제공 연산자의 수정 된 버전을 제공 하 **`new`** 고 **`delete`** 힙 메모리에서 개체를 할당 및 할당 취소 합니다.

**`new`** Malloc 및 free 대신 및를 사용 하는 경우 **`delete`** 클래스 라이브러리의 메모리 관리 디버깅 향상 기능을 활용할 수 있습니다 .이 기능을 사용 하면 메모리 누수를 탐지 하는 데 유용할 수 있습니다.   릴리스 버전의 MFC를 사용 하 여 프로그램을 빌드할 때 및 연산자의 표준 버전 **`new`** 은 **`delete`** 메모리를 할당 및 할당 취소 하는 효율적인 방법을 제공 합니다 (MFC의 릴리스 버전은 이러한 연산자의 수정 된 버전을 제공 하지 않음).

힙에 할당 된 개체의 총 크기는 시스템의 사용 가능한 가상 메모리에 의해서만 제한 됩니다.

## <a name="see-also"></a>참고 항목

[메모리 관리](memory-management.md)
