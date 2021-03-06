---
description: '자세히 알아보기: TN020: ID 명명 및 번호 매기기 규칙'
title: 'TN020: ID 명명 및 번호 매기기 규칙'
ms.date: 11/04/2016
f1_keywords:
- vc.id
helpviewer_keywords:
- TN020
- resource identifiers, naming and numbering
- resource identifiers
ms.assetid: aecbd2cf-68b3-47f6-ae21-b1f507917245
ms.openlocfilehash: 85f59e45ec9d4ce748515cf638f4fb4cf33c7d38
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215874"
---
# <a name="tn020-id-naming-and-numbering-conventions"></a>TN020: ID 명명 및 번호 매기기 규칙

이 참고에서는 MFC 2.0에서 리소스, 명령, 문자열, 컨트롤 및 자식 창에 사용 하는 ID 명명 및 번호 매기기 규칙을 설명 합니다.

MFC ID 명명 및 번호 매기기 규칙은 다음 요구 사항을 충족 하기 위한 것입니다.

- Visual C++ 리소스 편집기에서 지원 되는 mfc 라이브러리 및 MFC 응용 프로그램에서 사용 되는 일관 된 ID 이름 지정 표준을 제공 합니다. 이를 통해 프로그래머는 리소스의 형식 및 출처를 해당 ID에서 보다 쉽게 해석할 수 있습니다.

- 특정 Id 유형 간의 강력한 일대일 관계를 강조 합니다.

- Windows에서 Id를 명명 하는 데 널리 사용 되는 표준을 준수 합니다.

- ID 번호 지정 공간을 분할 합니다. ID 번호는 프로그래머, MFC, Windows 및 Visual C++ 편집 리소스에서 할당할 수 있습니다. 적절 한 분할은 ID 번호의 중복을 방지 하는 데 도움이 됩니다.

## <a name="the-id-prefix-naming-convention"></a>ID 접두사 명명 규칙

응용 프로그램에서 여러 유형의 Id가 발생할 수 있습니다. MFC ID 명명 규칙은 다양 한 리소스 형식에 대해 서로 다른 접두사를 정의 합니다.

MFC는 "IDR_" 접두사를 사용 하 여 여러 리소스 형식에 적용 되는 리소스 ID를 표시 합니다. 예를 들어, 지정 된 프레임 창의 경우 MFC는 동일한 "IDR_" 접두사를 사용 하 여 메뉴, 액셀러레이터, 문자열 및 아이콘 리소스를 표시 합니다. 다음 표에서는 다양 한 접두사 및 사용법을 보여 줍니다.

|접두사|기능|
|------------|---------|
|IDR_|여러 리소스 종류 (주로 메뉴, 액셀러레이터 및 리본에 사용 됨)|
|IDD_|대화 상자 템플릿 리소스의 경우 (예: IDD_DIALOG1).|
|IDC_|커서 리소스의 경우|
|IDI_|아이콘 리소스의 경우.|
|IDB_|비트맵 리소스의 경우.|
|IDS_|문자열 리소스의 경우|

대화 상자 리소스 내에서 MFC는 다음 규칙을 따릅니다.

|접두사 또는 레이블|기능|
|---------------------|---------|
|IDOK, IDCANCEL|표준 푸시 단추 Id의 경우입니다.|
|IDC_|다른 대화 상자 컨트롤의 경우입니다.|

"IDC_" 접두사는 커서에도 사용 됩니다. 일반적으로 일반적인 응용 프로그램에는 몇 개의 커서와 많은 대화 상자 컨트롤이 있기 때문에이 명명 충돌은 일반적으로 문제가 되지 않습니다.

메뉴 리소스 내에서 MFC는 다음 규칙을 따릅니다.

|접두사|기능|
|------------|---------|
|IDM_|MFC 명령 아키텍처를 사용 하지 않는 메뉴 항목|
|ID_|MFC 명령 아키텍처를 사용 하는 메뉴 명령|

MFC 명령 아키텍처를 따르는 명령에는 ON_COMMAND 명령 처리기가 있어야 하며 ON_UPDATE_COMMAND_UI 처리기를 사용할 수 있습니다. 이러한 명령 처리기가 MFC 명령 아키텍처를 따르는 경우 메뉴 명령, 도구 모음 단추 또는 대화 상자 표시줄 단추에 바인딩되어 있는지 여부와 관계 없이 제대로 작동 합니다. 프로그램의 메시지 표시줄에 표시 되는 메뉴 프롬프트 문자열에도 동일한 "ID_" 접두사가 사용 됩니다. 응용 프로그램에서 대부분의 메뉴 항목은 MFC 명령 규칙을 따라야 합니다. 표준 명령 Id (예: ID_FILE_NEW)는 모두이 규칙을 따릅니다.

MFC는 "IDS_" 대신 특수 한 형태의 문자열로 "IDP_"도 사용 합니다. "IDP_" 접두사가 있는 문자열에는 메시지 상자에 사용 되는 문자열이 표시 됩니다. "IDP_" 문자열은 "%1"과 (와) "%2"을 (를) 프로그램에 의해 결정 된 문자열의 자리 표시자로 포함할 수 있습니다. "IDP_" 문자열은 일반적으로 관련 도움말 항목을 포함 하며 "IDS_" 문자열은 그렇지 않습니다. "IDP_" 문자열은 항상 지역화 되며 "IDS_" 문자열은 지역화 되지 않을 수 있습니다.

또한 MFC 라이브러리는 "IDW_" 접두사를 "IDC_" 대신 특수 한 형태의 컨트롤 Id로 사용 합니다. 이러한 Id는 프레임 워크 클래스에의 한 뷰 및 분할자와 같은 자식 창에 할당 됩니다. MFC 구현 Id에는 "AFX_" 접두사가 붙습니다.

## <a name="the-id-numbering-convention"></a>ID-Numbering 규칙

다음 표에서는 특정 형식의 Id에 대 한 유효한 범위를 나열 합니다. 몇 가지 제한 사항은 기술 구현 제한이 며, 다른 일부는 Id가 Windows 미리 정의 된 Id 또는 MFC 기본 구현과 충돌 하지 않도록 설계 된 규칙입니다.

권장 범위 내에서 모든 Id를 정의 하는 것이 좋습니다. 0이 사용 되지 않으므로 이러한 범위의 하한값은 1입니다. 일반적인 규칙을 사용 하 고 첫 번째 ID로 100 또는 101를 사용 하는 것이 좋습니다.

|접두사|리소스 유형|유효 범위|
|------------|-------------------|-----------------|
|IDR_|multiple|1 ~ 0x6FFF|
|IDD_|대화 상자 템플릿|1 ~ 0x6FFF|
|IDC_, IDI_, IDB_|커서, 아이콘, 비트맵|1 ~ 0x6FFF|
|IDS_, IDP_|일반 문자열|1 ~ 0x7FFF|
|ID_|명령|0x8000 ~ 0xDFFF|
|IDC_|controls|8 ~ 0xDFFF|

이러한 범위 제한이 적용 되는 이유는 다음과 같습니다.

- 규칙에 따라 ID 값 0이 사용 되지 않습니다.

- Windows 구현 제한은 진정한 리소스 Id를 0x7FFF 보다 작거나 같도록 제한 합니다.

- MFC의 내부 프레임 워크는 다음과 같은 범위를 예약 합니다.

  - 0x7000 ~ 0x7FFF (afxres.h 참조)

  - 0xE000 ~ 0xEFFF (afxres.h 참조)

  - 16000 ~ 18000 (afxribbonres 참조)

  이러한 범위는 이후 MFC 구현에서 변경 될 수 있습니다.

- 여러 Windows 시스템 명령에는 0xF000부터 0xFFFF 까지의 범위가 사용 됩니다.

- 1 ~ 7의 컨트롤 Id는 IDOK 및 IDCANCEL와 같은 표준 컨트롤용으로 예약 되어 있습니다.

- 문자열의 0x8000 ~ 0xFFFF의 범위는 명령에 대 한 메뉴 프롬프트를 위해 예약 됩니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
