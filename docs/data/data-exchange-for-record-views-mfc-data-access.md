---
description: '자세히 알아보기: 레코드 뷰에 대 한 데이터 교환 (MFC Data Access)'
title: 레코드 뷰의 데이터 교환   (MFC Data Access)
ms.date: 11/19/2018
helpviewer_keywords:
- RFX (record field exchange), data exchange mechanism
- RFX (record field exchange), record views
- record views, data exchange
- DDX (dialog data exchange), record views
- RFX (record field exchange)
ms.assetid: abc52ca7-6997-47a7-98f3-f347f52b1f72
ms.openlocfilehash: 6ffb82e3fb1e035b1334e15d5b4d1d25634739c4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213210"
---
# <a name="data-exchange-for-record-views---mfc-data-access"></a>레코드 뷰의 데이터 교환   (MFC Data Access)

[클래스 추가](../mfc/reference/adding-an-mfc-odbc-consumer.md) 를 사용 하 여 레코드 뷰의 대화 상자 템플릿 리소스에 있는 컨트롤을 레코드 집합의 필드에 매핑하는 경우 프레임 워크는 레코드 집합에서 컨트롤로, 그리고 컨트롤에서 레코드 집합으로 양방향으로 데이터 교환을 관리 합니다. DDX 메커니즘을 사용하면 데이터를 전송하는 코드를 직접 작성할 필요가 없습니다.

레코드 뷰의 DDX는 클래스 (ODBC)의 레코드 집합에 대 한 [RFX](../data/odbc/record-field-exchange-rfx.md) 와 함께 작동 `CRecordset` 합니다.  RFX는 데이터 원본의 현재 레코드와 레코드 집합 개체의 필드 데이터 멤버 간에 데이터를 이동 합니다. DDX는 필드 데이터 멤버에서 폼의 컨트롤로 데이터를 이동합니다. 이 조합은 먼저 폼 컨트롤을 채운 다음 사용자가 레코드 간을 이동할 때 계속해서 컨트롤을 채웁니다. 또한 업데이트된 데이터를 레코드 집합으로 다시 이동했다가 데이터 소스로 이동할 수도 있습니다.

다음 그림에서는 레코드 뷰에 대 한 DDX와 RFX 간의 관계를 보여 줍니다.

![데이터 교환 및 레코드&#45;필드 교환을&#45;대화 상자](../data/media/vc37xt1.gif "데이터 교환 및 레코드&#45;필드 교환을&#45;대화 상자")<br/>
DDE(Dialog Data Exchange) 및 레코드 필드 교환

DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../mfc/dialog-data-exchange-and-validation.md)를 참조하세요. RFX에 대 한 자세한 내용은 [rfx (레코드 필드 교환)](../data/odbc/record-field-exchange-rfx.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[레코드 뷰 (MFC Data Access)](../data/record-views-mfc-data-access.md)<br/>
[ODBC 드라이버 목록](../data/odbc/odbc-driver-list.md)
