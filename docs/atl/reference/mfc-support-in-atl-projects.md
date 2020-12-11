---
description: '자세한 정보: ATL 프로젝트의 MFC 지원'
title: ATL 프로젝트의 MFC 지원
ms.date: 11/04/2016
f1_keywords:
- vc.atl.addmfc
helpviewer_keywords:
- ATL projects, MFC support
ms.assetid: f90b4276-cb98-4c11-902c-9ebcfe6f954b
ms.openlocfilehash: 8614bfdd5320e0ecdf34cc96251fa8a20f2dede9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157921"
---
# <a name="mfc-support-in-atl-projects"></a>ATL 프로젝트의 MFC 지원

ATL 프로젝트 마법사에서 **Mfc 지원** 을 선택 하는 경우 프로젝트는 응용 프로그램을 mfc 응용 프로그램 개체 (클래스)로 선언 합니다. 프로젝트는 MFC 라이브러리를 초기화 하 고 [CWinApp](../../mfc/reference/cwinapp-class.md)에서 파생 된 클래스 ( *ProjName* 클래스)를 인스턴스화합니다.

이 옵션은 특성을 사용 하지 않는 ATL DLL 프로젝트에만 사용할 수 있습니다.

```
class CProjNameApp : public CWinApp
{
public:

// Overrides
    virtual BOOL InitInstance();
virtual int ExitInstance();
DECLARE_MESSAGE_MAP()
};

BEGIN_MESSAGE_MAP(CProjNameApp, CWinApp)
END_MESSAGE_MAP()

CProjNameApp theApp;

BOOL CProjNameApp::InitInstance()
{
    return CWinApp::InitInstance();

}

int CProjNameApp::ExitInstance()
{
    return CWinApp::ExitInstance();

}
```

클래스 뷰에서 응용 프로그램 개체 클래스와 해당 및 함수를 볼 수 있습니다 `InitInstance` `ExitInstance` .

## <a name="see-also"></a>참고 항목

[클래스 추가](../../ide/adding-a-class-visual-cpp.md)<br/>
[ATL 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)<br/>
[기본 ATL 프로젝트 구성](../../atl/reference/default-atl-project-configurations.md)
