---
description: '자세히 알아보기: CObject에서 새 클래스를 파생 시켜야 하나요?'
title: CObject에서 새 클래스를 파생시켜야 합니까?
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
ms.openlocfilehash: d37570cb62f1ee274e4cea85fc95a9221c95fd8a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261309"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>CObject에서 새 클래스를 파생시켜야 합니까?

아니요, 수행하지 않습니다.

Serialization 또는 동적 creatability 같이 제공 하는 기능이 필요한 경우 [CObject](reference/cobject-class.md) 에서 클래스를 파생 시킵니다. 많은 데이터 클래스는 파일에 대해 serialize되어야 하므로 `CObject`에서 해당 클래스를 파생하는 것이 좋습니다. 에서 파생 된 클래스의 예제는 `CObject` [Scribble 샘플](../overview/visual-cpp-samples.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[CObject 클래스: 질문과 대답](cobject-class-frequently-asked-questions.md)
