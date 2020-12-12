---
description: '자세히 알아보기: CAtlServiceModuleT:: Handler 함수'
title: 'CAtlServiceModuleT:: Handler 함수'
ms.date: 11/04/2016
helpviewer_keywords:
- Handler method
ms.assetid: 14db5f2a-be87-4774-a296-445cb6fc7b2e
ms.openlocfilehash: 934c612b6fdfd47bb9966536cc335da58fbd38c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148371"
---
# <a name="catlservicemodulethandler-function"></a>CAtlServiceModuleT:: Handler 함수

`CAtlServiceModuleT::Handler` SCM (서비스 제어 관리자)이 서비스 상태를 검색 하 고이를 중지 하거나 일시 중지 하는 등의 다양 한 지침을 제공 하기 위해 호출 하는 루틴입니다. SCM은 작업 코드를에 전달 하 여 서비스가 수행 해야 하는 작업을 `Handler` 표시 합니다. 기본 ATL 생성 서비스는 중지 명령만 처리 합니다. SCM이 중지 명령을 전달 하는 경우 서비스는 SCM에 프로그램이 중지 됨을 알립니다. 그런 다음 서비스는를 호출 `PostThreadMessage` 하 여 종료 메시지를 자체에 게시 합니다. 그러면 메시지 루프가 종료 되 고 서비스가 궁극적으로 닫힙니다.

추가 지침을 처리 하려면 `m_status` 생성자에서 초기화 된 데이터 멤버를 변경 해야 `CAtlServiceModuleT` 합니다. 이 데이터 멤버는 서비스 제어판 응용 프로그램에서 서비스를 선택할 때 사용할 수 있는 단추를 SCM에 알립니다.

## <a name="see-also"></a>참고 항목

[Services](../atl/atl-services.md)<br/>
[CAtlServiceModuleT:: Handler](../atl/reference/catlservicemodulet-class.md#handler)
