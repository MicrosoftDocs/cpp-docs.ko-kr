---
description: One-Stage 및 Two-Stage 개체 생성에 대해 자세히 알아보세요.
title: 1단계 및 2단계 개체 생성
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
ms.openlocfilehash: d46a8d380c263c4ce18671f02b11d5b058bc8410
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243915"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>1단계 및 2단계 개체 생성

펜 및 브러시와 같은 그래픽 개체를 만드는 두 가지 방법 중에서 선택할 수 있습니다.

- *1 단계 생성*: 생성자를 사용 하 여 한 단계로 개체를 구성 하 고 초기화 합니다.

- *2 단계 생성*: 두 개의 별도 단계로 개체를 구성 하 고 초기화 합니다. 생성자는 개체를 만들고 초기화 함수에서이를 초기화 합니다.

2 단계 생성은 항상 더 안전 합니다. 단일 단계 생성에서는 잘못 된 인수를 제공 하거나 메모리 할당에 실패 하는 경우 생성자가 예외를 throw 할 수 있습니다. 이 문제는 2 단계 생성에 의해 방지 되지만 실패를 확인 해야 합니다. 두 경우 모두 개체 소멸은 동일한 프로세스입니다.

> [!NOTE]
> 이러한 기술은 그래픽 개체 뿐만 아니라 개체를 만드는 데 적용 됩니다.

## <a name="example-of-both-construction-techniques"></a>두 생성 기술의 예

다음 간단한 예제에서는 pen 개체를 구성 하는 두 가지 방법을 보여 줍니다.

[!code-cpp[NVC_MFCDocViewSDI#6](codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]

### <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [그래픽 개체](graphic-objects.md)

- [그래픽 개체를 선택하여 디바이스 컨텍스트로 넣기](selecting-a-graphic-object-into-a-device-context.md)

- [디바이스 컨텍스트](device-contexts.md)

- [뷰에 그리기](drawing-in-a-view.md)

## <a name="see-also"></a>참고 항목

[그래픽 개체](graphic-objects.md)
