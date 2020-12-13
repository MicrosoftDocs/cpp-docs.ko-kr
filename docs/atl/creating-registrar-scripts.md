---
description: '자세한 정보: 등록자 스크립트 만들기'
title: ATL 등록자에 대한 스크립트 만들기
ms.date: 05/14/2014
helpviewer_keywords:
- scripting, registry scripting
- ATL, registry
- registrar scripts [ATL]
- scripts, Registrar scripts
- scripts, creating
ms.assetid: cbd5024b-8061-4a71-be65-7fee90374a35
ms.openlocfilehash: a3ce4855460e65eda5ab522bc16f39191da02a71
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153189"
---
# <a name="creating-registrar-scripts"></a>등록자 스크립트 만들기

등록자 스크립트는 API 기반이 아닌 데이터 기반 액세스를 제공합니다. 레지스트리에 키를 추가하기 위해 스크립트에서 하나나 둘 정도의 줄만 필요하므로 일반적으로 데이터 기반 액세스가 더 효율적입니다.

[ATL 컨트롤 마법사](../atl/reference/atl-control-wizard.md)는 COM 서버에 대한 등록자 스크립트를 자동으로 생성합니다. 이 스크립트는 개체와 연결된 .rgs 파일에서 찾을 수 있습니다.

ATL 등록자의 스크립트 엔진은 런타임 시 등록자 스크립트를 처리합니다. ATL은 서버 설치 중에 스크립트 엔진을 자동으로 호출합니다.

이 문서는 등록자 스크립트와 관련된 다음 항목을 다룹니다.

- [BNF(Backus-Naur 양식) 구문 이해](../atl/understanding-backus-naur-form-bnf-syntax.md)

- [구문 분석 트리 이해](../atl/understanding-parse-trees.md)

- [레지스트리 스크립팅 예제](../atl/registry-scripting-examples.md)

- [대체 가능 매개 변수 사용 (등록자의 전처리기)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)

- [스크립트 호출](../atl/invoking-scripts.md)

## <a name="see-also"></a>참고 항목

[레지스트리 구성 요소(등록자)](../atl/atl-registry-component-registrar.md)
