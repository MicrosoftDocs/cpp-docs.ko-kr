---
description: '자세한 정보: 대체 가능 매개 변수 사용 (등록자&#39;s 전처리기)'
title: 대체 가능 매개 변수 사용 (ATL 등록자)
ms.date: 11/04/2016
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
ms.openlocfilehash: 5b8b8071115186a462bbf9ca0b12d869458dd925
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157204"
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>대체 가능 매개 변수 사용 (등록자&#39;s 전처리기)

대체 가능 매개 변수를 사용 하 여 등록자의 클라이언트는 런타임 데이터를 지정할 수 있습니다. 이를 위해 등록자는 스크립트의 대체 가능 매개 변수와 연결 된 값이 입력 되는 대체 맵을 유지 관리 합니다. 등록자는 런타임에 이러한 항목을 만듭니다.

## <a name="using-module"></a><a name="_atl_using_.25.module.25"></a> % MODULE% 사용

[ATL 컨트롤 마법사](../atl/reference/atl-control-wizard.md) 는를 사용 하는 스크립트를 자동으로 생성 합니다 `%MODULE%` . ATL은 서버 DLL 또는 EXE의 실제 위치에 대해 대체 가능한 매개 변수를 사용 합니다.

## <a name="concatenating-run-time-data-with-script-data"></a>스크립트 데이터를 사용 하 여 Run-Time 데이터 연결

전처리기의 또 다른 용도는 런타임 데이터를 스크립트 데이터와 연결 하는 것입니다. 예를 들어 "" 문자열이 끝에 추가 된 모듈의 전체 경로를 포함 하는 항목이 필요 하다 고 가정 `, 1` 합니다. 먼저 다음과 같은 확장을 정의 합니다.

```rgs
'MySampleKey' = s '%MODULE%, 1'
```

그런 다음 [스크립트 호출](../atl/invoking-scripts.md)에 나열 된 스크립트 처리 방법 중 하나를 호출 하기 전에 맵에 대체를 추가 합니다.

[!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]

스크립트를 구문 분석 하는 동안 등록 기관은 `'%MODULE%, 1'` 로 확장 `c:\mycode\mydll.dll, 1` 됩니다.

> [!NOTE]
> 등록자 스크립트에서 4K는 최대 토큰 크기입니다. 토큰은 구문에서 인식할 수 있는 모든 요소입니다. 여기에는 전처리기에 의해 만들어지거나 확장 된 토큰이 포함 됩니다.

> [!NOTE]
> 런타임에 대체 값을 대체 하려면 스크립트에서 [DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource) 또는 [DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid) 매크로에 대 한 호출을 제거 합니다. 대신, `UpdateRegistry` [UpdateRegistryFromResourceD](../atl/reference/catlmodule-class.md#updateregistryfromresourced) 또는 [UpdateRegistryFromResourceS](../atl/reference/catlmodule-class.md#updateregistryfromresources)를 호출 하는 고유한 메서드로 대체 하 고 _ATL_REGMAP_ENTRY 구조체의 배열을 전달 합니다. _ATL_REGMAP_ENTRY 배열에는 {NULL, NULL} (으)로 설정 된 항목이 적어도 하나 이상 있어야 하며,이 항목은 항상 마지막 항목 이어야 합니다. 그렇지 않으면가 호출 될 때 액세스 위반 오류가 생성 됩니다 `UpdateRegistryFromResource` .

> [!NOTE]
> 실행 파일을 출력 하는 프로젝트를 빌드할 때 ATL은 런타임에 생성 된 경로 이름 앞뒤에 **% MODULE%** 등록자 스크립트 매개 변수를 사용 하 여 자동으로 따옴표를 추가 합니다. 경로 이름에 따옴표를 포함 하지 않으려면 새 **% MODULE_RAW%** 매개 변수를 대신 사용 합니다.
>
> DLL을 출력 하는 프로젝트를 빌드할 때 **% MODULE%** 또는 **% MODULE_RAW%** 가 사용 되 면 ATL은 경로 이름에 따옴표를 추가 하지 않습니다.

## <a name="see-also"></a>참고 항목

[등록자 스크립트 만들기](../atl/creating-registrar-scripts.md)
