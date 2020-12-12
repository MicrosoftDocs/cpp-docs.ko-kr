---
description: '자세한 정보: 스택 및 큐 컬렉션 만들기'
title: 스택 및 큐 컬렉션 만들기
ms.date: 11/04/2016
helpviewer_keywords:
- MFC collection classes [MFC], stack collections
- collections, stack
- stack
- collection classes [MFC], creating
- queue collections
- MFC collection classes [MFC], queue collections
- stack collections
- collections, queue
ms.assetid: 3c7bc198-35f0-4fc3-aaed-6005a0f22638
ms.openlocfilehash: e6c3d4a2ade4262e01bd5d84529aa57d308a8623
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309773"
---
# <a name="creating-stack-and-queue-collections"></a>스택 및 큐 컬렉션 만들기

이 문서에서는 MFC 목록 클래스에서 [스택](#_core_stacks) 및 [큐](#_core_queues)와 같은 다른 데이터 구조를 만드는 방법을 설명 합니다. 이 예제에서는에서 파생 된 클래스 `CList` 를 사용 하지만 `CList` 기능을 추가 해야 하는 경우가 아니면 직접를 사용할 수 있습니다.

## <a name="stacks"></a><a name="_core_stacks"></a> 스택

표준 목록 컬렉션에는 head와 tail이 모두 있으므로 마지막으로 시작 된 스택의 동작을 모방 하는 파생 된 목록 컬렉션을 쉽게 만들 수 있습니다. 스택은 낙서의 트레이 스택과 같습니다. 트레이가 스택에 추가 되 면 스택에서 위쪽으로 이동 합니다. 마지막으로 추가 된 트레이가 제거 되는 첫 번째입니다. 목록 컬렉션 멤버 함수 `AddHead` 및를 `RemoveHead` 사용 하 여 목록에서 특정 요소를 추가 하 고 제거할 수 있으므로 가장 최근에 추가한 요소가 가장 먼저 제거 됩니다.

#### <a name="to-create-a-stack-collection"></a>스택 컬렉션을 만들려면

1. 기존 MFC 목록 클래스 중 하나에서 새 목록 클래스를 파생 시키고 스택 작업 기능을 지원 하기 위해 더 많은 멤버 함수를 추가 합니다.

   다음 예제에서는 멤버 함수를 추가 하 여 스택에 요소를 푸시하고, 스택의 맨 위에 있는 요소를 피킹 하 고, 스택에서 맨 위에 있는 요소를 팝 하는 방법을 보여 줍니다.

   [!code-cpp[NVC_MFCCollections#20](codesnippet/cpp/creating-stack-and-queue-collections_1.h)]

이 방법은 기본 클래스를 노출 합니다 `CObList` . 사용자는 스택에 적합 한지에 관계 없이 모든 `CObList` 멤버 함수를 호출할 수 있습니다.

## <a name="queues"></a><a name="_core_queues"></a> 큐

표준 목록 컬렉션에는 head와 tail이 모두 있으므로 첫 번째-아웃 큐의 동작을 모방 하는 파생 된 목록 컬렉션을 쉽게 만들 수 있습니다. 큐는 낙서의 사람들과 비슷합니다. 줄의 첫 번째 사람이 가장 먼저 처리 됩니다. 사용자가 많을 수록 줄의 끝으로 이동 하 여 차례로 기다립니다. 목록 컬렉션 멤버 함수 `AddTail` 및를 `RemoveHead` 사용 하 여 목록의 head 또는 tail에서 특정 요소를 추가 하 고 제거할 수 있습니다. 따라서 가장 최근에 추가 된 요소는 항상 마지막으로 제거 됩니다.

#### <a name="to-create-a-queue-collection"></a>큐 컬렉션을 만들려면

1. MFC 라이브러리와 함께 제공 되는 미리 정의 된 목록 클래스 중 하나에서 새 목록 클래스를 파생 시키고 큐 작업의 의미 체계를 지 원하는 멤버 함수를 더 추가 합니다.

   다음 예제에서는 멤버 함수를 추가 하 여 큐의 끝에 요소를 추가 하 고 큐 앞에서 요소를 가져오는 방법을 보여 줍니다.

   [!code-cpp[NVC_MFCCollections#21](codesnippet/cpp/creating-stack-and-queue-collections_2.h)]

## <a name="see-also"></a>참고 항목

[컬렉션](collections.md)
