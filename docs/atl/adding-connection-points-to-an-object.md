---
description: '자세한 정보: 개체에 연결 요소 추가'
title: 개체에 연결 지점 추가
ms.date: 11/04/2016
helpviewer_keywords:
- connection points [C++], adding to ATL objects
- Implement Connection Point ATL wizard
ms.assetid: 843531be-4a36-4db0-9d54-e029b1a72a8b
ms.openlocfilehash: 7d8274ab37cef28a58666852aad24db7d945d26e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166241"
---
# <a name="adding-connection-points-to-an-object"></a>개체에 연결 지점 추가

[ATL 자습서](../atl/active-template-library-atl-tutorial.md) 에서는 연결 지점에 대 한 지원을 포함 하는 컨트롤을 만드는 방법, 이벤트를 추가 하는 방법 및 연결 지점을 구현 하는 방법을 보여 줍니다. ATL은 [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) 클래스를 사용 하 여 연결 요소를 구현 합니다.

연결 지점을 구현 하기 위해 다음 두 가지 옵션을 선택할 수 있습니다.

- 컨트롤이 나 개체에 연결 지점을 추가 하 여 나가는 이벤트 소스를 직접 구현 합니다.

- 다른 형식 라이브러리에 정의 된 연결 지점 인터페이스를 다시 사용 합니다.

두 경우 모두 연결 지점 구현 마법사는 형식 라이브러리를 사용 하 여 작업을 수행 합니다.

### <a name="to-add-a-connection-point-to-a-control-or-object"></a>컨트롤이 나 개체에 연결 지점을 추가 하려면

1. .Idl 파일의 라이브러리 블록에서 요소를 정의 합니다. ATL 컨트롤 마법사를 사용 하 여 컨트롤을 만들 때 연결 지점의 지원을 사용 하도록 설정한 경우에는 해당 사용자가 이미 생성 됩니다. 컨트롤을 만들 때 연결 지점의 지원을 사용 하도록 설정 하지 않은 경우 .idl 파일에 직접 추가 해야 합니다. 다음은이에 대 한 예입니다. 나가는 인터페이스는 디스패치 인터페이스가 될 필요는 없지만 VBScript 및 JScript와 같은 많은 스크립팅 언어에는이 작업이 필요 하므로이 예제에서는 두 개의 dispinterface를 사용 합니다.

   [!code-cpp[NVC_ATL_Windowing#81](../atl/codesnippet/cpp/adding-connection-points-to-an-object_1.idl)]

   uuidgen.exe 또는 guidgen.exe 유틸리티를 사용 하 여 GUID를 생성 합니다.

2. `[default,source]`프로젝트의 .idl 파일에서 개체에 대 한 coclass를 인터페이스로 추가 합니다. 컨트롤을 만들 때 연결 지점의 지원을 사용 하도록 설정한 경우에도 ATL 컨트롤 마법사에서 `[default,source` ] 항목을 만듭니다. 이 항목을 수동으로 추가 하려면 굵게 표시 된 줄을 추가 합니다.

   [!code-cpp[NVC_ATL_Windowing#82](../atl/codesnippet/cpp/adding-connection-points-to-an-object_2.idl)]

   예제는 [Circ](../overview/visual-cpp-samples.md) ATL 샘플에서 .idl 파일을 참조 하세요.

3. 클래스 뷰를 사용 하 여 메서드 및 속성을 이벤트 인터페이스에 추가 합니다. 클래스 뷰에서 클래스를 마우스 오른쪽 단추로 클릭 하 고 바로 가기 메뉴에서 **추가** 를 가리킨 다음 **연결 지점 추가** 를 클릭 합니다.

4. 연결 지점 구현 마법사의 **원본 인터페이스** 목록 상자에서 **프로젝트의 인터페이스** 를 선택 합니다. 컨트롤에 대 한 인터페이스를 선택 하 고 **확인** 을 누르면 다음 작업을 수행 합니다.

   - 이벤트에 대 한 나가는 호출을 수행 하는 코드를 구현 하는 이벤트 프록시 클래스를 사용 하 여 헤더 파일을 생성 합니다.

   - 연결 지점 맵에 항목을 추가 합니다.

   또한 컴퓨터의 모든 형식 라이브러리 목록이 표시 됩니다. 다른 형식 라이브러리에 있는 것과 정확히 동일한 송신 인터페이스를 구현 하려는 경우에만 이러한 다른 형식 라이브러리 중 하나를 사용 하 여 연결 지점을 정의 해야 합니다.

### <a name="to-reuse-a-connection-point-interface-defined-in-another-type-library"></a>다른 형식 라이브러리에 정의 된 연결 지점 인터페이스를 다시 사용 하려면

1. 클래스 뷰에서 **BEGIN_COM_MAP** 매크로를 구현 하는 클래스를 마우스 오른쪽 단추로 클릭 하 고 바로 가기 메뉴에서 **추가** 를 가리킨 다음 **연결 지점 추가** 를 클릭 합니다.

2. 연결 지점 구현 마법사에서 형식 라이브러리의 형식 라이브러리 및 인터페이스를 선택 하 고 **추가** 를 클릭 합니다.

3. .Idl 파일을 다음 중 하나로 편집 합니다.

   - 해당 이벤트 원본이 사용 되 고 있는 개체에 대 한 .idl 파일의 개체를 복사 합니다.

   - 해당 형식 라이브러리에 대해 **importlib** 명령을 사용 합니다.

## <a name="see-also"></a>참고 항목

[연결점](../atl/atl-connection-points.md)
