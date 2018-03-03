---
title: "OLE 끌어서 놓기 및 데이터 전송 클래스 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.ole
dev_langs:
- C++
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE drag and drop [MFC], and data transfer classes
- drag and drop [MFC], classes
- data transfer [MFC], OLE
- data transfer classes [MFC]
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0e8c5a54184bcf6450bf39b39a6b90d7865c09d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>OLE 끌어서 놓기 및 데이터 전송 클래스
이러한 클래스는 OLE 데이터 전송에 사용 됩니다. 클립보드를 사용 하 여 또는 끌어서 통해 응용 프로그램 및 drop 간에 전달할 데이터를 허용 합니다.  
  
 [COleDropSource](../mfc/reference/coledropsource-class.md)  
 처음부터 끝까지 끌어서 놓기 작업을 제어 합니다. 이 클래스는 끌기 작업을 시작 및 종료 될 때 결정 합니다. 또한 커서 피드백을 끌어서 놓기 작업 동안 표시 됩니다.  
  
 [COleDataSource](../mfc/reference/coledatasource-class.md)  
 응용 프로그램은 데이터 전송에 대 한 데이터를 제공 하는 경우 사용 합니다. `COleDataSource`개체 지향 클립보드 개체로 볼 수 없습니다.  
  
 [COleDropTarget](../mfc/reference/coledroptarget-class.md)  
 끌어서 놓기 작업의 대상을 나타냅니다. A `COleDropTarget` 화면의 창에 해당 하는 개체입니다. 데이터 검색 놓여진 하며 실제 삭제 작업을 허용할지 여부를 결정 합니다.  
  
 [COleDataObject](../mfc/reference/coledataobject-class.md)  
 수신기 측면으로 사용 `COleDataSource`합니다. `COleDataObject`개체를 제공 하 여 저장 된 데이터에 대 한 액세스는 `COleDataSource` 개체입니다.  
  
## <a name="see-also"></a>참고 항목  
 [클래스 개요](../mfc/class-library-overview.md)

