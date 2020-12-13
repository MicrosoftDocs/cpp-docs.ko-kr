---
description: '자세한 정보: 액티브 문서 포함'
title: 액티브 문서 포함
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- MFC, COM support
- active document containers [MFC], about active document containers
- MFC COM, active document containment
ms.assetid: b8dfa74b-75ce-47df-b75e-fc87b7f7d687
ms.openlocfilehash: 9a190e0203152e2411699aa601a095a530303546
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150386"
---
# <a name="active-document-containment"></a>액티브 문서 포함

액티브 문서 포함은 각 문서 유형에 대해 여러 응용 프로그램 프레임을 만들고 사용 하는 대신 문서를 사용할 수 있는 단일 프레임을 제공 하는 기술입니다. 이는 단일 콘텐츠만 활성화 될 수 있는 복합 문서 내의 포함 된 개체를 OLE에서 사용할 수 있다는 점에서 기본 OLE 기술과 다릅니다. 액티브 문서 포함을 사용 하면 단일 프레임의 컨텍스트 내에서 전체 문서 (즉, 관련 메뉴, 도구 모음 등을 포함 한 전체 응용 프로그램)를 활성화할 수 있습니다.

액티브 문서 포함 기술은 원래 Microsoft Office Office 바인더를 구현 하기 위해 개발 되었습니다. 그러나이 기술은 Office 바인더가 아닌 액티브 문서 컨테이너를 지원할 만큼 유연 하며 Office 및 Office 호환 응용 프로그램 이외의 문서 서버를 지원할 수 있습니다.

활성 문서를 호스트 하는 응용 프로그램을 [액티브 문서 컨테이너](active-document-containers.md)라고 합니다. 이러한 컨테이너의 예로는 Microsoft Office 바인더 또는 Microsoft Internet Explorer가 있습니다.

액티브 문서 포함은 ole의 복합 문서 기술인 ole 문서에 대 한 확장 집합으로 구현 됩니다. 확장은 포함 된 단일 콘텐츠 대신 전체 문서를 나타낼 수 있는 포함 된 내부 개체를 허용 하는 추가 인터페이스입니다. OLE 문서와 마찬가지로 액티브 문서 포함은 활성 문서에 대 한 표시 공간을 제공 하는 컨테이너와 활성 문서 자체에 대 한 사용자 인터페이스 및 조작 기능을 제공 하는 서버를 사용 합니다.

[활성 문서 서버](active-document-servers.md) 는 하나 이상의 활성 문서 클래스를 지 원하는 응용 프로그램 (예: Word, Excel 또는 PowerPoint)입니다. 각 개체 자체는 적절 한 컨테이너에서 개체를 활성화할 수 있도록 하는 확장 인터페이스를 지원 합니다.

Word 또는 Excel과 같은 활성 문서 서버에서 제공 되는 [활성 문서](active-documents.md) 는 기본적으로 다른 액티브 문서 컨테이너 내에 개체로 포함 되는 전체 크기의 기존 문서입니다. 포함 된 개체와 달리 활성 문서는 해당 페이지를 완전히 제어할 수 있으며, 응용 프로그램의 전체 인터페이스 (모든 기본 명령 및 도구 포함)를 사용 하 여 사용자가 응용 프로그램을 편집할 수 있습니다.

활성 문서는 표준 OLE 포함 개체와 구분 하 여 가장 잘 이해할 수 있습니다. OLE 규칙에 따라 포함 된 개체는 해당 개체를 소유 하는 문서의 페이지 내에 표시 되 고 문서는 OLE 컨테이너를 통해 관리 됩니다. 컨테이너는 포함 된 개체의 데이터를 문서의 나머지 부분과 함께 저장 합니다. 그러나 포함 된 개체는 표시 되는 페이지를 제어 하지 않으므로 제한 됩니다.

액티브 문서 컨테이너 응용 프로그램의 사용자는 즐겨 사용 하는 응용 프로그램을 사용 하 여 (Office 바인더에서 섹션 이라고 함) 활성 문서를 만들 수 있지만 (이러한 응용 프로그램을 사용 하도록 설정 된 경우), 사용자가 결과 프로젝트를 단일 엔터티로 관리할 수 있습니다 .이를 고유 하 게 명명, 저장 및 인쇄할 수 있습니다. 동일한 방식으로, 인터넷 브라우저의 사용자는 전체 네트워크와 로컬 파일 시스템을 단일 위치에서 해당 저장소의 문서를 검색할 수 있는 단일 문서 저장소 엔터티로 취급할 수 있습니다.

## <a name="sample-programs"></a>샘플 프로그램

- [MFCBIND](../overview/visual-cpp-samples.md) 샘플에서는 액티브 문서 컨테이너 응용 프로그램을 구현 하는 방법을 보여 줍니다.

## <a name="see-also"></a>참고 항목

[MFC COM](mfc-com.md)
