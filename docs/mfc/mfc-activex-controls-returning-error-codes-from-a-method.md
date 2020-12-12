---
description: '자세한 정보: MFC ActiveX 컨트롤: 메서드에서 오류 코드 반환'
title: 'MFC ActiveX 컨트롤: 메서드에서 오류 코드 반환'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- SetNotSupported method, using
- errors [MFC], ActiveX control error codes
- GetNotSupported method [MFC]
- FireError method [MFC]
- SCODE, MFC ActiveX controls
- ThrowError method [MFC]
ms.assetid: 771fb9c9-2413-4dcc-b386-7bc4c4adeafd
ms.openlocfilehash: f6a1f372442ee67787a7a5421dabb4460acfcc7a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206073"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>MFC ActiveX 컨트롤: 메서드에서 오류 코드 반환

이 문서에서는 ActiveX 컨트롤 메서드에서 오류 코드를 반환 하는 방법을 설명 합니다.

메서드 내에서 오류가 발생 했음을 나타내려면 ThrowError (상태 코드)를 매개 변수로 사용 하는 [COleControl::](reference/colecontrol-class.md#throwerror) 멤버 함수를 사용 해야 합니다. 미리 정의 된을 사용 하거나 고유한 항목 중 하나를 정의할 수 있습니다.

> [!NOTE]
> `ThrowError` 는 속성의 Get 또는 Set 함수 또는 자동화 메서드 내에서 오류를 반환 하는 수단 으로만 사용 됩니다. 이러한 경우에는 적절 한 예외 핸들러가 스택에 표시 됩니다.

[Colecontrol:: SetNotSupported](reference/colecontrol-class.md#setnotsupported), [Colecontrol:: getnotsupported](reference/colecontrol-class.md#getnotsupported)및 [colecontrol:: setnotsupported](reference/colecontrol-class.md#setnotpermitted)와 같은 가장 일반적으로 미리 정의 된 scodes에 대 한 도우미 함수가 있습니다.

미리 정의 된 SCODEs와 사용자 지정 코드를 정의 하는 방법에 대 한 지침은 ActiveX 컨트롤의 [Activex 컨트롤에서 오류 처리](mfc-activex-controls-advanced-topics.md) : 고급 항목을 참조 하세요.

코드의 다른 영역에서 예외를 보고 하는 방법에 대 한 자세한 내용은 [COleControl:: FireError](reference/colecontrol-class.md#fireerror) 및 activex 컨트롤에서 [Activex 컨트롤의 오류 처리](mfc-activex-controls-advanced-topics.md) 섹션: 고급 항목을 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)
