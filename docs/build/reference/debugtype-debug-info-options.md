---
description: 자세히 알아보기:/DEBUGTYPE (디버그 정보 옵션)
title: /DEBUGTYPE(디버그 정보 옵션)
ms.date: 11/04/2016
f1_keywords:
- /debugtype
helpviewer_keywords:
- /DEBUGTYPE linker option
- DEBUGTYPE linker option
- -DEBUGTYPE linker option
ms.assetid: 1ddcb718-7fec-4f92-a319-3f70f04fe742
ms.openlocfilehash: 858d5ed8eb449931229700a10b755dd61ef371cc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201731"
---
# <a name="debugtype-debug-info-options"></a>/DEBUGTYPE(디버그 정보 옵션)

/DEBUGTYPE 옵션은 /DEBUG 옵션으로 생성된 디버깅 정보의 형식을 지정합니다.

```
/DEBUGTYPE:[CV | PDATA | FIXUP]
```

## <a name="arguments"></a>인수

**CV**<br/>
기호, 줄 번호 및 PDB 파일의 기타 개체 컴파일 정보에 대한 디버그 정보를 내보내도록 링커에 지시합니다. 기본적으로 **/debug** 를 지정 하 고 **/DEBUGTYPE** 를 지정 하지 않으면이 옵션을 사용할 수 있습니다.

**PDATA**<br/>
PDB 파일의 디버그 스트림 정보에 .pdata 및 .xdata 항목을 추가하도록 링커에 지시합니다. 기본적으로이 옵션은 **/debug** 및 **/DRIVER** 옵션을 모두 지정한 경우에 사용할 수 있습니다. **/DEBUGTYPE: .pdata** 를 단독으로 지정 하는 경우 링커는 PDB 파일에 디버깅 기호를 자동으로 포함 합니다. **/DEBUGTYPE: .pdata, 픽스업** 이 지정 된 경우 링커는 PDB 파일에 디버깅 기호를 포함 하지 않습니다.

**FIXUP**<br/>
PDB 파일의 디버그 스트림 정보에 재배치 테이블 항목을 추가하도록 링커에 지시합니다. 기본적으로이 옵션은 **/debug** 및 **/PROFILE** 옵션을 모두 지정한 경우에 사용할 수 있습니다. **/DEBUGTYPE: 픽스업** 또는 **/DEBUGTYPE: 픽스업** 이 지정 된 경우 링커는 PDB 파일에 디버깅 기호를 포함 하지 않습니다.

**/DEBUGTYPE** 에 대 한 인수를 쉼표로 구분 하 여 순서 대로 결합할 수 있습니다. **/DEBUGTYPE** 옵션과 해당 인수는 대/소문자를 구분 하지 않습니다.

## <a name="remarks"></a>설명

**/DEBUGTYPE** 옵션을 사용 하 여 디버깅 스트림에 재배치 테이블 데이터 또는 .pdata 및. .xdata 헤더 정보를 포함 하도록 지정 합니다. 그러면 링커는 커널 모드 코드를 중단할 때 커널 디버거에 표시되는 사용자 모드 코드에 대한 정보를 포함할 수 있습니다. **픽스업** 이 지정 될 때 디버깅 기호를 사용할 수 있도록 하려면 **CV** 인수를 포함 합니다.

응용 프로그램에 일반적으로 사용 되는 사용자 모드에서 코드를 디버깅 하려면 **/DEBUGTYPE** 옵션이 필요 하지 않습니다. 기본적으로 디버깅 출력 ([/Z7,/zi,/zi](z7-zi-zi-debug-information-format.md))을 지정 하는 컴파일러 스위치는 Visual Studio 디버거에 필요한 모든 정보를 내보냅니다. **/DEBUGTYPE: .pdata** 또는 **/DEBUGTYPE: CV, .pdata, 픽스업을** 사용 하 여 장치 드라이버용 구성 앱과 같은 사용자 모드 및 커널 모드 구성 요소를 결합 하는 코드를 디버깅 합니다. 커널 모드 디버거에 대 한 자세한 내용은 [Windows 용 디버깅 도구 (WinDbg, KD, CDB, NTSD)](/windows-hardware/drivers/debugger/index) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[/DEBUG (디버그 정보 생성)](debug-generate-debug-info.md)<br/>
[/DRIVER (Windows NT 커널 모드 드라이버)](driver-windows-nt-kernel-mode-driver.md)<br/>
[/PROFILE (성능 도구 프로파일러)](profile-performance-tools-profiler.md)<br/>
[Windows 용 디버깅 도구 (WinDbg, KD, CDB, NTSD)](/windows-hardware/drivers/debugger/index)
