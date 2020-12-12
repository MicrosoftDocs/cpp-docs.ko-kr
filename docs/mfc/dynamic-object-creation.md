---
description: '자세한 정보: 동적 개체 만들기'
title: 동적 개체 만들기
ms.date: 03/27/2020
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
ms.openlocfilehash: b39c0561a98807030c471b3de4cd5921883f9f0e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290975"
---
# <a name="dynamic-object-creation"></a>동적 개체 만들기

이 문서에서는 런타임에 개체를 동적으로 만드는 방법을 설명 합니다. 프로시저는 [Run-Time 클래스 정보에 액세스](accessing-run-time-class-information.md)문서에 설명 된 대로 런타임 클래스 정보를 사용 합니다.

#### <a name="dynamically-create-an-object-given-its-run-time-class"></a>해당 런타임 클래스가 지정 된 개체를 동적으로 만듭니다.

1. 의 함수를 사용 하 여 동적으로 개체를 만들려면 다음 코드를 사용 `CreateObject` `CRuntimeClass` 합니다. 오류가 발생 하면에서 예외를 발생 시 키 지 `CreateObject` 않고 **NULL** 을 반환 합니다.

   [!code-cpp[NVC_MFCCObjectSample#6](codesnippet/cpp/dynamic-object-creation_1.cpp)]

## <a name="see-also"></a>참고 항목

[창 개체 소멸](tn017-destroying-window-objects.md) 
 [CObject 사용](using-cobject.md)
