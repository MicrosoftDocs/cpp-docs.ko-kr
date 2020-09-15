---
title: '/o실험적: module (모듈 지원 사용)'
description: '/S실험적: module 컴파일러 옵션을 사용 하 여 모듈에 대 한 실험적 컴파일러 지원을 사용 하도록 설정 합니다.'
ms.date: 09/03/2019
f1_keywords:
- module
- /experimental:module
helpviewer_keywords:
- module
- /experimental:module
- Enable module support
ms.openlocfilehash: 0eea5127f651eaff30c197271ae6da38ac1356be
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075727"
---
# <a name="experimentalmodule-enable-module-support"></a>/o실험적: module (모듈 지원 사용)

초안 c + + 20 표준에 지정 된 대로 모듈에 대 한 실험적 컴파일러 지원을 사용 하도록 설정 합니다.

## <a name="syntax"></a>구문

> **/s실험적: module**[ **-** ]

## <a name="remarks"></a>설명

/Std: [c + + 최신](std-specify-language-standard-version.md) 옵션과 함께 **/s실험적: module** 컴파일러 옵션을 사용 하 여 실험적 모듈 지원을 사용 하도록 설정할 수 있습니다. **/S실험적: module** 을 사용 하 여 모듈 지원을 명시적으로 사용 하지 않도록 설정할 수 있습니다.

이 옵션은 Visual Studio 2015 업데이트 1부터 사용할 수 있습니다. Visual Studio 2019 버전 16.2부터 초안 c + + 20 표준 모듈은 Microsoft c + + 컴파일러에서 완전히 구현 되지 않습니다. 모듈 기능을 사용 하 여 단일 파티션 모듈을 만들고 Microsoft에서 제공 하는 표준 라이브러리 모듈을 가져올 수 있습니다. 모듈 및 모듈을 사용 하는 코드는 동일한 컴파일러 옵션을 사용 하 여 컴파일해야 합니다.

모듈 및 모듈을 사용 하 고 만드는 방법에 대 한 자세한 내용은 [c + +의 모듈 개요](../../cpp/modules-cpp.md)를 참조 하세요.

소스 파일 ModuleName에서 내보내기 모듈을 만드는 데 사용 되는 컴파일러 명령줄 옵션의 예는 다음과 같습니다 *.*

```cmd
cl /EHsc /MD /experimental:module /module:export /module:name ModuleName /module:wrapper C:\Output\path\ModuleName.h /module:output C:\Output\path\ModuleName.ifc -c ModuleName.ixx
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성** 드롭다운을 **모든 구성**으로 설정 합니다.

1. **구성 속성**  >  **C/c + +**  >  **언어** 속성 페이지를 선택 합니다.

1. **C + + 모듈 사용 (실험적)** 속성을 수정한 다음 **확인**을 선택 합니다.

## <a name="see-also"></a>참고 항목

[`/headerUnit` (헤더 단위 IFC 사용)](headerunit.md)\
[`/module:exportHeader` (헤더 단위 만들기)](module-exportheader.md)\
[`/module:reference` (명명 된 모듈 (IFC) 사용)](module-reference.md)\
[`/translateInclude` (Include 지시문을 import 지시문으로 변환)](translateinclude.md)\
[/Zc(규칙)](zc-conformance.md)
