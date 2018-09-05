---
title: '방법: 리소스 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- toolbars [C++], resources
- resource toolbars
- resources [Visual Studio], creating
ms.assetid: aad44914-9145-45a3-a7d8-9de89b366716
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b7c82a55d2cbfba20b80a02dbcf000c85ed10e83
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679795"
---
# <a name="how-to-create-a-resource"></a>방법: 리소스 파일 만들기

> [!NOTE]
> **리소스 뷰** Express 버전에서는 지원 되지 않습니다.

### <a name="to-create-a-new-resource-in-resource-view"></a>리소스 뷰에서 새 리소스를 만들려면

1. .rc 파일에 포커스를 사용 하 여 [리소스 뷰](../windows/resource-view-window.md)를 클릭 합니다 **편집** 메뉴 선택 **리소스 추가** (에서.rc 파일을 마우스 오른쪽 단추로 클릭 **리소스 뷰** 선택한 **리소스 추가** 바로 가기 메뉴에서).

   > [!NOTE] 
   > 프로젝트에 .rc 파일이 아직 없는 경우 [새 리소스 스크립트 파일 만들기](../windows/how-to-create-a-resource-script-file.md)를 참조하세요.

2. [리소스 추가 대화 상자](../windows/add-resource-dialog-box.md)에서 프로젝트에 추가할 리소스 형식을 선택합니다.

### <a name="to-create-a-new-resource-in-solution-explorer"></a>솔루션 탐색기에서 새 리소스를 만들려면

1. **솔루션 탐색기**에서 프로젝트 폴더를 마우스 오른쪽 단추로 클릭하고 **추가**를 선택하고 바로 가기 메뉴에서 **리소스 추가** 를 클릭합니다.

   프로젝트에 .rc 파일이 없으면 이 단계에서 해당 파일을 만듭니다. 그런 다음 이 단계를 반복하여 새.rc 파일에 특정 리소스 형식을 추가할 수 있습니다.

2. [리소스 추가 대화 상자](../windows/add-resource-dialog-box.md)에서 프로젝트에 추가할 리소스 형식을 선택합니다.

### <a name="to-create-a-new-resource-in-class-view"></a>클래스 뷰에서 새 리소스를 만들려면

1. [클래스 뷰](/visualstudio/ide/viewing-the-structure-of-code)클래스를 마우스 오른쪽 단추로 클릭 하 고 선택 **추가**, 클릭 **리소스 추가** 바로 가기 메뉴에서.

2. [리소스 추가 대화 상자](../windows/add-resource-dialog-box.md)에서 프로젝트에 추가할 리소스 형식을 선택합니다.

### <a name="to-create-a-new-resource-from-the-project-menu"></a>프로젝트 메뉴에서 새 리소스를 만들려면

1. **프로젝트** 메뉴에서 **리소스 추가**를 선택합니다.

새 리소스를 만들 때 Visual c + + 고유 이름을 할당, 예를 들어 `IDD_Dialog1`합니다. 연결된 리소스 편집기 또는 [속성 창](/visualstudio/ide/reference/properties-window)에서 리소스에 대한 속성을 편집하여 이 리소스 ID를 사용자 지정할 수 있습니다.

리소스를 새 기본 리소스(템플릿에 기반을 두지 않은 리소스) 또는 [템플릿](../windows/how-to-use-resource-templates.md)을 기반으로 패턴화된 리소스로 만들 수 있습니다.

관리 되는 프로젝트에 리소스를 추가 하는 방법에 대 한 정보를 참조 하세요 [데스크톱 앱의 리소스](/dotnet/framework/resources/index) 에 *.NET Framework Developer's Guide*합니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[리소스 파일](../windows/resource-files-visual-studio.md)  
[리소스 편집기](../windows/resource-editors.md)  
[리소스 추가 대화 상자](../windows/add-resource-dialog-box.md)