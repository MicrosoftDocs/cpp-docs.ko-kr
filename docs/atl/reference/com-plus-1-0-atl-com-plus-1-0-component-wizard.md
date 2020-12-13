---
description: '자세한 정보: COM + 1.0, ATL COM + 1.0 구성 요소 마법사'
title: COM+ 1.0, ATL COM+ 1.0 구성 요소 마법사
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.mts.options
ms.assetid: 2fbe259c-6be1-4d0e-9cfe-721c75c97cb1
ms.openlocfilehash: 581a258fc2702465fea40590430080bb6b9fcd66
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141299"
---
# <a name="com-10-atl-com-10-component-wizard"></a>COM+ 1.0, ATL COM+ 1.0 구성 요소 마법사

::: moniker range="msvc-160"

Visual Studio 2019 이상에서는 이 마법사를 사용할 수 없습니다.

::: moniker-end

::: moniker range="<=msvc-150"

ATL COM + 1.0 구성 요소 마법사의 이 페이지를 사용하여 지원되는 인터페이스 유형 및 추가 인터페이스를 지정합니다.

ATL 프로젝트 및 ATL COM 클래스에 대한 자세한 내용은 [ATL COM 데스크톱 구성 요소](../../atl/atl-com-desktop-components.md)를 참조하세요.

- **인터페이스**

   개체가 지원하는 인터페이스의 형식을 나타냅니다. 개체는 기본적으로 이중 인터페이스를 지원합니다.

   |옵션|설명|
   |------------|-----------------|
   |**이중**|개체가 이중 인터페이스를 지원하도록 지정합니다(해당 vtable에 사용자 지정 인터페이스를 사용자 지정 함수 및 런타임에 바인딩된 `IDispatch` 메서드가 있음). COM 클라이언트와 자동화 컨트롤러 개체에 액세스할 수 있게 합니다.|
   |**사용자 지정**|개체가 사용자 지정 인터페이스를 지원하도록 지정합니다(해당 vtable에 사용자 지정 함수가 있음). 사용자 지정 인터페이스는 특히 프로세스 경계를 넘어서는 이중 인터페이스보다 빠를 수 있습니다.<br /><br /> - **자동화 호환** 사용자 지정 인터페이스에 자동화 지원을 추가합니다. 특성이 지정된 프로젝트의 경우 coclass에 **oleautomation** 특성을 설정합니다.|

- **큐 가능**

   클라이언트가 메시지 큐를 사용하여 이 구성 요소를 비동기식으로 호출할 수 있음을 나타냅니다. 구성 요소 특성이 지정된 매크로 사용자 지정(TLBATTR_QUEUEABLE, 0)을 .h 파일(특성이 지정된 프로젝트) 또는 .idl 파일(특성이 지정되지 않는 프로젝트)에 추가합니다.

- **지원**

   오류 처리 및 개체 컨트롤에 대한 추가 지원을 나타냅니다.

   |옵션|설명|
   |------------|-----------------|
   |**ISupportErrorInfo**|개체가 오류 정보를 클라이언트에 반환할 수 있도록 [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) 인터페이스에 대한 지원을 만듭니다.|
   |**IObjectControl**|는 [Activate](/windows/win32/api/comsvcs/nf-comsvcs-iobjectcontrol-activate), [Canbepooled](/windows/win32/api/comsvcs/nf-comsvcs-iobjectcontrol-canbepooled)및 [Deactivate](/windows/win32/api/comsvcs/nf-comsvcs-iobjectcontrol-deactivate)의 세 가지 [IObjectControl](/windows/win32/api/comsvcs/nn-comsvcs-iobjectcontrol) 메서드에 대 한 개체 액세스를 제공 합니다.|
   |**IObjectConstruct**|[IObjectConstruct](/windows/win32/api/comsvcs/nn-comsvcs-iobjectconstruct) 인터페이스에 대한 지원을 생성하여 다른 메서드 또는 개체에서 매개 변수를 전달하는 것을 관리합니다.|

- **트랜잭션**

   개체가 트랜잭션을 지원함을 나타냅니다. .idl 파일에 mtxattr.h 파일을 포함합니다(특성이 지정되지 않은 프로젝트).

   |옵션|설명|
   |------------|-----------------|
   |**지원됨**|.h 파일(특성이 지정된 프로젝트) 또는 .idl 파일(특성이 지정되지 않는 프로젝트)에 구성 요소 특성 매크로 사용자 지정(TLBATTR_TRANS_SUPPORTED,0)을 추가하여 개체가 트랜잭션 스트림의 루트가 되지 않도록 지정합니다.|
   |**필수**|.h 파일(특성이 지정된 프로젝트) 또는 .idl 파일(특성이 지정되지 않는 프로젝트)에 구성 요소 특성 매크로 사용자 지정(TLBATTR_TRANS_REQUIRED,0)을 추가하여 개체가 트랜잭션 스트림의 루트인지 여부를 지정합니다.|
   |**지원되지 않음**|개체가 트랜젝션을 제외하도록 지정합니다. 구성 요소 특성 매크로 사용자 지정(TLBATTR_TRANS_NOTSUPP, 0)을 .h 파일(특성이 지정된 프로젝트) 또는 .idl 파일(특성이 지정되지 않는 프로젝트)에 추가합니다.|
   |**새로 만들기 필요**|.h 파일(특성이 지정된 프로젝트) 또는 .idl 파일(특성이 지정되지 않는 프로젝트)에 구성 요소 특성 매크로 사용자 지정(TLBATTR_TRANS_REQNEW,0)을 추가하여 개체가 항상 트랜잭션 스트림의 루트가 되도록 지정합니다.|

::: moniker-end

## <a name="see-also"></a>참고 항목

[ATL COM + 1.0 구성 요소 마법사](../../atl/reference/atl-com-plus-1-0-component-wizard.md)<br/>
[ATL COM+ 1.0 구성 요소](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)
