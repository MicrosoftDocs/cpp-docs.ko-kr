---
description: Document-Template 클래스에 대해 자세히 알아보세요.
title: 문서 템플릿 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
ms.openlocfilehash: f9e67cc8f6a115345f6b1f42c2064fcbed7be47e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330276"
---
# <a name="document-template-classes"></a>문서 템플릿 클래스

문서 템플릿 개체는 새 문서 또는 뷰가 만들어질 때 문서, 뷰 및 프레임 창 개체의 생성을 조정 합니다.

[CDocTemplate](reference/cdoctemplate-class.md)<br/>
문서 템플릿의 기본 클래스입니다. 이 클래스는 직접 사용 하지 않습니다. 대신이 클래스에서 파생 된 다른 문서 템플릿 클래스 중 하나를 사용 합니다.

[CMultiDocTemplate](reference/cmultidoctemplate-class.md)<br/>
MDI (다중 문서 인터페이스)의 문서에 대 한 템플릿입니다. MDI 응용 프로그램은 한 번에 여러 문서를 열 수 있습니다.

[CSingleDocTemplate](reference/csingledoctemplate-class.md)<br/>
SDI (단일 문서 인터페이스)의 문서에 대 한 템플릿입니다. SDI 응용 프로그램은 한 번에 하나의 문서만 열려 있습니다.

## <a name="related-class"></a>관련 클래스

[CCreateContext](reference/ccreatecontext-structure.md)<br/>
문서, 뷰 및 프레임 창 개체 만들기를 조정 하기 위해 문서 템플릿이 창 생성 함수에 전달 하는 구조체입니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](class-library-overview.md)
