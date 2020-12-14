---
description: '자세히 알아보기: 메모리 관리'
title: 메모리 관리
ms.date: 11/04/2016
helpviewer_keywords:
- memory [MFC]
- MFC, memory management
- memory allocation [MFC]
- memory [MFC], managing
- memory allocation [MFC], MFC
ms.assetid: 934ac81b-d630-4232-88e5-ea74f7187987
ms.openlocfilehash: 4e274820ce82cf8b338c6a62349440e944f21f7a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253379"
---
# <a name="memory-management"></a>메모리 관리

이 문서 그룹에서는 메모리 관리와 관련 된 MFC (MFC 라이브러리)의 범용 서비스를 활용 하는 방법을 설명 합니다. 메모리 할당은 프레임 할당과 힙 할당 이라는 두 가지 주요 범주로 나눌 수 있습니다.

두 할당 방법의 주요 차이점은 프레임 할당을 사용 하는 경우 일반적으로 실제 메모리 블록 자체를 사용 하는 것 이지만 힙 할당을 사용 하는 경우 항상 메모리 블록에 대 한 포인터를 제공 한다는 것입니다. 두 스키마의 또 다른 주요 차이점은 프레임 개체가 자동으로 삭제 되는 반면, 힙 개체는 프로그래머가 명시적으로 삭제 해야 한다는 것입니다.

Windows 용 프로그램의 메모리 관리에 대 한 비 MFC 정보는 Windows SDK의 [메모리 관리](/windows/win32/memory/memory-management) 를 참조 하세요.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [프레임 할당](memory-management-frame-allocation.md)

- [힙 할당](memory-management-heap-allocation.md)

- [배열에 대 한 메모리 할당](memory-management-examples.md)

- [힙의 배열에 대 한 메모리 할당을 취소 합니다.](memory-management-examples.md)

- [데이터 구조에 대 한 메모리 할당](memory-management-examples.md)

- [개체에 대 한 메모리 할당](memory-management-examples.md)

- [크기 조정 가능한 메모리 블록](memory-management-resizable-memory-blocks.md)

## <a name="see-also"></a>참고 항목

[개념](mfc-concepts.md)<br/>
[일반 MFC 항목](general-mfc-topics.md)
