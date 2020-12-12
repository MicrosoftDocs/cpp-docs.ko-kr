---
description: '자세히 알아보기: ASP, ATL Active Server 페이지 구성 요소 마법사'
title: ASP, ATL Active Server Page 구성 요소 마법사
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.asp.asp
helpviewer_keywords:
- ATL Active Server Page Component Wizard, ASP
ms.assetid: 4d8cafd6-5e12-4461-8911-29288896af3c
ms.openlocfilehash: e9cc11cf60c3a87d6891c98a72eb240729d1a739
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165539"
---
# <a name="asp-atl-active-server-page-component-wizard"></a>ASP, ATL Active Server Page 구성 요소 마법사

ATL Active Server 페이지 구성 요소 마법사의이 페이지에서는 ASP 구성 요소와 관련 된 정보 및 상태를 처리 하는 옵션 설정을 지정할 수 있습니다.

- **선택적 메서드**

   선택적 ASP 메서드인 **OnStartPage** 및 **OnEndPage** 를 개체에 추가 합니다. Active Server 페이지 내장 개체를 설정 하려면이 옵션을 선택 해야 합니다. 기본적으로 선택 되어 있습니다.

- **OnStartPage/OnEndPage**

   [OnStartPage](/previous-versions//ms691624\(v=vs.85\)) 는 스크립트가 개체에 처음 액세스 하려고 할 때 호출 됩니다. **OnEndPage** 은 개체가 스크립트 처리를 마칠 때 호출 됩니다.

- **내장 개체**

   **OnStartPage/OnEndPage** 옵션을 선택 하 여 ASP 내장 개체를 설정 해야 합니다.

|옵션|설명|
|------------|-----------------|
|**요청**|Active Server Pages 내장 **요청** 개체에 대 한 액세스를 제공 합니다. 요청 개체는 HTTP 요청을 전달 하는 데 사용 됩니다.|
|**Response**|Active Server 페이지 내장 **응답** 개체에 대 한 액세스를 제공 합니다. 요청에 대 한 응답으로 응답 개체는 브라우저에 정보를 보내 사용자에 게 표시 합니다.|
|**세션**|Active Server Pages 내장 **세션** 개체에 대 한 액세스를 제공 합니다. **세션** 개체는 상태 정보를 저장 하 고 검색 하는 등 현재 사용자 세션에 대 한 정보를 유지 관리 합니다.|
|**애플리케이션**|Active Server 페이지 내장 **응용 프로그램** 개체에 대 한 액세스를 제공 합니다. **응용 프로그램** 개체는 여러 ASP 개체에서 공유 되는 상태를 관리 합니다.|
|**서버**|Active Server Pages 내장 **서버** 개체에 대 한 액세스를 제공 합니다. **서버** 개체를 사용 하 여 다른 ASP 개체를 만들 수 있습니다.|

## <a name="see-also"></a>참고 항목

[ATL Active Server 페이지 구성 요소 마법사](../../atl/reference/atl-active-server-page-component-wizard.md)<br/>
[ATL Active Server Page 구성 요소](../../atl/reference/adding-an-atl-active-server-page-component.md)
