---
description: '자세한 정보: 방법: 기존 MFC 리본을 리본 리소스로 변환'
title: '방법: 기존 MFC 리본을 리본 리소스로 변환'
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource, converting from an MFC ribbon
- MFC ribbon, converting to a ribbon resource
ms.assetid: 324b7ff6-58f9-4691-96a9-9836a79d0fb6
ms.openlocfilehash: 825b8b4e3322afd8919ffad0f5e0f73c9d52be78
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290286"
---
# <a name="how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource"></a>방법: 기존 MFC 리본을 리본 리소스로 변환

리본 리소스는 수동으로 코딩 된 리본 보다 시각화, 수정 및 유지 관리 하기가 더 쉽습니다. 이 항목에서는 MFC 프로젝트에서 수동으로 코딩 된 리본을 리본 리소스로 변환 하는 방법에 대해 설명 합니다.

MFC 리본 클래스 (예: [Cmfcribbon Bar 클래스](reference/cmfcribbonbar-class.md))를 사용 하는 코드가 있는 기존 mfc 프로젝트가 있어야 합니다.

### <a name="to-convert-an-mfc-ribbon-to-a-ribbon-resource"></a>MFC 리본을 리본 리소스로 변환 하려면

1. Visual Studio의 기존 MFC 프로젝트에서 개체가 초기화 된 소스 파일을 엽니다 `CMFCRibbonBar` . 일반적으로이 파일은 mainfrm.cpp입니다. 리본에 대 한 초기화 코드 뒤에 다음 코드를 추가 합니다.

```
    m_wndRibbonBar.SaveToXMLFile("RibbonOutput.xml");
```

   파일을 저장하고 닫습니다.

1. MFC 응용 프로그램을 빌드하고 실행 한 다음 메모장에서 RibbonOutput.txt를 열고 해당 내용을 복사 합니다.

1. Visual Studio의 **프로젝트** 메뉴에서 **리소스 추가** 를 클릭 합니다. **리소스 추가** 대화 상자에서 **리본** 을 선택한 다음 **새로 만들기** 를 클릭 합니다.

   Visual Studio에서 리본 리소스를 만들고 디자인 뷰에서 엽니다. 리본 리소스 ID는 IDR_RIBBON1 **리소스 뷰** 에 표시 됩니다. 리본은 ribbon1.xml. .mfcribbon-ms XML 파일에 정의 되어 있습니다.

1. Visual Studio에서 .mfcribbon-ms ribbon1.xml를 열고, 내용을 삭제 한 다음, 이전에 복사한 RibbonOutput.txt의 내용을 붙여넣습니다. Ribbon1.xml. .mfcribbon-ms를 저장 하 고 닫습니다.

1. Cmfc리본 표시줄 개체가 초기화 된 원본 파일 (일반적으로 mainfrm.cpp)을 다시 열고 기존 리본 코드를 주석으로 처리 합니다. 주석 처리 한 코드 뒤에 다음 코드를 추가 합니다.

```
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
```

1. 프로젝트를 빌드하고 프로그램을 실행 합니다.

## <a name="see-also"></a>참고 항목

[리본 디자이너 (MFC)](ribbon-designer-mfc.md)
