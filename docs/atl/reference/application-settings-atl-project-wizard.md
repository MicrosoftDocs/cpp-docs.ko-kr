---
description: '자세히 알아보기: 응용 프로그램 설정, ATL 프로젝트 마법사'
title: 애플리케이션 설정, ATL 프로젝트 마법사
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.atl.com.appset
helpviewer_keywords:
- ATL Project Wizard, application settings
ms.assetid: d48c9fc5-f439-49fd-884c-8bcfa7d52991
ms.openlocfilehash: 7805fcb8760035ac232a36a42a1cf34273ee42a4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158947"
---
# <a name="application-settings-atl-project-wizard"></a>애플리케이션 설정, ATL 프로젝트 마법사

ATL 프로젝트 마법사의 **응용 프로그램 설정** 페이지를 사용 하 여 기본 기능을 디자인 하 고 새 ATL 프로젝트에 추가할 수 있습니다.

## <a name="server-type"></a>서버 유형

다음 세 가지 서버 유형 중 하나를 선택 합니다.

- **DLL (동적 연결 라이브러리)**

   In-process 서버를 만들려면 선택 합니다.

- **실행 파일 (EXE)**

   로컬 out-of-process 서버를 만들려면 선택 합니다. 이 옵션은 MFC 또는 COM + 1.0에 대 한 지원을 허용 하지 않습니다. 프록시/스텁 코드의 병합을 허용 하지 않습니다.

- **서비스 (EXE)**

   Windows가 시작 될 때 백그라운드에서 실행 되는 Windows 응용 프로그램을 만들려면 선택 합니다. 이 옵션은 MFC 또는 COM + 1.0에 대 한 지원을 허용 하지 않으며 프록시/스텁 코드 병합을 허용 하지 않습니다.

## <a name="additional-options"></a>추가 옵션

> [!NOTE]
> 모든 추가 옵션은 DLL 프로젝트에만 사용할 수 있습니다.

- **프록시/스텁 코드 병합 허용**

   인터페이스를 마샬링하는 데 필요한 경우 편의를 위해 **프록시/스텁 코드 병합 허용** 확인란을 선택 합니다. 이 옵션은 서버와 동일한 실행 파일에 MIDL 생성 프록시 및 스텁 코드를 배치 합니다.

- **MFC 지원**

   개체에 MFC 지원이 포함 되도록 지정 하려면 선택 합니다. 이 옵션은 프로젝트를 MFC 라이브러리에 연결 하 여 포함 된 클래스 및 함수에 액세스할 수 있도록 합니다.

- **COM + 1.0 지원**

   COM + 1.0 구성 요소를 지원 하도록 프로젝트 빌드 설정을 수정 하려면 선택 합니다. 라이브러리의 표준 목록 외에도 마법사는 COM + 1.0 구성 요소별 라이브러리 comsvcs를 추가 합니다.

   또한 mtxex.dll는 응용 프로그램이 시작 될 때 호스트 시스템에서 지연 로드 됩니다.

- **구성 요소 등록자 지원**

   ATL 프로젝트에 COM + 1.0 구성 요소에 대 한 지원이 포함 된 경우이 옵션을 설정할 수 있습니다. 구성 요소 등록자를 사용 하면 COM + 1.0 개체에서 구성 요소 목록을 얻거나, 구성 요소를 등록 하거나, 구성 요소를 개별적으로 또는 한꺼번에 등록 취소할 수 있습니다.

## <a name="see-also"></a>참고 항목

[ATL 프로젝트 마법사](../../atl/reference/atl-project-wizard.md)<br/>
[ATL 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)<br/>
[기본 ATL 프로젝트 구성](../../atl/reference/default-atl-project-configurations.md)
