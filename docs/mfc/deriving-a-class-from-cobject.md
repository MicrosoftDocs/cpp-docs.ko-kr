---
description: '자세한 정보: CObject에서 클래스 파생'
title: CObject에서 클래스 파생시키기
ms.date: 11/04/2016
helpviewer_keywords:
- DECLARE_DYNCREATE macro [MFC]
- DECLARE_SERIAL macro [MFC]
- macros [MFC], serialization
- serialization [MFC], macros
- DECLARE_DYNAMIC macro [MFC]
- derived classes [MFC], from CObject
- CObject class [MFC], deriving serializable classes
- CObject class [MFC], deriving from
ms.assetid: 5ea4ea41-08b5-4bd8-b247-c5de8c152a27
ms.openlocfilehash: c6c2ea75354d783b234bc3f7cac7a08dac4f05da
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240704"
---
# <a name="deriving-a-class-from-cobject"></a>CObject에서 클래스 파생시키기

이 문서에서는 [CObject](reference/cobject-class.md)에서 클래스를 파생 시키는 데 필요한 최소 단계에 대해 설명 합니다. 다른 `CObject` 클래스 문서 `CObject` 에서는 serialization, 진단 디버깅 지원 등의 특정 기능을 활용 하는 데 필요한 단계에 대해 설명 합니다.

의 토론에서 `CObject` "인터페이스 파일" 및 "구현 파일" 이라는 용어는 자주 사용 됩니다. 인터페이스 파일 (헤더 파일 이라고 함) 또는입니다. H 파일) 클래스를 사용 하는 데 필요한 클래스 선언과 기타 정보를 포함 합니다. 구현 파일 (또는)입니다. CPP 파일)에는 클래스 정의 및 클래스 멤버 함수를 구현 하는 코드가 포함 됩니다. 예를 들어 라는 클래스의 경우 `CPerson` 일반적으로 PERSON 이라는 이름의 인터페이스 파일을 만듭니다. H와 PERSON 이라는 구현 파일이 있습니다. .CPP. 그러나 응용 프로그램 간에 공유 되지 않는 일부 작은 클래스의 경우 인터페이스와 구현을 단일으로 결합 하는 것이 더 쉬울 수 있습니다. CPP 파일.

에서 클래스를 파생 시킬 때 네 가지 수준의 기능 중에서 선택할 수 있습니다 `CObject` .

- 기본 기능: 런타임 클래스 정보 또는 직렬화에 대 한 지원은 없지만 진단 메모리 관리를 포함 합니다.

- 기본 기능 및 런타임 클래스 정보에 대 한 지원.

- 기본 기능과 런타임 클래스 정보 및 동적 생성을 지원 합니다.

- 기본 기능 및 런타임 클래스 정보, 동적 생성 및 serialization에 대 한 지원

이후 직렬화가 필요한 경우 다시 사용 하도록 디자인 된 클래스 (나중에 기본 클래스 역할을 하는 클래스)에는 최소한 런타임 클래스 지원 및 serialization 지원이 포함 되어야 합니다.

파생 된 클래스의 선언 및 구현에서 특정 선언 및 구현 매크로를 사용 하 여 기능 수준을 선택 `CObject` 합니다.

다음 표에서는 serialization 및 런타임 정보를 지 원하는 데 사용 되는 매크로 간의 관계를 보여 줍니다.

### <a name="macros-used-for-serialization-and-run-time-information"></a>Serialization 및 Run-Time 정보에 사용 되는 매크로

|매크로 사용 됨|CObject:: IsKindOf|CRuntimeClass::<br /><br /> CreateObject|CArchive:: operator>><br /><br /> CArchive:: operator<<|
|----------------|-----------------------|--------------------------------------|-------------------------------------------------------|
|기본 `CObject` 기능|아니요|아니요|아니요|
|`DECLARE_DYNAMIC`|예|아니요|아니요|
|`DECLARE_DYNCREATE`|예|예|아니요|
|`DECLARE_SERIAL`|예|예|예|

#### <a name="to-use-basic-cobject-functionality"></a>기본 CObject 기능을 사용 하려면

1. 일반 c + + 구문을 사용 하 여 `CObject` (또는에서 파생 된 클래스)에서 클래스를 파생 시킵니다 `CObject` .

   다음 예제에서는에서 클래스를 파생 하는 가장 간단한 사례를 보여 줍니다 `CObject` .

   [!code-cpp[NVC_MFCCObjectSample#1](codesnippet/cpp/deriving-a-class-from-cobject_1.h)]

그러나 일반적으로의 일부 멤버 함수를 재정의 하 여 `CObject` 새 클래스의 특정 기능을 처리할 수 있습니다. 예를 들어 일반적으로의 함수를 재정의 하 여 `Dump` `CObject` 클래스의 콘텐츠에 대 한 디버깅 출력을 제공할 수 있습니다. 을 재정의 하는 방법에 대 한 자세한 `Dump` 내용은 [개체 덤프 사용자 지정](/previous-versions/visualstudio/visual-studio-2010/sc15kz85(v=vs.100))문서를 참조 하세요. 의 함수를 재정의 하 여 `AssertValid` `CObject` 클래스 개체의 데이터 멤버에 대 한 일관성의 유효성을 검사 하는 사용자 지정 된 테스트를 제공할 수도 있습니다. 을 재정의 하는 방법에 대 한 설명은 `AssertValid` [MFC ASSERT_VALID 및 CObject:: AssertValid](reference/diagnostic-services.md#assert_valid)를 참조 하세요.

[기능 수준을 지정](specifying-levels-of-functionality.md) 하는 문서에서는 런타임 클래스 정보, 동적 개체 만들기 및 serialization을 포함 하 여 다른 수준의 기능을 지정 하는 방법을 설명 합니다.

## <a name="see-also"></a>참고 항목

[CObject 사용](using-cobject.md)
