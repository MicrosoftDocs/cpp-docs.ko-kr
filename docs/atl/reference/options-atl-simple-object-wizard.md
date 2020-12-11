---
description: '자세히 알아보기: 옵션, ATL 단순 개체 마법사'
title: 옵션, ATL 단순 개체 마법사
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.simple.options
helpviewer_keywords:
- ATL Simple Object Wizard, options
ms.assetid: 125fe179-942d-4181-8b82-33e92e1fd779
ms.openlocfilehash: 37353358aecddc084e5f29c6c6ee75b393fe8ded
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157843"
---
# <a name="options-atl-simple-object-wizard"></a>옵션, ATL 단순 개체 마법사

ATL 단순 개체 마법사의이 페이지에서는 개체에 대 한 향상 된 효율성 및 오류 지원을 디자인할 수 있습니다.

ATL 프로젝트 및 ATL COM 클래스에 대한 자세한 내용은 [ATL COM 데스크톱 구성 요소](../../atl/atl-com-desktop-components.md)를 참조하세요.

- **스레딩 모델**

   스레드를 관리 하는 방법을 나타냅니다. 기본적으로 프로젝트는 **아파트** 스레딩을 사용 합니다.

   자세한 내용은 [프로젝트의 스레딩 모델 지정](../../atl/specifying-the-threading-model-for-a-project-atl.md)을 참조하세요.

   |옵션|설명|
   |------------|-----------------|
   |**Single**|개체가 항상 주 COM 스레드에서 실행 되도록 지정 합니다. 자세한 내용은 [단일 스레드 아파트](/windows/win32/com/single-threaded-apartments) 및 [InprocServer32](/windows/win32/com/inprocserver32) 를 참조 하세요.|
   |**아파트로**|개체가 아파트 스레딩을 사용 하도록 지정 합니다. 단일 스레드 아파트와 동일 합니다. 아파트 스레드 구성 요소의 각 개체에는 개체의 수명 동안 해당 스레드에 대 한 아파트가 할당 됩니다. 그러나 여러 개체에 대해 여러 스레드를 사용할 수 있습니다. 각 아파트는 특정 스레드에 연결 되며 Windows 메시지 펌프 (기본값)를 포함 합니다.<br /><br /> 자세한 내용은 [단일 스레드 아파트](/windows/win32/com/single-threaded-apartments) 를 참조 하세요.|
   |**모두**|개체가 만든 스레드의 종류에 따라 개체가 아파트 또는 자유 스레딩을 사용할 수 있도록 지정 합니다.|
   |**Free**|개체에서 자유 스레딩을 사용 하도록 지정 합니다. 자유 스레딩은 다중 스레드 아파트 모델과 같습니다. 자세한 내용은 [다중 스레드 아파트](/windows/win32/com/multithreaded-apartments) 를 참조 하세요.|
   |**Neutral**|개체가 다중 스레드 아파트에 대 한 지침을 따르는지를 지정 하지만 모든 종류의 스레드에서 실행 될 수 있습니다.|

- **집계**

   개체가 [집계](/windows/win32/com/aggregation)를 사용 하는지 여부를 나타냅니다. 집계 개체는 클라이언트에 노출할 인터페이스를 선택 하 고, 인터페이스는 집계 개체가 구현 하는 것 처럼 노출 됩니다. 집계 개체의 클라이언트는 집계 개체와만 통신 합니다.

   |옵션|설명|
   |------------|-----------------|
   |**예**|개체를 집계할 수 있도록 지정 합니다. 기본값입니다.|
   |**아니요**|개체를 집계 하지 않도록 지정 합니다.|
   |**에게만**|개체를 집계 하도록 지정 합니다.|

- **인터페이스**

   개체가 지원하는 인터페이스의 형식을 나타냅니다. 개체는 기본적으로 이중 인터페이스를 지원합니다.

   |옵션|설명|
   |------------|-----------------|
   |**이중**|개체가 이중 인터페이스를 지원 하도록 지정 합니다. 해당 vtable에는 사용자 지정 인터페이스 함수 및 런타임에 바인딩 `IDispatch` 메서드가 있습니다. COM 클라이언트와 [자동화 컨트롤러](../../mfc/automation-clients.md) 모두에서 개체에 액세스할 수 있습니다. 기본값입니다.|
   |**사용자 지정**|개체가 사용자 지정 인터페이스를 지원하도록 지정합니다(해당 vtable에 사용자 지정 함수가 있음). 사용자 지정 인터페이스는 특히 프로세스 경계를 넘어서는 이중 인터페이스보다 빠를 수 있습니다.<br /><br /> - **자동화 호환** 자동화 컨트롤러에서 사용자 지정 인터페이스를 지 원하는 개체에 액세스할 수 있도록 합니다.|

- **지원**

   개체에 대 한 추가 지원을 나타냅니다.

   |옵션|설명|
   |------------|-----------------|
   |**ISupportErrorInfo**|개체가 오류 정보를 클라이언트에 반환할 수 있도록 [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) 인터페이스에 대한 지원을 만듭니다.|
   |**연결 지점**|개체의 클래스가 [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)에서 파생 되도록 하 여 개체에 대 한 연결 요소를 사용 하도록 설정 합니다.|
   |**자유 스레드된 마샬러**|동일한 프로세스의 스레드 간에 인터페이스 포인터를 효율적으로 마샬링하는 자유 스레드된 마샬러 개체를 만듭니다. **둘 다** 를 스레딩 모델로 지정 하는 개체에 사용할 수 있습니다.|
   |**IObjectWithSite** (IE 개체 지원)|컨테이너에서 개체와 해당 사이트 간의 통신을 지 원하는 간단한 방법을 제공 하는 [IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md)를 구현 합니다.|

## <a name="see-also"></a>참고 항목

[ATL 단순 개체 마법사](../../atl/reference/atl-simple-object-wizard.md)<br/>
[ATL 단순 개체](../../atl/reference/adding-an-atl-simple-object.md)<br/>
[In-process 서버 스레딩 문제](/windows/win32/com/in-process-server-threading-issues)
