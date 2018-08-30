---
title: GDI 리소스 할당 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0f7923d36abcd0e9f6b7cb9e97072f5782178919
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208050"
---
# <a name="allocating-gdi-resources"></a>GDI 리소스 할당
이 문서에서는 인쇄에 필요한 Windows GDI(그래픽 장치 인터페이스) 개체를 할당 및 할당 취소하는 방법을 설명합니다.  
  
> [!NOTE]
>  자세한 내용은 GDI + SDK 설명서를 참조 하세요. [ https://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/GDIPlus/GDIPlus.asp ](https://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/gdiplus/gdiplus.asp)합니다.  
  
 화면 표시가 아니라 인쇄를 위해 특정 글꼴, 펜 또는 기타 GDI 개체를 사용해야 한다고 가정합니다. 필요한 메모리 때문에 응용 프로그램이 시작될 때 이러한 개체를 할당하는 것은 비효율적입니다. 응용 프로그램이 문서를 인쇄하지 않는 경우 해당 메모리가 다른 용도에 필요할 수 있습니다. 인쇄가 시작될 때 할당한 후 인쇄가 끝나면 삭제하는 것이 좋습니다.  
  
 이러한 GDI 개체를 할당 하려면 재정의 [OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting) 멤버 함수입니다. 이 함수는 두 가지 이유로이 용도에 적합: 프레임 워크를이 함수를 호출 되 면 각 인쇄 작업의와 다르게 부분 [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting),이 함수에 대 한 액세스에는 [CDC](../mfc/reference/cdc-class.md) 프린터 장치 드라이버를 나타내는 개체입니다. GDI 개체를 가리키는 뷰 클래스에 멤버 변수를 정의 하 여 인쇄 작업 하는 동안 사용 하기 위해 이러한 개체를 저장할 수 있습니다 (예를 들어 `CFont *` 멤버 및 등).  
  
 프린터 장치 컨텍스트로 선택 만든 GDI 개체를 사용 하 여 [OnPrint](../mfc/reference/cview-class.md#onprint) 멤버 함수입니다. 문서의 다른 페이지에 대 한 다양 한 GDI 개체가 필요한 경우를 검사할 수 있습니다 합니다 `m_nCurPage` 의 멤버는 [CPrintInfo](../mfc/reference/cprintinfo-structure.md) 구조체이 고 GDI 개체를 적절 하 게 선택 합니다. 연속하는 여러 페이지에 대한 GDI 개체가 필요한 경우 Windows에서 `OnPrint`가 호출될 때마다 장치 컨텍스트로 선택해야 합니다.  
  
 이러한 GDI 개체 할당을 취소 하려면 재정의 [OnEndPrinting](../mfc/reference/cview-class.md#onendprinting) 멤버 함수입니다. 각 인쇄 작업이 끝날 때 프레임워크에서 이 함수를 호출하여, 응용 프로그램이 다른 작업에 반환되기 전에 인쇄와 관련된 GDI 개체 할당을 취소할 수 있는 기회를 제공합니다.  
  
## <a name="see-also"></a>참고 항목  
 [인쇄](../mfc/printing.md)   
 [기본 인쇄가 수행되는 방법](../mfc/how-default-printing-is-done.md)

