---
description: '자세히 알아보기: 인쇄 및 인쇄 미리 보기'
title: 인쇄 및 인쇄 미리 보기
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC]
- previewing printing
- printing [MFC]
- print preview
- printing [MFC], print preview
ms.assetid: d15059cd-32de-4450-95f7-e73aece238f6
ms.openlocfilehash: 57dfd8eed1719b17f776a62273c9afa9ff5e80f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205839"
---
# <a name="printing-and-print-preview"></a>인쇄 및 인쇄 미리 보기

MFC는 [CView](reference/cview-class.md)클래스를 통해 프로그램의 문서에 대 한 인쇄 및 인쇄 미리 보기를 지원 합니다. 기본 인쇄 및 인쇄 미리 보기의 경우 보기 클래스의 [OnDraw](reference/cview-class.md#ondraw) 멤버 함수를 재정의 하면 됩니다. 이 함수는 화면의 보기, 실제 프린터의 프린터 장치 컨텍스트 또는 화면에서 프린터를 시뮬레이트하는 장치 컨텍스트에 그릴 수 있습니다.

또한 여러 페이지 문서 인쇄 및 미리 보기를 관리 하는 코드를 추가 하 고 인쇄 된 문서의 페이지를 표시 하 고 머리글 및 바닥글을 추가할 수 있습니다.

이 문서 패밀리에서는 MFC 라이브러리 (MFC)에서 인쇄를 구현 하는 방법 및 프레임 워크에 이미 기본 제공 되는 인쇄 아키텍처를 활용 하는 방법에 대해 설명 합니다. 또한 MFC에서 인쇄 미리 보기 기능을 쉽게 구현 하는 방법과이 기능을 사용 하 고 수정 하는 방법을 설명 합니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [인쇄](printing.md)

- [인쇄 미리 보기 아키텍처](print-preview-architecture.md)

- [샘플](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>참고 항목

[사용자 인터페이스 요소](user-interface-elements-mfc.md)
