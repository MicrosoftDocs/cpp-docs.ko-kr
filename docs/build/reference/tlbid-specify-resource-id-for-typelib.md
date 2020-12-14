---
description: 자세히 알아보기:/TLBID (TypeLib의 리소스 ID 지정)
title: /TLBID(TypeLib의 리소스 ID 지정)
ms.date: 11/04/2016
f1_keywords:
- /tlbid
- VC.Project.VCLinkerTool.TypeLibraryResourceID
helpviewer_keywords:
- tlb files, specifying resource ID
- -TLBID linker option
- .tlb files, specifying resource ID
- /TLBID linker option
- TLBID linker option
- type libraries, specifying resource ID
ms.assetid: 434b28a2-4656-4d52-ac82-8b18bf486fb2
ms.openlocfilehash: 4958229cbebe988867c5419d7953b6ffd968e45f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230018"
---
# <a name="tlbid-specify-resource-id-for-typelib"></a>/TLBID(TypeLib의 리소스 ID 지정)

```
/TLBID:id
```

## <a name="arguments"></a>인수

*id*<br/>
링커가 만든 형식 라이브러리에 대 한 사용자 지정 값입니다. 기본 리소스 ID 1을 재정의 합니다.

## <a name="remarks"></a>설명

특성을 사용 하는 프로그램을 컴파일하는 경우 링커는 형식 라이브러리를 만듭니다. 링커는 리소스 ID 1을 형식 라이브러리에 할당 합니다.

이 리소스 ID가 기존 리소스 중 하 나와 충돌 하는 경우/TLBID.를 사용 하 여 다른 ID를 지정할 수 있습니다. 에 전달할 수 있는 값의 범위는 `id` 1 ~ 65535입니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **포함 된 IDL** 속성 페이지를 클릭 합니다.

1. **TypeLib 리소스 ID** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryResourceID%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
