---
description: '자세히 알아보기: MFC ActiveX 컨트롤: 속성'
title: 'MFC ActiveX 컨트롤: 속성'
ms.date: 11/04/2016
helpviewer_keywords:
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
- properties [MFC]
ms.assetid: b678a53c-0d9e-476f-8aa0-23b80baaba46
ms.openlocfilehash: 9331be68c2e09fe3a4ad83d21e3ed58bbdfdd61e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206138"
---
# <a name="mfc-activex-controls-properties"></a>MFC ActiveX 컨트롤: 속성

ActiveX 컨트롤은 컨트롤 컨테이너와 통신 하기 위해 이벤트를 발생 시킵니다. 반환 된 컨테이너는 메서드와 속성을 사용 하 여 컨트롤과 통신 합니다. 메서드와 속성은 각각 c + + 클래스의 멤버 함수 및 멤버 변수와 유사 하 게 사용 됩니다. 속성은 모든 컨테이너에 노출 되는 ActiveX 컨트롤의 데이터 멤버입니다. 속성은 자동화 클라이언트 및 ActiveX 컨트롤 컨테이너와 같은 ActiveX 컨트롤을 포함 하는 응용 프로그램에 대 한 인터페이스를 제공 합니다.

속성은 특성도 라고도 합니다.

ActiveX 컨트롤 메서드에 대 한 자세한 내용은 [MFC Activex 컨트롤: 메서드](mfc-activex-controls-methods.md)문서를 참조 하세요.

ActiveX 컨트롤은 스톡 및 사용자 지정 메서드와 속성을 모두 구현할 수 있습니다. 클래스는 `COleControl` 스톡 속성에 대 한 구현을 제공 합니다. 스톡 속성의 전체 목록은 [MFC ActiveX 컨트롤: 스톡 속성 추가](mfc-activex-controls-adding-stock-properties.md)문서를 참조 하세요. 개발자가 정의한 사용자 지정 속성은 ActiveX 컨트롤에 특수 기능을 추가 합니다. 자세한 내용은 [MFC ActiveX 컨트롤: 사용자 지정 속성 추가](mfc-activex-controls-adding-custom-properties.md)를 참조 하세요.

메서드와 같은 사용자 지정 속성과 스톡 속성은 클래스의 기존 멤버 함수 및 속성과 메서드를 처리 하는 디스패치 맵으로 구성 된 메커니즘에서 지원 됩니다 `COleControl` . 또한 이러한 속성에는 개발자가 컨트롤에 추가 정보를 전달 하는 데 사용 하는 매개 변수가 있을 수 있습니다.

다음 문서에서는 ActiveX 컨트롤 속성에 대해 자세히 설명 합니다.

- [MFC ActiveX 컨트롤: 스톡 속성 추가](mfc-activex-controls-adding-stock-properties.md)

- [MFC ActiveX 컨트롤: 사용자 지정 속성 추가](mfc-activex-controls-adding-custom-properties.md)

- [MFC ActiveX 컨트롤: 고급 속성 구현](mfc-activex-controls-advanced-property-implementation.md)

- [MFC ActiveX 컨트롤: 앰비언트 속성 액세스](mfc-activex-controls-accessing-ambient-properties.md)

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)
