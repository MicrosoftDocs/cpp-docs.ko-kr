---
description: 다음에 대 한 자세한 정보:/vmm,/svm,/vmv (일반적인 용도 표시)
title: /vmm,-vm,-vmv (일반적인 용도 표시)
ms.date: 11/04/2016
f1_keywords:
- /vms
- /vmm
- /vmv
helpviewer_keywords:
- Virtual Inheritance compiler option
- general purpose representation compiler options
- vms compiler option [C++]
- vmm compiler option [C++]
- /vmm compiler option [C++]
- -vmm compiler option [C++]
- -vms compiler option [C++]
- /vms compiler option [C++]
- vmv compiler option [C++]
- /vmv compiler option [C++]
- Single Inheritance compiler option
- -vmv compiler option [C++]
ms.assetid: 0fcd7ae0-3031-4c62-a2a8-e154c8685dae
ms.openlocfilehash: 8c5761a2f51ec9860a4afeb7d4aacbf7f882b3f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257227"
---
# <a name="vmm-vms-vmv-general-purpose-representation"></a>/vmm, /vms, /vmv(일반적인 용도 표시)

[/Vmb,/vmg (표시 메서드)](vmb-vmg-representation-method.md) 를 [표시 메서드로](vmb-vmg-representation-method.md)선택한 경우 사용 됩니다. 이러한 옵션은 아직 발생 하지 않은 클래스 정의의 상속 모델을 표시 합니다.

## <a name="syntax"></a>구문

```
/vmm
/vms
/vmv
```

## <a name="remarks"></a>설명

다음 표에서는 이러한 옵션에 대해 설명합니다.

|옵션|설명|
|------------|-----------------|
|**/vmm**|클래스 멤버에 대 한 포인터의 가장 일반적인 표현을 여러 상속을 사용 하는 것으로 지정 합니다.<br /><br /> [#Pragma pointers_to_members](../../preprocessor/pointers-to-members.md) 에 해당 하는 [상속 키워드](../../cpp/inheritance-keywords.md) 및 인수는 **multiple_inheritance** 됩니다.<br /><br /> 이 표현은 단일 상속에 필요한 것 보다 큽니다.<br /><br /> 멤버에 대 한 포인터가 선언 되는 클래스 정의의 상속 모델이 virtual 인 경우 컴파일러에서 오류를 생성 합니다.|
|**/vms**|클래스 멤버에 대 한 포인터의 가장 일반적인 표현을 상속 안 함 또는 단일 상속 중 하나를 사용 하는 것으로 지정 합니다.<br /><br /> [#Pragma pointers_to_members](../../preprocessor/pointers-to-members.md) 에 해당 하는 [상속 키워드](../../cpp/inheritance-keywords.md) 및 인수는 **single_inheritance** 됩니다.<br /><br /> 이것은 클래스 멤버에 대 한 포인터의 가장 작은 표현입니다.<br /><br /> 멤버에 대 한 포인터가 선언 되는 클래스 정의의 상속 모델이 multiple 또는 virtual 인 경우 컴파일러에서 오류를 생성 합니다.|
|**/vmv**|클래스 멤버에 대 한 포인터의 가장 일반적인 표현을 가상 상속을 사용 하는 것으로 지정 합니다. 오류가 발생 하지 않으며 기본값입니다.<br /><br /> [#Pragma pointers_to_members](../../preprocessor/pointers-to-members.md) 에 해당 하는 [상속 키워드](../../cpp/inheritance-keywords.md) 및 인수는 **virtual_inheritance** 됩니다.<br /><br /> 이 옵션을 사용 하려면 다른 옵션 보다 포인터를 해석 하는 더 큰 포인터와 추가 코드가 필요 합니다.|

이러한 상속 모델 옵션 중 하나를 지정 하는 경우 해당 상속 형식 또는 클래스 전후에 포인터를 선언 했는지 여부에 관계 없이 해당 모델은 클래스 멤버에 대 한 모든 포인터에 사용 됩니다. 따라서 항상 단일 상속 클래스를 사용 하는 경우 **/vm** 을 사용 하 여 컴파일하여 코드 크기를 줄일 수 있습니다. 그러나 가장 일반적인 사례 (가장 큰 데이터 표현의 비용)를 사용 하려는 경우 **/vmv** 를 사용 하 여 컴파일합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/C++** 폴더를 클릭합니다.

1. **명령줄** 속성 페이지를 클릭합니다.

1. **추가 옵션** 상자에 컴파일러 옵션을 입력합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/vmb,/vmg (표시 메서드)](vmb-vmg-representation-method.md)<br/>
[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
