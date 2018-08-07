---
title: '방법: 리소스 스크립트 파일 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rc files, creating
- .rc files, creating
- resource script files, creating
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ed35392180d0531133413a54ca2190ed65519546
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570576"
---
# <a name="how-to-create-a-resource-script-file"></a>방법: 리소스 스크립트 파일 만들기
> [!NOTE]
>  Express 버전에서는 리소스 편집기를 사용할 수 없습니다.  
>   
>  이 자료는 Windows 데스크톱 응용 프로그램에 적용됩니다. .NET 언어의 프로젝트에서는 리소스 스크립트 파일을 사용하지 않습니다. 자세한 내용은 [리소스 파일](../windows/resource-files-visual-studio.md)을 참조하세요.  
  
### <a name="to-create-a-new-resource-script-rc-file"></a>새 리소스 스크립트(.rc) 파일을 만들려면  
  
1.  기존 프로젝트 폴더에 포커스를 둡니다 **솔루션 탐색기**, 예를 들어, "MyProject"로 지정 합니다.  
  
    > [!NOTE]
    >  솔루션 탐색기에서 솔루션 폴더와 프로젝트 폴더를 혼동하지 마세요. 에 포커스를 둔 경우는 **솔루션** 폴더, 선택 항목을 **새 항목 추가** 대화 상자 (3 단계) 다른 됩니다.  
  
2.  **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.  
  
3.  **새 항목 추가** 대화 상자에서 **Visual C++** 폴더를 클릭한 후 오른쪽 창에서 **리소스 파일(.rc)** 을 선택합니다.  
  
4.  **이름** 텍스트 상자에서 리소스 스크립트 파일의 이름을 지정한 후 **열기**를 클릭합니다.  
  
 이제 .rc 파일을 [생성](../windows/how-to-create-a-resource.md) 하여 새 리소스를 추가할 수 있습니다.  
  
> [!NOTE]
>  Visual Studio IDE에 로드된 기존 프로젝트에만 리소스 스크립트(.rc 파일)를 추가할 수 있습니다. 프로젝트의 외부에 독립 실행형 .rc 파일을 만들 수 없습니다. [리소스 템플릿](../windows/how-to-use-resource-templates.md) (.rct 파일)은 언제든지 만들 수 있습니다.


## <a name="requirements"></a>요구 사항  
  
Win32  
  
## <a name="see-also"></a>참고 항목  
 [리소스 파일](../windows/resource-files-visual-studio.md)   
 [리소스 편집기](../windows/resource-editors.md)
