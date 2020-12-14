---
description: '자세히 알아보기: 대화 상자 초기화'
title: 대화 상자 초기화
ms.date: 11/04/2016
helpviewer_keywords:
- initializing dialog boxes [MFC]
- OnInitDialog method [MFC]
- modal dialog boxes [MFC], initializing
- modeless dialog boxes [MFC], initializing
- MFC dialog boxes [MFC], initializing
ms.assetid: 968142f5-19f9-4b34-a1d4-8e6412d4379b
ms.openlocfilehash: 317098a8c0cc745bbd4c94b9ed02401774cb0df9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197623"
---
# <a name="initializing-the-dialog-box"></a>대화 상자 초기화

대화 상자와 모든 컨트롤이 만들어졌지만 화면에 대화 상자를 표시 하기 바로 전에 대화 상자 개체의 [OnInitDialog](reference/cdialog-class.md#oninitdialog) 멤버 함수가 호출 됩니다. 모달 대화 상자의 경우이는 호출 중에 발생 `DoModal` 합니다. 모덜리스 대화 상자의 경우 `OnInitDialog` 가 호출 될 때가 호출 됩니다 `Create` . 일반적으로를 재정의 `OnInitDialog` 하 여 편집 상자의 초기 텍스트를 설정 하는 것과 같은 대화 상자의 컨트롤을 초기화 합니다. `OnInitDialog`재정의에서 기본 클래스의 멤버 함수를 호출 해야 합니다 `CDialog` `OnInitDialog` .

대화 상자의 배경색 및 응용 프로그램의 다른 모든 대화 상자를 설정 하려면 [대화 상자의 배경색 설정](setting-the-dialog-boxs-background-color.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC에서 대화 상자를 통해 작업](life-cycle-of-a-dialog-box.md)
