---
description: '자세히 알아보기: 메모리 관리: 프레임 할당'
title: '메모리 관리: 프레임 할당'
ms.date: 11/04/2016
helpviewer_keywords:
- memory leaks [MFC], frame allocation
- memory [MFC], detecting leaks
- memory [MFC], reclaiming
- memory allocation [MFC], frames
- frame variables [MFC], automatic deletion of
- scope [MFC], frame variables
- heap allocation [MFC], vs. frame allocation
- variables [MFC], frame variables
- memory leaks [MFC], detecting
- memory, releasing [MFC]
- stack frames [MFC]
- memory leaks [MFC], allocating objects on the frame
- detecting memory leaks [MFC]
- frame allocation [MFC]
- frame variables [MFC]
ms.assetid: 945a211a-6f4f-4679-bb6a-b0f2a0d4a6c1
ms.openlocfilehash: 1763d332275f17ee082b891830641ebc61cad054
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193437"
---
# <a name="memory-management-frame-allocation"></a>메모리 관리: 프레임 할당

프레임 할당은 함수가 호출 될 때마다 설정 된 "스택 프레임"에서 해당 이름을 사용 합니다. 스택 프레임은 함수에 대 한 인수를 임시로 포함 하는 메모리 영역 및 함수에 로컬로 정의 된 변수입니다. 프레임 변수는 컴파일러에서 자동으로 공간을 할당 하기 때문에 "자동" 변수 라고도 합니다.

프레임 할당에는 두 가지 주요 특성이 있습니다. 첫째, 지역 변수를 정의 하는 경우 전체 변수를 저장할 수 있는 충분 한 공간이 스택 프레임에 할당 됩니다 .이는 배열이 크거나 데이터 구조 이더라도 충분 합니다. 둘째, 프레임 변수가 범위를 벗어날 때 자동으로 삭제 됩니다.

[!code-cpp[NVC_MFC_Utilities#10](codesnippet/cpp/memory-management-frame-allocation_1.cpp)]

로컬 함수 변수의 경우 함수가 종료 될 때이 범위 전환이 발생 하지만 중첩 된 중괄호가 사용 되는 경우 프레임 변수의 범위는 함수 보다 작을 수 있습니다. 프레임 변수를 자동으로 삭제 하는 것은 매우 중요 합니다. 단순 기본 형식 (예: **`int`** 또는 **바이트**), 배열 또는 데이터 구조에서 자동 삭제는 단순히 변수에 사용 되는 메모리를 회수 합니다. 변수는 범위를 벗어났기 때문에 액세스할 수 없습니다. 그러나 c + + 개체의 경우에는 자동 삭제 프로세스가 다소 복잡 합니다.

개체가 프레임 변수로 정의 되 면 해당 생성자가 정의가 발견 된 지점에서 자동으로 호출 됩니다. 개체가 범위를 벗어나면 해당 소멸자는 개체에 대 한 메모리가 회수 되기 전에 자동으로 호출 됩니다. 이러한 자동 생성 및 소멸은 매우 편리 하지만 특히 소멸자의 자동 호출에 대해 알고 있어야 합니다.

프레임에서 개체를 할당 하는 경우의 주요 장점은 자동으로 삭제 된다는 것입니다. 프레임에 개체를 할당 하면 메모리 누수를 유발 하는 잊어버린 개체에 대해 걱정할 필요가 없습니다. 메모리 누수에 대 한 자세한 내용은 [MFC의 메모리 누수 탐지](/previous-versions/visualstudio/visual-studio-2010/c99kz476(v=vs.100))문서를 참조 하세요. 프레임 할당의 단점은 해당 범위 외부에서 프레임 변수를 사용할 수 없다는 것입니다. 프레임 할당과 힙 할당을 선택 하는 또 다른 요인은 긴 구조와 개체의 경우 스택 공간이 제한 되는 경우가 많으므로 저장소에 대 한 스택 대신 힙을 사용 하는 것이 좋습니다.

## <a name="see-also"></a>참고 항목

[메모리 관리](memory-management.md)
