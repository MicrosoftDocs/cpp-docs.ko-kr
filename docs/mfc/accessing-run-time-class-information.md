---
description: '자세히 알아보기: Run-Time 클래스 정보 액세스'
title: 런타임 클래스 정보 액세스
ms.date: 11/04/2016
helpviewer_keywords:
- CObject class [MFC], and RTTI
- CObject class [MFC], using IsKindOf method [MFC]
- run time [MFC], class information
- RUNTIME_CLASS macro [MFC]
- CObject class [MFC], using RUNTIME_CLASS macro [MFC]
- RTTI compiler option [MFC]
- CObject class [MFC], accessing run-time class information
- run time [MFC]
- IsKindOf method method [MFC]
- run-time class [MFC], accessing information
- classes [MFC], run-time class information
- run-time class [MFC]
- RUNTIME_CLASS macro, using
ms.assetid: 3445a9af-0bd6-4496-95c3-aa59b964570b
ms.openlocfilehash: fb5877a3ac6ece58ed46bde2b5fbdcc49db10351
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169478"
---
# <a name="accessing-run-time-class-information"></a>런타임 클래스 정보 액세스

이 문서에서는 런타임에 개체의 클래스에 대 한 정보에 액세스 하는 방법을 설명 합니다.

> [!NOTE]
> MFC는 Visual C++ 4.0에 도입 된 RTTI ( [런타임 형식 정보](../cpp/run-time-type-information.md) ) 지원을 사용 하지 않습니다.

Cobject에서 클래스를 파생 [하 고](reference/cobject-class.md) **DECLARE** _ **DYNAMIC** 및를 사용 하는 경우 `IMPLEMENT_DYNAMIC` `DECLARE_DYNCREATE` `IMPLEMENT_DYNCREATE` `DECLARE_SERIAL` `IMPLEMENT_SERIAL` [cobject에서 클래스를 파생](deriving-a-class-from-cobject.md)하는 방법 문서에 설명 된 클래스에는 `CObject` 런타임에 개체의 정확한 클래스를 확인할 수 있는 기능이 있습니다.

이 기능은 함수 인수에 대 한 추가 형식 검사가 필요한 경우와 개체의 클래스를 기반으로 특수 용도의 코드를 작성 해야 하는 경우에 가장 유용 합니다. 그러나이 방법은 가상 함수의 기능을 복제 하기 때문에 일반적으로 권장 되지 않습니다.

`CObject`멤버 함수를 `IsKindOf` 사용 하 여 특정 개체가 지정 된 클래스에 속해 있는지 또는 특정 클래스에서 파생 된 경우이를 확인할 수 있습니다. 에 대 한 인수는 `IsKindOf` `CRuntimeClass` `RUNTIME_CLASS` 클래스 이름으로 매크로를 사용 하 여 가져올 수 있는 개체입니다.

### <a name="to-use-the-runtime_class-macro"></a>RUNTIME_CLASS 매크로를 사용 하려면

1. `RUNTIME_CLASS`클래스에 대해 여기에 표시 된 것 처럼 클래스의 이름과 함께를 사용 합니다 `CObject` .

   [!code-cpp[NVC_MFCCObjectSample#4](codesnippet/cpp/accessing-run-time-class-information_1.cpp)]

런타임 클래스 개체에 직접 액세스 해야 하는 경우는 거의 없습니다. 다음 절차에 표시 된 것 처럼 보다 일반적인 사용은 런타임 클래스 개체를 함수에 전달 하는 것입니다 `IsKindOf` . `IsKindOf`함수는 개체를 테스트 하 여 특정 클래스에 속하는지 여부를 확인 합니다.

#### <a name="to-use-the-iskindof-function"></a>IsKindOf 함수를 사용 하려면

1. 클래스에 런타임 클래스가 지원 되는지 확인 합니다. 즉, 클래스는에서 직접 또는 간접적으로 파생 되어야 하며,,,, 및 `CObject` 매크로 는  `IMPLEMENT_DYNAMIC` `DECLARE_DYNCREATE` `IMPLEMENT_DYNCREATE` `DECLARE_SERIAL` `IMPLEMENT_SERIAL` [CObject에서 클래스 파생](deriving-a-class-from-cobject.md)문서에 설명 된, 및 매크로를 사용 하 여 파생 되어야 합니다.

1. 다음과 같이 `IsKindOf` 매크로를 사용 하 여 해당 클래스의 개체에 대 한 멤버 함수를 호출 하 여 `RUNTIME_CLASS` 인수를 생성 합니다 `CRuntimeClass` .

   [!code-cpp[NVC_MFCCObjectSample#2](codesnippet/cpp/accessing-run-time-class-information_2.h)]

   [!code-cpp[NVC_MFCCObjectSample#5](codesnippet/cpp/accessing-run-time-class-information_3.cpp)]

    > [!NOTE]
    >  IsKindOf는 개체가 지정 된 클래스 또는 지정 된 클래스에서 파생 된 클래스의 멤버인 경우 **TRUE** 를 반환 합니다. `IsKindOf` 는 여러 상속 또는 가상 기본 클래스를 지원 하지 않지만 필요한 경우 파생 된 Microsoft Foundation 클래스에 대해 여러 상속을 사용할 수 있습니다.

런타임 클래스 정보를 사용 하는 한 가지 방법은 개체를 동적으로 만드는 것입니다. 이 프로세스는 [동적 개체 만들기](dynamic-object-creation.md)문서에 설명 되어 있습니다.

Serialization 및 런타임 클래스 정보에 대 한 자세한 내용은 MFC 및 [serialization](serialization-in-mfc.md) [의 문서 파일](files-in-mfc.md) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[CObject 사용](using-cobject.md)
