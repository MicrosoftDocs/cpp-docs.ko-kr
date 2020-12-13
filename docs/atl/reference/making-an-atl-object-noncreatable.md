---
description: '자세한 정보: ATL 개체 만들기 Noncreatable'
title: ATL 개체를 Noncreatable로 설정
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.objects
helpviewer_keywords:
- noncreatable ATL objects
- ATL projects, noncreatable objects
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
ms.openlocfilehash: 0a7a07081546722e5a960cb8bf0384a1d7e47f9b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139180"
---
# <a name="making-an-atl-object-noncreatable"></a>ATL 개체를 Noncreatable로 설정

클라이언트에서 개체를 직접 만들 수 없도록 ATL 기반 COM 개체의 특성을 변경할 수 있습니다. 이 경우 개체는 직접 만들지 않고 다른 개체에 대 한 메서드 호출을 통해 반환 됩니다.

## <a name="to-make-an-object-noncreatable"></a>개체를 noncreatable 설정 하려면

1. 개체에 대 한 [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) 를 제거 합니다. 개체를 noncreatable 하 고 등록할 컨트롤을 사용 하려면 OBJECT_ENTRY_AUTO [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto)으로 바꿉니다.

1. .Idl 파일의 coclass에 [noncreatable](../../windows/attributes/noncreatable.md) 특성을 추가 합니다. 예를 들어:

    ```
    [uuid(A1992E3D-3CF0-11D0-826F-00A0C90F2851),
    helpstring("MyObject"),
    noncreatable]
    coclass MyObject
    {
        [default] interface IMyInterface;
    }
    ```

## <a name="see-also"></a>참고 항목

[ATL 프로젝트 마법사](../../atl/reference/atl-project-wizard.md)<br/>
[Visual Studio의 C++ 프로젝트 형식](../../build/reference/visual-cpp-project-types.md)<br/>
[ATL 및 C Run-Time 코드를 사용한 프로그래밍](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[ATL COM 개체의 기본 사항](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[기본 ATL 프로젝트 구성](../../atl/reference/default-atl-project-configurations.md)
