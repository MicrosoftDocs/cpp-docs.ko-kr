---
description: 자세히 알아보기:/DEFAULTLIB (기본 라이브러리 지정)
title: /DEFAULTLIB(기본 라이브러리 지정)
ms.date: 05/29/2018
f1_keywords:
- VC.Project.VCLinkerTool.DefaultLibraries
- /defaultlib
helpviewer_keywords:
- -DEFAULTLIB linker option
- DEFAULTLIB linker option
- /DEFAULTLIB linker option
- libraries, adding to list of
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
ms.openlocfilehash: 9abaf158ed01b3e0a04d29c55d213c8749462c43
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201692"
---
# <a name="defaultlib-specify-default-library"></a>/DEFAULTLIB(기본 라이브러리 지정)

외부 참조를 확인 하려면 검색할 기본 라이브러리를 지정 합니다.

## <a name="syntax"></a>Syntax

> **/DEFAULTLIB**:_라이브러리_

### <a name="arguments"></a>인수

*라이브러리*<br/>
외부 참조를 확인할 때 검색할 라이브러리의 이름입니다.

## <a name="remarks"></a>설명

**/DEFAULTLIB** 옵션은 참조를 확인할 때 링크가 검색 하는 라이브러리 목록에 *라이브러리* 하나를 추가 합니다. **/DEFAULTLIB** 로 지정 된 라이브러리는 명령줄에서 명시적으로 지정 된 라이브러리와 .obj 파일에 명명 된 기본 라이브러리 앞에 검색 됩니다.

인수 없이 사용 하는 경우 [/nodefaultlib (모든 기본 라이브러리 무시)](nodefaultlib-ignore-libraries.md) 옵션은 모든 **/DEFAULTLIB**:*library* 옵션을 재정의 합니다. **/Nodefaultlib**:*library* 옵션은 둘 다에 동일한 *라이브러리* 이름이 지정 된 경우 **/DEFAULTLIB**:*library* 를 재정의 합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트 **속성 페이지** 대화 상자를 엽니다. 자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

1. **구성 속성** > **링커** > **명령줄** 속성 페이지를 선택합니다.

1. **추가 옵션** 에서 검색할 각 라이브러리에 대해 **/DEFAULTLIB**:*library* 옵션을 입력 합니다. **확인** 을 선택하여 변경 내용을 저장합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

- [MSVC 링커 참조](linking.md)
- [MSVC 링커 옵션](linker-options.md)
