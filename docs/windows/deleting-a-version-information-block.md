---
title: 버전 정보 블록 (c + +)를 삭제 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.version
dev_langs:
- C++
helpviewer_keywords:
- blocks, deleting
- version information, deleting blocks
- resources [C++], deleting version information
ms.assetid: 4e1641eb-d5b2-4183-b273-bc5b51af1537
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6951904f0a579017c5a5a76f7fd8ba798017a34b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425056"
---
# <a name="deleting-a-version-information-block-c"></a>버전 정보 블록 (c + +)를 삭제합니다.

### <a name="to-delete-a-version-information-block"></a>버전 정보 블록을 삭제하려면

1. [리소스 뷰](../windows/resource-view-window.md)에서 해당 아이콘을 두 번 클릭하여 버전 정보 리소스를 엽니다.

   > [!NOTE]
   > 프로젝트에 .rc 파일이 아직 없는 경우 [새 리소스 스크립트 파일 만들기](../windows/how-to-create-a-resource-script-file.md)를 참조하세요.

2. 삭제하려는 블록 헤더를 마우스 오른쪽 단추로 클릭한 후 바로 가기 메뉴에서 **버전 정보 블록 삭제** 를 선택합니다.

   이 명령은 선택한 헤더를 삭제하고 나머지 버전 정보를 그대로 둡니다. 이 작업은 실행 취소할 수 없습니다.

관리 되는 프로젝트에 리소스를 추가 하는 방법에 대 한 정보를 참조 하세요 [데스크톱 앱의 리소스](/dotnet/framework/resources/index) 에 *.NET Framework Developer's Guide*합니다. 수동으로 관리 되는 프로젝트에 리소스 파일을 추가, 리소스 액세스, 정적 리소스 표시 및 속성에 리소스 문자열 할당에 대 한 내용은 참조 하세요 [데스크톱 앱에 대 한 리소스 파일 만들기](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)합니다. 전역화 및 지역화 관리 되는 앱의 리소스에 대 한 내용은 참조 하세요 [Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)합니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[버전 정보 편집기](../windows/version-information-editor.md)<br/>
[버전 정보 (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)