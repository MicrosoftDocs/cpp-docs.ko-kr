---
title: 등록자 코드에 대한 정적 링크 설정(C++ 전용)
description: C + + 코드를 ATL 등록자 코드에 정적으로 연결 하는 방법입니다.
ms.date: 09/03/2020
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
ms.openlocfilehash: f08f7d9433ae1344c7a98a5c52502d03bad21e91
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609153"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>등록자 코드에 대 한 정적 링크 설정 (c + +만 해당)

C + + 클라이언트는 등록자의 코드에 대 한 정적 링크를 만들 수 있습니다. 등록자 파서의 정적 링크는 릴리스 빌드에 약 5K를 추가 합니다.

정적 링크를 설정 하는 가장 간단한 방법은 개체의 선언에를 지정 하는 것 [`DECLARE_REGISTRY_RESOURCEID`](reference/registry-macros.md#declare_registry_resourceid) 입니다. (ATL에서 사용 하는 기본 사양입니다.)

## <a name="to-create-a-static-link-using-declare_registry_resourceid"></a>를 사용 하 여 정적 링크를 만들려면 `DECLARE_REGISTRY_RESOURCEID`

1. **`/D _ATL_STATIC_REGISTRY`** **`/D _ATL_DLL`** CL 명령줄에서 대신를 지정 합니다. 자세한 내용은 [`/D`](../build/reference/d-preprocessor-definitions.md)를 참조하세요.

1. 컴파일하고.

## <a name="see-also"></a>참고 항목

[레지스트리 구성 요소 (등록자)](../atl/atl-registry-component-registrar.md)
