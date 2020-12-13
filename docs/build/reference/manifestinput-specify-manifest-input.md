---
description: 자세히 알아보기:/MANIFESTINPUT (매니페스트 입력 지정)
title: /MANIFESTINPUT(매니페스트 입력 지정)
ms.date: 07/24/2019
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: e4c5561779f41074a1c52593a62dd7d32ca32801
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137932"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT(매니페스트 입력 지정)

이미지에 포함 된 매니페스트에 포함할 매니페스트 입력 파일을 지정 합니다.

## <a name="syntax"></a>구문

```
/MANIFESTINPUT:filename
```

### <a name="parameters"></a>매개 변수

*filename*<br/>
포함 된 매니페스트에 포함할 매니페스트 파일입니다.

## <a name="remarks"></a>설명

**/MANIFESTINPUT** 옵션은 실행 가능한 이미지에 포함 된 매니페스트를 만드는 데 사용할 입력 파일의 경로를 지정 합니다. 매니페스트 입력 파일이 여러 개 있는 경우 각 입력 파일에 대해 한 번씩 스위치를 여러 번 사용 합니다. 매니페스트 입력 파일이 병합 되어 포함 된 매니페스트를 만듭니다. 이 옵션을 사용 하려면 **/Smanifest: EMBED** 옵션이 필요 합니다.

이 옵션은 Visual Studio에서 직접 설정할 수 없습니다. 대신 프로젝트의 **추가 매니페스트 파일** 속성을 사용 하 여 포함할 추가 매니페스트 파일을 지정 합니다. 자세한 내용은 [매니페스트 도구 속성 페이지](manifest-tool-property-pages.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
