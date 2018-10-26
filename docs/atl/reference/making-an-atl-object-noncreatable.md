---
title: ATL 개체 수 없도록 설정 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.objects
dev_langs:
- C++
helpviewer_keywords:
- noncreatable ATL objects
- ATL projects, noncreatable objects
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fff45e65fde53d5621d35766e7170c300ee138f9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50068478"
---
# <a name="making-an-atl-object-noncreatable"></a>ATL 개체 수 없도록 설정 만들기

클라이언트 개체를 직접 만들 수 있도록 ATL 기반 COM 개체의 특성을 변경할 수 있습니다. 이 경우 개체는 수 다른 개체에서 메서드 호출을 통해 반환 된 것이 아니라 직접.

## <a name="to-make-an-object-noncreatable"></a>개체 수 없도록 설정 하려면

1. 제거 된 [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) 개체에 대 한 합니다. 개체를 noncreatable 아니라 등록 컨트롤을 사용 하도록 하려는 경우 대체와 OBJECT_ENTRY_AUTO [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto)합니다.

1. 추가 된 [noncreatable](../../windows/noncreatable.md) .idl 파일의 coclass 특성입니다. 예를 들어:

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
[Visual C++ 프로젝트 형식](../../ide/visual-cpp-project-types.md)<br/>
[응용 프로그램 마법사를 사용하여 데스크톱 프로젝트 만들기](../../ide/creating-desktop-projects-by-using-application-wizards.md)<br/>
[ATL 및 C 런타임 코드를 사용한 프로그래밍](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[ATL COM 개체 기본 사항](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[기본 ATL 프로젝트 구성](../../atl/reference/default-atl-project-configurations.md)
