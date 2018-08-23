---
title: 여러 문자열의 Caption 속성 변경 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- String editor, changing properties of multiple strings
- strings [C++], changing caption property of multiple
- string editing, string tables
- string tables, changing caption of multiple strings
ms.assetid: 82ac4389-fd9c-4794-a18f-c6bf5b253bd7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 205fbd0674fa1a64ee6aeb66edfecdc1861ccba7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42578374"
---
# <a name="changing-the-caption-property-of-multiple-strings"></a>여러 문자열의 Caption 속성 변경

다음 절차는 여러 문자열의 caption 속성을 변경 하는 방법을 보여 줍니다.

### <a name="to-change-the-caption-property-of-multiple-strings"></a>여러 문자열의 caption 속성을 변경 하려면

1. 문자열 테이블에서 해당 아이콘을 두 번 클릭 하 여 [리소스 뷰](../windows/resource-view-window.md)합니다.

   > [!NOTE]
   > 프로젝트에 .rc 파일이 아직 없는 경우 [새 리소스 스크립트 파일 만들기](../windows/how-to-create-a-resource-script-file.md)를 참조하세요.

2. 누른 변경 하려는 문자열을 선택 합니다 **Ctrl** 각각 클릭 하면 키입니다.

3. 에 [속성 창](/visualstudio/ide/reference/properties-window), 변경할 속성에 대 한 새 값을 입력 합니다.

4. **Enter** 키를 누릅니다.

(대상으로 하는 공용 언어 런타임) 관리 되는 프로젝트에 리소스를 추가 하는 방법에 대 한 정보를 참조 하세요 [데스크톱 앱의 리소스](/dotnet/framework/resources/index) 에 *.NET Framework Developer's Guide*합니다. 수동으로 관리 되는 프로젝트에 리소스 파일을 추가, 리소스 액세스, 정적 리소스 표시 및 속성에 리소스 문자열 할당에 대 한 내용은 참조 하세요 [연습: Windows Forms 지역화](http://msdn.microsoft.com/9a96220d-a19b-4de0-9f48-01e5d82679e5) 고[연습: ASP.NET에서 지역화에 리소스를 사용 하 여](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)입니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[문자열 편집기](../windows/string-editor.md)  