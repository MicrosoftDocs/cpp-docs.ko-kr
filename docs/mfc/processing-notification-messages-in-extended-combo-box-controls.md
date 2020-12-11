---
description: '자세히 알아보기: 확장 된 콤보 상자 컨트롤에서 알림 메시지 처리'
title: 확장된 콤보 상자 컨트롤에서 알림 메시지 처리
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
ms.openlocfilehash: ef004c3649ce78b24aa1c77aa90488ae6391dcca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154814"
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>확장된 콤보 상자 컨트롤에서 알림 메시지 처리

사용자가 확장된 콤보 상자를 조작하면 컨트롤(`CComboBoxEx`)이 해당 부모 창(일반적으로 뷰 또는 대화 상자 개체)에 알림 메시지를 보냅니다. 이에 대한 응답으로 작업을 수행하려는 경우 이러한 메시지를 처리합니다. 예를 들어 사용자가 드롭다운 목록을 활성화하거나 컨트롤의 편집 상자를 클릭하면 CBEN_BEGINEDIT 알림이 전송됩니다.

[클래스 마법사](reference/mfc-class-wizard.md) 를 사용 하 여 구현 하려는 메시지의 부모 클래스에 알림 처리기를 추가 합니다.

다음 목록에서는 확장된 콤보 상자 컨트롤에서 전송되는 다양한 알림에 대해 설명합니다.

- CBEN_BEGINEDIT 사용자가 드롭다운 목록을 활성화하거나 컨트롤의 편집 상자를 클릭하면 전송됩니다.

- CBEN_DELETEITEM 항목이 삭제된 경우 전송됩니다.

- CBEN_DRAGBEGIN 사용자가 컨트롤의 편집 부분에 표시된 항목의 이미지를 끌기 시작하면 전송됩니다.

- CBEN_ENDEDIT 사용자가 편집 상자 내에서 작업을 완료하거나 컨트롤의 드롭다운 목록에서 항목을 선택한 경우 전송됩니다.

- CBEN_GETDISPINFO 콜백 항목에 대한 표시 정보를 검색하기 위해 전송됩니다.

- CBEN_INSERTITEM 컨트롤에 새 항목이 삽입된 경우 전송됩니다.

## <a name="see-also"></a>참고 항목

[CComboBoxEx 사용](using-ccomboboxex.md)<br/>
[컨트롤](controls-mfc.md)
