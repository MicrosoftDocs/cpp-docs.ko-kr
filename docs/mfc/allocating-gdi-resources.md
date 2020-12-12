---
description: '자세한 정보: GDI 리소스 할당'
title: GDI 리소스 할당
ms.date: 06/03/2019
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
ms.openlocfilehash: 348f1ca1eadc22dfc8ca6faa6c31bb2f8d81e51e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176810"
---
# <a name="allocating-gdi-resources"></a>GDI 리소스 할당

이 문서에서는 인쇄에 필요한 Windows GDI(그래픽 디바이스 인터페이스) 개체를 할당 및 할당 취소하는 방법을 설명합니다.

> [!NOTE]
> 자세한 내용은 [Gdi + SDK 설명서](/windows/win32/gdiplus/-gdiplus-gdi-start)를 참조 하세요.

화면 표시가 아니라 인쇄를 위해 특정 글꼴, 펜 또는 기타 GDI 개체를 사용해야 한다고 가정합니다. 필요한 메모리 때문에 애플리케이션이 시작될 때 이러한 개체를 할당하는 것은 비효율적입니다. 애플리케이션이 문서를 인쇄하지 않는 경우 해당 메모리가 다른 용도에 필요할 수 있습니다. 인쇄가 시작될 때 할당한 후 인쇄가 끝나면 삭제하는 것이 좋습니다.

이러한 GDI 개체를 할당 하려면 [Onbeginprinting](reference/cview-class.md#onbeginprinting) 멤버 함수를 재정의 합니다. 이 함수는 다음과 같은 두 가지 이유로이 목적에 매우 적합 합니다. 프레임 워크는 각 인쇄 작업이 시작 될 때이 함수를 한 번 호출 하 고, [Onprepareprinting](reference/cview-class.md#onprepareprinting)와 달리이 함수는 프린터 장치 드라이버를 나타내는 [CDC](reference/cdc-class.md) 개체에 액세스할 수 있습니다. 멤버 등의 GDI 개체를 가리키는 뷰 클래스의 멤버 변수를 정의 하 여 인쇄 작업 중에 사용할 개체를 저장할 수 있습니다 `CFont *` .

만든 GDI 개체를 사용 하려면 [OnPrint](reference/cview-class.md#onprint) 멤버 함수의 프린터 장치 컨텍스트로 선택 합니다. 문서의 각 페이지에 대해 다른 GDI 개체가 필요한 경우 `m_nCurPage` [Cprintinfo](reference/cprintinfo-structure.md) 구조체의 멤버를 검사 하 고 그에 따라 gdi 개체를 선택할 수 있습니다. 연속하는 여러 페이지에 대한 GDI 개체가 필요한 경우 Windows에서 `OnPrint`가 호출될 때마다 디바이스 컨텍스트로 선택해야 합니다.

이러한 GDI 개체의 할당을 취소 하려면 [OnEndPrinting](reference/cview-class.md#onendprinting) 멤버 함수를 재정의 합니다. 각 인쇄 작업이 끝날 때 프레임워크에서 이 함수를 호출하여, 애플리케이션이 다른 작업에 반환되기 전에 인쇄와 관련된 GDI 개체 할당을 취소할 수 있는 기회를 제공합니다.

## <a name="see-also"></a>참고 항목

[인쇄](printing.md)<br/>
[기본 인쇄를 수행 하는 방법](how-default-printing-is-done.md)
