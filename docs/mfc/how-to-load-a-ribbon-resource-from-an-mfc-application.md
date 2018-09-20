---
title: '방법: MFC 응용 프로그램에서 리본 리소스 로드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1643989a96a9003847fb53de624bff12cd51cd88
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434296"
---
# <a name="how-to-load-a-ribbon-resource-from-an-mfc-application"></a>방법: MFC 응용 프로그램에서 리본 리소스 로드

응용 프로그램에서 리본 리소스를 사용하려면 응용 프로그램을 수정하여 리본 리소스를 로드합니다.

### <a name="to-load-a-ribbon-resource"></a>리본 리소스를 로드하려면

1. `Ribbon Control` 클래스에서 `CMainFrame` 개체를 선언합니다.

```
    CMFCRibbonBar m_wndRibbonBar;
```

1. `CMainFrame::OnCreate`에서 리본 컨트롤을 만들고 초기화합니다.

```
    if (!m_wndRibbonBar.Create (this))
{
    return -1;
}

    if (!m_wndRibbonBar.LoadFromResource(IDR_RIBBON))
{
    return -1;
}
```

## <a name="see-also"></a>참고 항목

[리본 디자이너(MFC)](../mfc/ribbon-designer-mfc.md)

