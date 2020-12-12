---
description: 자세히 알아보기:/MERGE (섹션 결합)
title: /병합(섹션 결합)
ms.date: 11/04/2016
f1_keywords:
- /merge
- VC.Project.VCLinkerTool.MergeSections
helpviewer_keywords:
- sections, combining
- /MERGE linker option
- sections, naming
- sections
- -MERGE linker option
- MERGE linker option
ms.assetid: 10fb20c2-0b3f-4c8d-98a8-f69aedf03d52
ms.openlocfilehash: 579e5432facd6deb8d2b26b997d9b61f167d2b3e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199105"
---
# <a name="merge-combine-sections"></a>/병합(섹션 결합)

```
/MERGE:from=to
```

## <a name="remarks"></a>설명

/MERGE 옵션은 첫 번째 섹션 (*에서*)을 두 번째 섹션 *()으로* 결합 하 여 결과 섹션의 이름을 *로* 지정 합니다. 예: `/merge:.rdata=.text`.

두 번째 섹션이 없으면 LINK에서로 섹션의 이름을 *에서* *로* 바꿉니다.

/MERGE 옵션은 Vxd를 만들고 컴파일러 생성 섹션 이름을 재정의 하는 데 유용 합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **고급** 속성 페이지를 클릭 합니다.

1. **섹션 병합** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergeSections%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
