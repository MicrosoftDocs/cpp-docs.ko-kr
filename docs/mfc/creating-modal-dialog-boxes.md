---
description: '자세한 정보: 모달 대화 상자 만들기'
title: 모달 대화 상자 만들기
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
ms.openlocfilehash: 82fa10c65161df98ea3d377e302c0fb787feb14c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309799"
---
# <a name="creating-modal-dialog-boxes"></a>모달 대화 상자 만들기

모달 대화 상자를 만들려면 [CDialog](reference/cdialog-class.md)에 선언 된 두 공용 생성자 중 하나를 호출 합니다. 그런 다음 dialog 개체의 [DoModal](reference/cdialog-class.md#domodal) 멤버 함수를 호출 하 여 대화 상자를 표시 하 고 사용자가 확인 또는 취소를 선택할 때까지 대화 상자와의 상호 작용을 관리 합니다. 이 관리는 `DoModal`을 사용하여 대화 상자 모달을 만듭니다. 모달 대화 상자에 대해 `DoModal`에서는 대화 상자 리소스를 로드합니다.

## <a name="see-also"></a>참고 항목

[MFC에서 대화 상자를 통해 작업](life-cycle-of-a-dialog-box.md)
