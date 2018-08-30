---
title: 형식 라이브러리에서 MFC 클래스 추가 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 656d5c357874a7b470eb2fd630c91ad0aefa5a0d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205375"
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>형식 라이브러리에서 MFC 클래스 추가
이 마법사를 사용 하 여 인터페이스를 사용할 수 있는 형식 라이브러리에서에서 MFC 클래스를 만듭니다. MFC 클래스를 [MFC 응용 프로그램](../../mfc/reference/creating-an-mfc-application.md), [MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md) 또는 [MFC ActiveX 컨트롤](../../mfc/reference/creating-an-mfc-activex-control.md)에 추가할 수 있습니다.  
  
> [!NOTE]
>  형식 라이브러리에서 클래스를 추가 하려면 사용 하도록 설정 하는 자동화를 사용 하 여 MFC 프로젝트를 만들 필요가 없습니다.  
  
 형식 라이브러리와 매개 변수 및 반환 형식 메서드를 정의 구성 요소에 의해 노출 된 인터페이스에 대 한 이진 설명을 포함 합니다. 형식 라이브러리에 표시 하려면 등록 해야 합니다 **사용 가능한 형식 라이브러리** Typelib 마법사에서 추가 클래스에서 목록. "내 Distributed COM:: 형식 라이브러리 및 언어 통합"에 대 한 자세한 내용은 MSDN 라이브러리의를 참조 하세요.  
  
### <a name="to-add-an-mfc-class-from-a-type-library"></a>형식 라이브러리에서 MFC 클래스를 추가 하려면  
  
1.  하나로 **솔루션 탐색기** 또는 [클래스 뷰](https://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925), 클래스를 추가 하려면 프로젝트의 이름을 마우스 오른쪽 단추로 클릭 합니다.  
  
2.  바로 가기 메뉴에서 **추가**를 클릭한 다음, **클래스 추가**를 클릭합니다.  
  
3.  에 [클래스 추가](../../ide/add-class-dialog-box.md) 대화 상자의 템플릿 창에서 클릭 **Typelib의 MFC 클래스**를 클릭 하 고 **열기** 표시할는 [Typelib 마법사에서 클래스 추가 ](../../mfc/reference/add-class-from-typelib-wizard.md).  
  
 마법사에서 형식 라이브러리에 둘 이상의 클래스를 추가할 수 있습니다. 마찬가지로 단일 마법사 세션에서 둘 이상의 형식 라이브러리에서 클래스를 추가할 수 있습니다.  
  
 마법사에서 파생 된 MFC 클래스를 만듭니다 [COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md), 선택한 형식 라이브러리에서 추가한 각 인터페이스에 대 한 합니다. `COleDispatchDriver` OLE 자동화의 클라이언트 쪽을 구현합니다.  
  
## <a name="see-also"></a>참고 항목  
 [자동화 클라이언트](../../mfc/automation-clients.md)   
 [자동화 클라이언트: 형식 라이브러리 사용](../../mfc/automation-clients-using-type-libraries.md)

