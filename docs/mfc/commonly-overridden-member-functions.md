---
title: 일반적으로 재정의되는 멤버 함수
ms.date: 09/06/2019
helpviewer_keywords:
- CDialog class [MFC], members
- OnInitDialog function
- dialog classes [MFC], commonly overridden member functions
- OnCancel function
- overriding, dialog class members
- OnOK function
- MFC dialog boxes [MFC], overriding member functions
ms.assetid: 78eb566c-e361-4c86-8db5-c7e2791b249a
ms.openlocfilehash: 51a647bb50415af71d6d148d3139f906f503ee2a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685819"
---
# <a name="commonly-overridden-member-functions"></a>일반적으로 재정의되는 멤버 함수

다음 표에서는 파생 클래스에서 `CDialog`재정의할 수 있는 가장 가능성이 높은 멤버 함수를 보여 줍니다.

### <a name="commonly-overridden-member-functions-of-class-cdialog"></a>CDialog 클래스의 일반적으로 재정의 되는 멤버 함수

|멤버 함수|응답 하는 메시지|재정의 목적|
|---------------------|----------------------------|-----------------------------|
|`OnInitDialog`|**WM_INITDIALOG**|대화 상자의 컨트롤을 초기화 합니다.|
|`OnOK`|**BN_CLICKED** button **IDOK**|사용자가 확인 단추를 클릭할 때 응답 합니다.|
|`OnCancel`|**BN_CLICKED** button **IDCANCEL**|사용자가 [취소] 단추를 클릭할 때 응답 합니다.|

`OnInitDialog`, `OnOK` 및`OnCancel` 는 가상 함수입니다. 이를 재정의 하려면 [MFC 클래스 마법사](reference/mfc-class-wizard.md)를 사용 하 여 파생 된 대화 상자 클래스에서 재정의 함수를 선언 합니다.

`OnInitDialog`는 대화 상자가 표시 되기 직전에 호출 됩니다. 일반적으로 처리기의 첫 `OnInitDialog` 번째 작업으로 재정의에서 기본 처리기를 호출 해야 합니다. 기본적 `OnInitDialog` 으로는 포커스를 대화 상자의 첫 번째 컨트롤로 설정 해야 함을 나타내려면 **TRUE** 를 반환 합니다.

`OnOK`는 일반적으로 모달 대화 상자가 아닌 모덜리스에 대해 재정의 됩니다. 모달 대화 상자에 대해이 처리기를 재정의 하는 경우 `EndDialog` 가 호출 되도록 재정의에서 기본 클래스 버전을 호출 하거나 직접 호출 `EndDialog` 합니다.

`OnCancel`는 일반적으로 모덜리스 대화 상자에 대해 재정의 됩니다.

이러한 멤버 함수에 대 한 자세한 내용은 mfc *참조* 의 [CDIALOG](../mfc/reference/cdialog-class.md) 클래스 및 [mfc에서 대화 상자를 사용 하](../mfc/life-cycle-of-a-dialog-box.md)는 방법에 대 한 설명을 참조 하세요.

## <a name="see-also"></a>참조

[대화 상자](../mfc/dialog-boxes.md)<br/>
[일반적으로 추가되는 멤버 함수](../mfc/commonly-added-member-functions.md)
