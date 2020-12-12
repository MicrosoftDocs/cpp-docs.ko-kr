---
description: '자세한 정보: 액티브 문서 포함의 예: Office 바인더'
title: '액티브 문서 포함의 예: Office Binder'
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- examples [MFC], active document containment
- containers [MFC], active document
- active document containers [MFC], examples
- Office Binder [MFC]
- MFC COM, active document containment
ms.assetid: 70dd8568-e8bc-44ac-bf5e-678767efe8e3
ms.openlocfilehash: 075922f3a50df77f83aab90dc380e33f703737fd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290832"
---
# <a name="example-of-active-document-containment-office-binder"></a>액티브 문서 포함의 예: Office Binder

Microsoft Office 바인더는 액티브 문서 컨테이너의 예입니다. Office 바인더에는 일반적으로 컨테이너 처럼 두 개의 주 창이 포함 되어 있습니다. 왼쪽 창에는 바인더의 활성 문서에 해당 하는 아이콘이 있습니다. 각 문서를 바인더 내의 *섹션* 이라고 합니다. 예를 들어 바인더는 Word 문서, PowerPoint 파일, Excel 스프레드시트 등을 포함할 수 있습니다.

왼쪽 창에서 아이콘을 클릭 하면 해당 활성 문서가 활성화 됩니다. 그러면 바인더의 오른쪽 창에 현재 선택한 활성 문서의 내용이 표시 됩니다.

바인더에서 Word 문서를 열고 활성화 하면 Word 메뉴 모음과 도구 모음이 보기 프레임의 맨 위에 나타나고 Word 명령이 나 도구를 사용 하 여 문서 내용을 편집할 수 있습니다. 그러나 메뉴 모음은 바인더와 Word의 메뉴 모음을 조합한 것입니다. Binder와 Word에 모두 **도움말** 메뉴가 있으므로 각 메뉴의 내용이 병합 됩니다. Office 바인더와 같은 액티브 문서 컨테이너는 **도움말** 메뉴 병합을 자동으로 제공 합니다. 자세한 내용은 [도움말 메뉴 병합](help-menu-merging.md)을 참조 하세요.

다른 응용 프로그램 종류의 활성 문서를 선택 하면 바인더의 인터페이스가 활성 문서의 응용 프로그램 형식에 맞게 변경 됩니다. 예를 들어 바인더가 Excel 스프레드시트를 포함 하는 경우 Excel 스프레드시트 섹션을 선택 하면 바인더의 메뉴가 변경 되는 것을 볼 수 있습니다.

물론 바인더 옆에는 다른 가능한 컨테이너 유형도 있습니다. 파일 탐색기는 왼쪽 창에서 트리 컨트롤을 사용 하 여 드라이브 또는 네트워크에 있는 디렉터리의 계층 목록을 표시 하 고 오른쪽 창에는 현재 선택한 디렉터리에 포함 된 파일을 표시 하는 일반적인 이중 창 인터페이스를 사용 합니다. 이중 창 인터페이스를 사용 하는 대신 인터넷 브라우저의 컨테이너 유형 (예: Microsoft Internet Explorer)은 일반적으로 단일 프레임을가지고 있으며 하이퍼링크를 사용 하 여 탐색을 제공 합니다.

## <a name="see-also"></a>참고 항목

[액티브 문서 포함](active-document-containment.md)
