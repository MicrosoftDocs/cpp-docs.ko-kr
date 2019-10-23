---
title: 원본 복사 프로젝트 속성(Linux C++)
ms.date: 10/16/2019
ms.assetid: 1a44230d-5dd8-4d33-93b4-e77e03e00150
ms.openlocfilehash: ceaa1240f08b83ebc83bd7fdc25a3215467eb3f1
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444947"
---
# <a name="copy-sources-project-properties-linux-c"></a>원본 복사 프로젝트 속성(Linux C++)

::: moniker range="vs-2015"

Linux 지원은 Visual Studio 2017 이상에서 사용할 수 있습니다.

::: moniker-end

::: moniker range=">=vs-2017"

이 속성 페이지에 설정된 속성은 해당 프로젝트에서 파일-수준 속성이 설정된 파일을 제외한 모든 파일에 적용됩니다.

속성 | 설명
--- | ---
복사할 소스 | 원격 시스템에 복사할 소스를 지정합니다. 이 목록을 변경하면 파일이 복사되는 원격 시스템의 디렉터리 구조가 이동되거나 영향을 받을 수 있습니다.
소스 복사 | 원격 시스템에 소스를 복사할지 여부를 지정합니다.
복사할 추가 소스 | 원격 시스템에 복사할 추가 소스를 지정합니다. 필요에 따라 구문(예: fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2)을 사용하여 로컬-원격 매핑 쌍으로 목록을 제공할 수 있습니다. 이 경우 로컬 파일이 원격 시스템의 지정된 원격 위치에 복사될 수 있습니다.

@SourcesToCopyRemotely 및 @DataFilesToCopyRemotely는 프로젝트 파일의 항목 그룹을 참조합니다. 원격으로 복사되는 원본 또는 데이터 파일을 수정하려면 다음과 같이 *vcxproj* 파일을 편집합니다.

```xml
<ItemGroup>
   <MyItems Include=“foo.txt” />
   <MyItems Include=“bar.txt” />
   <DataFilesToCopyRemotely Include=”@(MyItems)” />
</ItemGroup>
```

::: moniker-end
