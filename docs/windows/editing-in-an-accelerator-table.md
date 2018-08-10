---
title: 액셀러레이터 키 테이블에서 편집 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], editing
- keyboard shortcuts [C++], editing in an accelerator table
ms.assetid: 545b650b-4f26-4b20-8431-d942548443bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b0844ab8a4233e2204c42a8d165309c89026fb01
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646230"
---
# <a name="editing-in-an-accelerator-table"></a>액셀러레이터 키 테이블에서 편집
### <a name="to-edit-in-an-accelerator-table"></a>액셀러레이터 키 테이블에서 편집하려면  
  
1.  액셀러레이터 키 테이블에서 해당 아이콘을 두 번 클릭 하 여 [리소스 뷰](../windows/resource-view-window.md)합니다.  
  
    > [!NOTE]
    >  프로젝트에 .rc 파일이 아직 없는 경우 [새 리소스 스크립트 파일 만들기](../windows/how-to-create-a-resource-script-file.md)를 참조하세요.  
  
2.  테이블에서 항목을 선택하고 클릭하여 바로 편집을 활성화합니다.  
  
3.  드롭다운 콤보 상자에서 선택하거나 현재 위치에서 입력하여 변경합니다.  
  
    -   에 대 한 [ID](id-property.md)목록 또는 편집 하는 형식 중에서 선택 합니다.  
  
    -   에 대 한 [한정자](../windows/accelerator-modifier-property.md)목록 중에서 선택 합니다.  
  
    -   에 대 한 [키](../windows/accelerator-key-property.md)목록 또는 편집 하는 형식 중에서 선택 합니다.  
  
    -   에 대 한 [형식](../windows/accelerator-type-property.md)를 선택 **ASCII** 하거나 **VIRTKEY** 목록에서.  
  
 관리 되는 프로젝트에 리소스를 추가 하는 방법에 대 한 정보를 참조 하세요 [데스크톱 앱의 리소스](/dotnet/framework/resources/index) 에 *.NET Framework Developer's Guide*합니다.  
  
## <a name="requirements"></a>요구 사항  
 Win32  
  
## <a name="see-also"></a>참고 항목  
 [액셀러레이터 키 테이블 편집](../windows/editing-accelerator-tables.md)   
 [액셀러레이터 키 편집기](../windows/accelerator-editor.md)