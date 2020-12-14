---
description: 자세한 정보:/ORDER (순서 대로 함수 배치)
title: /ORDER(함수에 순서 지정)
ms.date: 09/05/2018
f1_keywords:
- VC.Project.VCLinkerTool.FunctionOrder
- /order
helpviewer_keywords:
- ORDER linker option
- -ORDER linker option
- LINK tool [C++], program optimizing
- /ORDER linker option
- LINK tool [C++], swap tuning
- paging, optimizing
ms.assetid: ecf5eb3e-e404-4e86-9a91-4e5ec157261a
ms.openlocfilehash: 36888cbb24c869d06eaaa5830b95ae76fc42b860
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226352"
---
# <a name="order-put-functions-in-order"></a>/ORDER(함수에 순서 지정)

개별적으로 패키지 된 (COMDAT) 함수에 대 한 링크 순서를 지정 합니다.

## <a name="syntax"></a>Syntax

> **/Order: \@** <em>파일 이름</em>

### <a name="parameters"></a>매개 변수

*filename*<br/>
COMDAT 함수의 링크 순서를 지정 하는 텍스트 파일입니다.

## <a name="remarks"></a>설명

**/Order** 컴파일러 옵션을 사용 하면 함수를 호출 하는 함수와 함께 그룹화 하 여 프로그램의 페이징 동작을 최적화할 수 있습니다. 자주 호출 되는 함수를 함께 그룹화 할 수도 있습니다. *교환 튜닝* 또는 *페이징 최적화* 라고 하는 이러한 기술은 호출 된 함수가 필요할 때 메모리에 있을 확률을 늘리고 디스크에서 페이징할 필요가 없습니다.

소스 코드를 개체 파일로 컴파일할 때 [/gy (함수 수준 링크 사용)](gy-enable-function-level-linking.md) 컴파일러 옵션을 사용 하 여 각 함수를 *COMDAT* 이라는 자체 섹션에 배치 하도록 컴파일러에 지시할 수 있습니다. **/Order** 링커 옵션은 지정 된 순서 대로 comdat를 실행 가능 이미지에 저장 하도록 링커에 지시 합니다.

COMDAT 순서를 지정 하려면 링커에 의해 배치 되는 순서 대로 각 COMDAT를 이름별로 나열 하는 텍스트 파일인 *지시 파일* 을 만듭니다. 이 파일의 이름을 **/order** 옵션의 *filename* 매개 변수로 전달 합니다. C + + 함수의 경우 COMDAT의 이름은 함수 이름의 데코레이팅된 형태입니다. C 함수, `main` 및로 선언 된 c + + 함수에는 데코레이팅되지 않은 이름을 사용 `extern "C"` 합니다. 함수 이름과 데코레이팅된 이름은 대/소문자를 구분 합니다. 데코레이팅된 이름에 대 한 자세한 내용은 [데코레이팅된 이름](decorated-names.md)을 참조 하세요.

Comdat의 데코레이팅된 이름을 찾으려면 개체 파일에서 [DUMPBIN](dumpbin-reference.md) 도구의 [/SYMBOLS](symbols.md) 옵션을 사용 합니다. 링커가 **\_** 물음표 (**?**) 또는 기호 ()로 시작 하는 경우를 제외 하 고는 응답 파일의 함수 이름에 밑줄 ()을 자동으로 앞에 사용 합니다 **\@** . 예를 들어 소스 파일 예제에 함수 및가 포함 되어 있으면 `int cpp_func(int)` `extern "C" int c_func(int)` `int main(void)` 명령에서 `DUMPBIN /SYMBOLS example.obj` 데코레이팅된 이름을 나열 합니다.

```Output
...
088 00000000 SECT1A notype ()    External     | ?cpp_func@@YAHH@Z (int __cdecl cpp_func(int))
089 00000000 SECT22 notype ()    External     | _c_func
08A 00000000 SECT24 notype ()    External     | _main
...
```

이 경우 `?cpp_func@@YAHH@Z` `c_func` 지시 파일에서, 및로 이름을 지정 `main` 합니다.

하나 이상의 **/order** 옵션이 링커 옵션에 표시 되는 경우 지정 된 마지막 항목은 적용 됩니다.

**/Order** 옵션을 사용 하면 증분 링크를 사용할 수 없습니다. 증분 링크를 사용 하도록 설정 하거나 [/zi (증분 PDB)](z7-zi-zi-debug-information-format.md) 컴파일러 옵션을 지정한 경우이 옵션을 지정 하면 링커 경고가 [LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md) 표시 될 수 있습니다. 이 경고를 표시 하려면 [/INCREMENTAL: NO](incremental-link-incrementally.md) 링커 옵션을 사용 하 여 증분 링크를 해제 하 고 [/Zi (pdb 생성)](z7-zi-zi-debug-information-format.md) 컴파일러 옵션을 사용 하 여 증분 링크 없이 PDB를 생성할 수 있습니다.

> [!NOTE]
> 정적 함수 이름이 공용 기호 이름이 아니므로 LINK에서 정적 함수를 정렬할 수 없습니다. **/Order** 를 지정 하면 순서 지시 파일에서 정적 또는 찾을 수 없는 각 기호에 대해 링커 경고 [LNK4037](../../error-messages/tool-errors/linker-tools-warning-lnk4037.md) 생성 됩니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **링커**  >  **최적화** 속성 페이지를 선택 합니다.

1. 지시 파일의 이름을 포함 하도록 **함수 순서** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.FunctionOrder%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
