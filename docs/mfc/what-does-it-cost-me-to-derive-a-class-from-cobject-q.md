---
description: '자세히 알아보기: CObject에서 클래스를 파생 하는 데 드는 비용은 무엇 인가요?'
title: CObject에서 클래스를 파생시키는 비용
ms.date: 11/04/2016
helpviewer_keywords:
- CObject class [MFC], overhead of derived classes [MFC]
ms.assetid: 9b92c98b-b3dd-48a7-9d24-c3b8554edf90
ms.openlocfilehash: 3dcedb7c15c4e02c6dc8cbb7ce0f239838d8067c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97305236"
---
# <a name="what-does-it-cost-me-to-derive-a-class-from-cobject"></a>CObject에서 클래스를 파생시키는 비용

[CObject](../mfc/reference/cobject-class.md) 클래스에서 파생 되는 오버 헤드는 최소화 됩니다. 파생 클래스는 네 개의 가상 함수와 단일 [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) 개체를 상속 합니다.

## <a name="see-also"></a>참고 항목

[CObject 클래스: 질문과 대답](../mfc/cobject-class-frequently-asked-questions.md)
