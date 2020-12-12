---
description: 자세히 알아보기:/link (링커에 옵션 전달)
title: /link(옵션을 링커로 전달)
ms.date: 03/25/2019
f1_keywords:
- /link
helpviewer_keywords:
- /link compiler option [C++]
- pass options to linker
- link compiler option [C++]
- linker [C++], passing options to
- -link compiler option [C++]
- cl.exe compiler [C++], passing options to linker
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
ms.openlocfilehash: 3617a005e6adbc41a589606aa145712fa2df442d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199495"
---
# <a name="link-pass-options-to-linker"></a>/link(옵션을 링커로 전달)

하나 이상의 링커 옵션을 링커에 전달 합니다.

## <a name="syntax"></a>Syntax

> **/link** *링커-옵션*

## <a name="arguments"></a>인수

*링커-옵션*<br/>
링커에 전달할 링커 옵션 또는 옵션입니다.

## <a name="remarks"></a>설명

**/Link** 옵션과 링커 옵션은 파일 이름 및 CL 옵션 뒤에 나와야 합니다. **/Link** 과 링커 옵션 사이에 공백이 필요 합니다. 자세한 내용은 [MSVC 링커 참조](linking.md)를 참조 하세요.

## <a name="example"></a>예제

이 샘플 명령줄은 *hello.exe* 를 컴파일하여 *.obj* 의 기존 개체 파일에 연결 합니다. 그런 다음 추가 **/VERSION** 명령을 링커에 전달 합니다.

`cl /W4 /EHsc hello.cpp there.obj /link /VERSION:3.14`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

IDE는 일반적으로 별도의 명령을 보내 코드를 컴파일하고 연결 합니다. 프로젝트 속성 페이지에서 링커 옵션을 설정할 수 있습니다.

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **링커** 폴더를 선택 합니다.

1. 하나 이상의 속성을 수정 합니다. **확인** 을 선택하여 변경 내용을 저장합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- 이 컴파일러 옵션은 프로그래밍 방식으로 변경할 수 없습니다.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
