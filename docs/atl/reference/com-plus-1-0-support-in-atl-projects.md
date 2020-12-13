---
description: '자세한 정보: ATL 프로젝트에서 COM + 1.0 지원'
title: ATL 프로젝트의 COM + 1.0 지원
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.MTS
helpviewer_keywords:
- ATL projects, COM+ 1.0 support
ms.assetid: 51fb08ac-d632-4657-a4e0-d3f989f0b6f8
ms.openlocfilehash: 8e196bccf25667da28532248765e47906fdcee97
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141286"
---
# <a name="com-10-support-in-atl-projects"></a>ATL 프로젝트의 COM + 1.0 지원

[ATL 프로젝트 마법사](../../atl/reference/creating-an-atl-project.md) 를 사용 하 여 com + 1.0 구성 요소에 대 한 기본 지원을 포함 하는 프로젝트를 만들 수 있습니다.

COM + 1.0는 배포 된 구성 요소 기반 응용 프로그램을 개발 하기 위해 설계 되었습니다. 또한 이러한 응용 프로그램을 배포 하 고 관리 하는 런타임 인프라를 제공 합니다.

**지원 COM + 1.0** 확인란을 선택 하면 마법사가 링크 단계에서 빌드 스크립트를 수정 합니다. 특히 COM + 1.0 프로젝트는 다음 라이브러리에 연결 됩니다.

- comsvcs

- Mtxguid

**지원 COM + 1.0** 확인란을 선택 하는 경우 **지원 구성 요소 등록자** 를 선택할 수도 있습니다. 구성 요소 등록자를 사용 하면 COM + 1.0 개체에서 구성 요소 목록을 가져오거나, 구성 요소를 등록 하거나, 구성 요소를 개별적으로 또는 한꺼번에 등록 취소할 수 있습니다.

## <a name="see-also"></a>참고 항목

[ATL COM 개체의 기본 사항](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[ATL 및 C Run-Time 코드를 사용한 프로그래밍](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[기본 ATL 프로젝트 구성](../../atl/reference/default-atl-project-configurations.md)
