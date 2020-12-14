---
description: '자세한 정보: 기능 수준 지정'
title: 기능 수준 지정
ms.date: 11/06/2018
helpviewer_keywords:
- CObject class [MFC], adding functionality to derived classes
- runtime [MFC], class information
- serialization [MFC], Cobject
- dynamic creation support
- levels [MFC], functionality in CObject
- run-time class [MFC], information support
- levels [MFC]
ms.assetid: 562669ba-c858-4f66-b5f1-b3beeea4f486
ms.openlocfilehash: 1b016cd5a41d3e09790f678a2d49d88df33d9782
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216849"
---
# <a name="specifying-levels-of-functionality"></a>기능 수준 지정

이 문서에서는 [CObject](../mfc/reference/cobject-class.md)파생 클래스에 다음 수준의 기능을 추가 하는 방법을 설명 합니다.

- 런타임 클래스 정보

- 동적 만들기 지원

- Serialization 지원

기능에 대 한 일반적인 설명은 `CObject` [CObject에서 클래스 파생](../mfc/deriving-a-class-from-cobject.md)문서를 참조 하세요.

## <a name="to-add-run-time-class-information"></a>런타임 클래스 정보를 추가 하려면

1. `CObject` [CObject에서 클래스 파생](../mfc/deriving-a-class-from-cobject.md) 문서에 설명 된 대로에서 클래스를 파생 시킵니다.

1. 다음과 같이 클래스 선언에서 DECLARE_DYNAMIC 매크로를 사용 합니다.

   [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/specifying-levels-of-functionality_1.h)]

1. 구현 파일 ()에서 IMPLEMENT_DYNAMIC 매크로를 사용 합니다. CPP)의 클래스입니다. 이 매크로는 다음과 같이 클래스와 해당 기본 클래스의 이름을 인수로 사용 합니다.

   [!code-cpp[NVC_MFCCObjectSample#3](../mfc/codesnippet/cpp/specifying-levels-of-functionality_2.cpp)]

> [!NOTE]
> 항상 구현 파일 ()에 IMPLEMENT_DYNAMIC을 배치 합니다. CPP)를 사용할 경우 IMPLEMENT_DYNAMIC 매크로는 컴파일하는 동안 한 번만 계산 되므로 인터페이스 파일 ()에서 사용 하면 안 됩니다. H)를 둘 이상의 파일에 포함할 수 있습니다.

## <a name="to-add-dynamic-creation-support"></a>동적 만들기 지원을 추가 하려면

1. 에서 클래스를 파생 시킵니다 `CObject` .

1. 클래스 선언에서 DECLARE_DYNCREATE 매크로를 사용 합니다.

1. 인수가 없는 생성자 (기본 생성자)를 정의 합니다.

1. 클래스 구현 파일에서 IMPLEMENT_DYNCREATE 매크로를 사용 합니다.

## <a name="to-add-serialization-support"></a>Serialization 지원을 추가 하려면

1. 에서 클래스를 파생 시킵니다 `CObject` .

1. `Serialize`멤버 함수를 재정의 합니다.

   > [!NOTE]
   > 을 직접 호출 하는 경우, `Serialize` 다형 포인터를 통해 개체를 직렬화 하지 않으려면 3 ~ 5 단계를 생략 합니다.

1. 클래스 선언에서 DECLARE_SERIAL 매크로를 사용 합니다.

1. 인수가 없는 생성자 (기본 생성자)를 정의 합니다.

1. 클래스 구현 파일에서 IMPLEMENT_SERIAL 매크로를 사용 합니다.

> [!NOTE]
> "다형 포인터"는 클래스의 개체 (호출) 또는에서 파생 된 클래스의 개체 (예를 들어, B)를 가리킵니다. 다형 포인터를 통해 serialize 하려면 프레임 워크에서 serialize 하는 개체의 런타임 클래스 (B)를 결정 해야 합니다 .이 클래스는 일부 기본 클래스 (A)에서 파생 된 클래스의 개체 일 수 있기 때문입니다.

에서 클래스를 파생 시킬 때 serialization을 사용 하도록 설정 하는 방법에 대 한 자세한 `CObject` 내용은 MFC 및 [serialization](../mfc/serialization-in-mfc.md) [의 문서 파일](../mfc/files-in-mfc.md) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[CObject에서 클래스 파생](../mfc/deriving-a-class-from-cobject.md)
