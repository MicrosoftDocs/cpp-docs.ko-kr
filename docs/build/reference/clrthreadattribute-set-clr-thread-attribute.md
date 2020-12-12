---
description: 자세히 알아보기:/CLRTHREADATTRIBUTE (CLR 스레드 특성 설정)
title: /CLRTHREADATTRIBUTE(CLR 스레드 특성 설정)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.CLRThreadAttribute
helpviewer_keywords:
- /CLRTHREADATTRIBUTE linker option
- -CLRTHREADATTRIBUTE linker option
ms.assetid: 4907e9ef-5031-446c-aecf-0a0b32fae1e8
ms.openlocfilehash: 119797ee10ed0c08477b8e08635605e4299ffd41
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179124"
---
# <a name="clrthreadattribute-set-clr-thread-attribute"></a>/CLRTHREADATTRIBUTE(CLR 스레드 특성 설정)

CLR 프로그램의 진입점에 대 한 스레딩 특성을 명시적으로 지정 합니다.

## <a name="syntax"></a>구문

```
/CLRTHREADATTRIBUTE:{STA|MTA|NONE}
```

#### <a name="parameters"></a>매개 변수

**MTA**<br/>
프로그램의 진입점에 MTAThreadAttribute 특성을 적용 합니다.

**NONE**<br/>
/CLRTHREADATTRIBUTE.를 지정 하지 않는 것과 같습니다.  CLR (공용 언어 런타임)에서 기본 스레딩 특성을 설정할 수 있도록 합니다.

**STA**<br/>
프로그램의 진입점에 STAThreadAttribute 특성을 적용 합니다.

## <a name="remarks"></a>설명

Thread 특성 설정은 주 스레드의 진입점에 영향을 주므로 .exe를 빌드하는 경우에만 유효 합니다.

기본 진입점을 사용 하는 경우 (예: main 또는 wmain)/CLRTHREADATTRIBUTE를 사용 하거나 기본 항목 함수에 스레딩 특성 (STAThreadAttribute 또는 MTAThreadAttribute)을 배치 하 여 스레딩 모델을 지정 합니다.

기본이 아닌 진입점을 사용 하는 경우/CLRTHREADATTRIBUTE를 사용 하거나 기본이 아닌 항목 함수에 스레딩 특성을 배치 하 여 스레딩 모델을 지정 하 고 [/entry](entry-entry-point-symbol.md)를 사용 하 여 기본이 아닌 진입점을 지정 합니다.

소스 코드에 지정 된 스레딩 모델이/CLRTHREADATTRIBUTE로 지정 된 스레딩 모델과 일치 하지 않는 경우 링커에서는/CLRTHREADATTRIBUTE를 무시 하 고 소스 코드에 지정 된 스레딩 모델을 적용 합니다.

단일 스레딩을 사용 하는 경우, 예를 들어, CLR 프로그램에서 단일 스레딩을 사용 하는 COM 개체를 호스팅하는 경우에 필요 합니다.  CLR 프로그램에서 다중 스레딩을 사용 하는 경우 단일 스레딩을 사용 하는 COM 개체를 호스트할 수 없습니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성** 노드를 확장합니다.

1. **링커** 노드를 확장합니다.

1. **고급** 속성 페이지를 클릭합니다.

1. **CLR 스레드 특성** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRThreadAttribute%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
