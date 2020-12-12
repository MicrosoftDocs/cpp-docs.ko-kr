---
description: '자세한 정보: 방법: 리소스 관리 (c + +)'
title: '방법: 리소스 관리 (c + +)'
ms.date: 02/14/2019
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
- vc.resvw.resource.changing
- vb.xmldesigner.data
- vs.resvw.resource.importing
- vc.resvw.resource.importing
helpviewer_keywords:
- resources [C++], moving between files
- resources [C++], copying
- resource files [C++], copying or moving resources between
- resource files [C++], tiling
- .rc files [C++], copying resources between
- rc files [C++], copying resources between
- Language property [C++]
- .resx files [C++], editing
- resource files [C++], editing
- resx files [C++], editing
- resources [C++], exporting
- graphics [C++], exporting
- graphics [C++], importing
- resources [C++], importing
- bitmaps [C++], importing and exporting
- toolbars [C++], importing
- images [C++], importing
- toolbars [C++], exporting
- cursors [C++], importing and exporting
- images [C++], exporting
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
ms.openlocfilehash: 3720cb5f3ab3b99ecba798abce1e4fdba25f8646
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329383"
---
# <a name="how-to-manage-resources-c"></a>방법: 리소스 관리 (c + +)

## <a name="copy-and-edit-resources"></a>리소스 복사 및 편집

리소스를 변경 하거나 복사 하는 동안 리소스의 언어 또는 조건을 변경 하지 않고 한 파일에서 다른 파일로 리소스를 복사할 수 있습니다.

기존 리소스 또는 실행 파일에서 현재 리소스 파일로 리소스를 쉽게 복사할 수 있습니다. 리소스를 복사 하려면 리소스를 포함 하는 두 파일을 동시에 열고 한 파일에서 다른 파일로 항목을 끌거나 두 파일 간에 복사 하 여 붙여 넣습니다. 이 메서드는 리소스 스크립트 (.rc) 파일 및 리소스 템플릿 (.rct) 파일 및 실행 파일 (.exe)로 작동 합니다.

> [!NOTE]
> Visual C++에는 자체 응용 프로그램에서 사용할 수 있는 샘플 리소스 파일이 포함 되어 있습니다. 자세한 내용은 [클립 아트: 공용 리소스](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general)를 참조 하세요.

프로젝트의 리소스 파일 (**리소스 뷰**)과 독립 실행형 .rc 파일 사이를 끌어서 놓거나, 복사 하거나, 잘라내거나, 붙여 넣을 수는 없습니다. 이전 버전의 제품에서이 작업을 수행할 수 있습니다. 프로젝트 외부에서 열리는 .rc 파일 간에만 끌어서 놓기 메서드를 사용 합니다.

### <a name="to-copy-resources"></a>리소스를 복사 하려면

1. 두 리소스 파일을 모두 독립 실행형으로 엽니다. [리소스 스크립트 파일 사용](how-to-create-a-resource-script-file.md#use-resource-script-files)을 참조 하세요. 예를 들어 *Source1* 및 *소스 2* 를 엽니다.

1. 첫 번째 .rc 파일 내에서 다음 중 하나를 수행 합니다.

   - 끌어서 놓기 방법 사용

      1. 복사할 리소스를 선택 합니다. 예를 들어 *Source1* 에서 **IDD_DIALOG1** 를 선택 합니다.

      1. **Ctrl** 키를 누른 채 리소스를 두 번째 .rc 파일로 끌어 옵니다. 예를 들어 **IDD_DIALOG1** 을 *Source1* 에서 *소스 2* 로 끌어 옵니다.

         > [!TIP]
         > **Ctrl** 키를 누른 채 리소스를 끌면 리소스를 복사 하지 않고 이동 합니다.

   - 복사 및 붙여넣기 방법 사용

      1. 복사할 리소스 (예: *Source1*)를 마우스 오른쪽 단추로 클릭 하 고 **복사** 를 선택 합니다.

      1. 리소스를 붙여 넣을 리소스 파일 (예: *소스 2*)을 마우스 오른쪽 단추로 클릭 하 고 **붙여넣기** 를 선택 합니다.

> [!NOTE]
> 기존 파일에 있는 기호 이름 또는 값과의 충돌을 방지 하기 위해 새 파일에 복사할 때 전송 된 리소스의 기호 값 또는 기호 이름과 값을 변경할 수 Visual C++.

리소스에서 복사하는 동안 언어 속성이나 조건 속성 또는 두 가지 모두를 변경할 수 있습니다.

- 리소스의 언어는 검색 중인 리소스를 식별 하는 데 도움이 되는 [findresource](/windows/win32/api/winbase/nf-winbase-findresourcea) 에서 사용 되는 언어를 지정 합니다. 리소스에는 텍스트와 관련이 없는 각 언어에 대 한 차이가 있을 수 있습니다. 예를 들어 일본어 키보드 에서만 작동 하는 액셀러레이터 나 중국어로 지역화 된 빌드에서만 적절 한 비트맵입니다.

- 리소스의 조건은 리소스의 해당 특정 복사본이 사용되는 조건을 식별하는 정의된 기호입니다.

리소스의 언어와 조건은 **작업 영역** 창의 리소스 이름 뒤에 괄호 안에 표시 됩니다. 여기서는 이라는 리소스를 `IDD_AboutBox` `Finnish` 해당 언어로 사용 하 고 조건이입니다 `XX33` .

```cpp
IDD_AboutBox (Finnish - XX33)
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>기존 리소스를 복사하고 해당 언어 또는 조건을 변경하려면

*.Rc* 파일 또는 [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources) 창에서 복사 하려는 리소스를 마우스 오른쪽 단추로 클릭 하 고 **복사본 삽입** 을 선택 합니다. 그런 후에 다음을 설정 합니다.

- **언어** 목록 상자에서 언어를 선택 합니다.

- **조건** 상자에 조건을 입력 합니다.

### <a name="to-edit-resources"></a>리소스를 편집 하려면

관리 되는 리소스 (.resx) 파일은 XML 파일입니다. **새 항목 추가** 대화 상자에서 관리 되는 리소스 파일을 프로젝트에 추가 하면 기본적으로 **관리 되는 리소스 편집기** 가 열립니다.

## <a name="import-and-export-resources"></a>리소스 가져오기 및 내보내기

Visual C++에서 사용하도록 그래픽 리소스(비트맵, 아이콘, 커서 및 도구 모음), HTML 파일 및 사용자 지정 리소스를 가져올 수 있습니다. Visual Studio c + + 프로젝트에서 동일한 형식의 파일을 개발 환경 외부에서 사용할 수 있는 별도의 파일로 내보낼 수 있습니다.

> [!NOTE]
> 액셀러레이터 키, 대화 상자, 문자열 테이블 등의 리소스 유형은 독립 실행형 파일 유형이 아니기 때문에 가져오거나 내보낼 수 없습니다.

### <a name="to-import-a-resource-into-the-resource-script-file"></a>리소스를 리소스 스크립트 파일로 가져오려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources) 에서 리소스를 추가 하려는 리소스 스크립트 (.rc) 파일의 노드를 마우스 오른쪽 단추로 클릭 하 고 **가져오기** 를 선택 합니다.

1. 비트맵 (.bmp), 아이콘 (.ico), 커서 (.cur), html 파일 (.htm) 또는 가져올 기타 파일의 파일 이름을 찾아 선택 합니다.

1. **확인** 을 선택 하 여 리소스 스크립트 파일에 리소스를 추가 합니다.

> [!NOTE]
> 가져오기 프로세스는 선택한 리소스 종류에 관계 없이 동일 하 게 작동 합니다. 가져온 리소스는 해당 리소스 유형의 올바른 노드에 자동으로 추가 됩니다.

### <a name="to-export-a-resource-for-use-outside-of-visual-c"></a>Visual C++ 외부에서 사용할 리소스를 내보내려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 내보낼 리소스를 마우스 오른쪽 단추로 클릭 하 고 **내보내기** 를 선택 합니다. 현재 파일 이름을 그대로 적용 하거나 새 이름을 입력할 수 있습니다.

1. 파일을 저장 하려는 폴더로 이동 하 고 **내보내기** 를 선택 합니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[리소스 파일](../windows/resource-files-visual-studio.md)<br/>
[방법: 리소스 만들기](../windows/how-to-create-a-resource-script-file.md)<br/>
[방법: 컴파일 타임에 리소스 포함](../windows/how-to-include-resources-at-compile-time.md)
