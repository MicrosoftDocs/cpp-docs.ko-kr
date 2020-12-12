---
description: 자세히 알아보기:/FUNCTIONPADMIN (핫 패치 가능 이미지 만들기)
title: /FUNCTIONPADMIN(핫 패치 가능 이미지 만들기)
ms.date: 03/09/2018
f1_keywords:
- /functionpadmin
helpviewer_keywords:
- -FUNCTIONPADMIN linker option
- /FUNCTIONPADMIN linker option
ms.assetid: 25b02c13-1add-4fbd-add9-fcb30eb2cae7
ms.openlocfilehash: f86adb2001adacf1b6c8a03a90b7452505841c08
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192007"
---
# <a name="functionpadmin-create-hotpatchable-image"></a>/FUNCTIONPADMIN(핫 패치 가능 이미지 만들기)

핫 패치를 위한 이미지를 준비 합니다.

## <a name="syntax"></a>Syntax

> **/Functionpadmin**[**:**_space_]

### <a name="arguments"></a>인수

*공간*<br/>
각 함수의 시작 부분에 더할 패딩 크기 (바이트)입니다. X 86에서는 기본적으로 5 바이트의 패딩 및 x 64의 기본값은 6 바이트입니다. 다른 대상에서 값을 제공 해야 합니다.

## <a name="remarks"></a>설명

링커가 핫 패치 가능 이미지를 생성 하려면 .obj 파일은 [/hotpatch (Create 핫 패치 가능 image)](hotpatch-create-hotpatchable-image.md)를 사용 하 여 컴파일해야 합니다.

cl.exe를 한 번 호출 하 여 이미지를 컴파일 및 연결 하는 경우 **/hotpatch** 는 **/functionpadmin** 을 의미 합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성** > **링커** > **명령줄** 속성 페이지를 선택합니다.

1. **추가 옵션** 에 **/propadmin** 옵션을 입력 합니다. **확인** 을 선택하여 변경 내용을 저장합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
