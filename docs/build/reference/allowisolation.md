---
title: /ALLOWISOLATION
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION_EDITBIN
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
ms.openlocfilehash: 3dae8ee83e25492fab0ba2c6a55681728d5f3453
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440379"
---
# <a name="allowisolation"></a>/ALLOWISOLATION

매니페스트 조회 동작을 지정합니다.

## <a name="syntax"></a>구문

```

/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>설명

**/ALLOWISOLATION** 를 실행 하면 운영 체제에서 매니페스트 조회 및 로드가 발생 합니다.

**/ALLOWISOLATION** 가 기본값입니다.

**/ALLOWISOLATION: NO** 는 매니페스트가 없는 것 처럼 실행 파일이 로드 됨을 나타내고 [EDITBIN 참조가](editbin-reference.md) 선택적 헤더의 `DllCharacteristics` 필드에 `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` 비트를 설정 하도록 합니다.

실행 파일에 대해 격리가 비활성화되었으면 Windows 로더가 새로 생성되는 프로세스에 대해 애플리케이션 매니페스트를 찾으려고 시도하지 않습니다. 실행 파일 자체에 매니페스트가 있거나 이름이 *실행 파일 이름*. .exe .manifest 인 매니페스트가 있더라도 새 프로세스에는 기본 활성화 컨텍스트가 없습니다.

## <a name="see-also"></a>참고 항목

[EDITBIN 옵션](editbin-options.md)<br/>
[/ALLOWISOLATION(매니페스트 조회)](allowisolation-manifest-lookup.md)<br/>
[매니페스트 파일 참조](/windows/win32/SbsCs/manifest-files-reference)
