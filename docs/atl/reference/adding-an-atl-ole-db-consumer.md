---
title: ATL OLE DB 소비자 추가 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
- OLE DB, adding ATL OLE DB consumer to projects
- ATL OLE DB consumers
ms.assetid: f940a513-4e42-4148-b521-dd0d7dc89fa2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90b16c84c0dc2c921722c4c80a1e2bdf0e091d9c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="adding-an-atl-ole-db-consumer"></a>ATL OLE DB 소비자 추가
이 마법사를 사용 하 여 프로젝트에 ATL OLE DB 소비자를 추가 합니다. ATL OLE DB 소비자는 데이터 원본에 액세스 하는 데 필요한 OLE DB 접근자 클래스 및 데이터 바인딩으로 구성 됩니다. 프로젝트 (ATL OLE DB 소비자 마법사를 추가 하는 자동으로) ATL 지원을 포함 하는 MFC 또는 Win32 응용 프로그램 또는 ATL COM 응용 프로그램으로 만든 것 이어야 합니다.  
  
 **참고** MFC 프로젝트에 OLE DB 소비자를 추가할 수 있습니다. 이렇게 하면 ATL OLE DB 소비자 마법사는 필요한 COM 지원 프로젝트에 추가 합니다. MFC 프로젝트를 만들 때 선택 했다고 가정은 **ActiveX 컨트롤** 확인란 (에 **고급 기능** MFC 프로젝트 응용 프로그램 마법사의 페이지)를 기본적으로 선택 된 항목을 합니다. 이 옵션을 선택 하 여 응용 프로그램 호출 하면 **CoInitialize** 및 **CoUninitialize**합니다. 선택 하지 않은 경우 **ActiveX 컨트롤** 를 호출 해야 하는 MFC 프로젝트를 만들 때 **CoInitialize** 및 **CoUninitialize** 주 코드에 있습니다.  
  
### <a name="to-add-an-atl-ole-db-consumer-to-your-project"></a>프로젝트에 ATL OLE DB 소비자를 추가 하려면  
  
1.  클래스 뷰에서 프로젝트를 마우스 오른쪽 단추로 클릭 합니다. 바로 가기 메뉴를 클릭 **추가** 클릭 하 고 **클래스 추가**합니다.  
  
2.  Visual c + + 폴더를 두 번 클릭은 **ATL OLE DB 소비자** 아이콘 또는 선택 하 고 클릭 **열려**합니다.  
  
     ATL OLE DB 소비자 마법사가 열립니다.  
  
3.  에 설명 된 대로 설정을 정의 [ATL OLE DB 소비자 마법사](../../atl/reference/atl-ole-db-consumer-wizard.md)합니다.  
  
4.  클릭 **마침** 마법사를 닫습니다. 새로 만든된 OLE DB 소비자 코드 프로젝트에 삽입 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [코드 마법사로 기능 추가](../../ide/adding-functionality-with-code-wizards-cpp.md)

