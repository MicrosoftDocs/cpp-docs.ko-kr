---
description: 자세히 알아보기:/SECTION (섹션 특성 지정)
title: /SECTION(섹션 특성 지정)
ms.date: 12/29/2017
f1_keywords:
- /section
helpviewer_keywords:
- SECTION linker option
- -SECTION linker option
- section attributes
- /SECTION linker option
ms.openlocfilehash: 8731f720e04ae2893f288e4b96aeaa019af43350
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224792"
---
# <a name="section-specify-section-attributes"></a>/SECTION(섹션 특성 지정)

> **/SECTION:**_name_, [[**!**] {**Dekprsw**}] [**, ALIGN =**_number_]

## <a name="remarks"></a>설명

**/SECTION** 옵션은 섹션의 .obj 파일을 컴파일할 때 설정한 특성을 재정의 하 여 섹션의 특성을 변경 합니다.

PE (이식 가능한 실행) 파일의 *섹션* 은 코드 또는 데이터를 포함 하는 명명 된 연속 메모리 블록입니다. 일부 섹션은 프로그램에서 직접 선언 하 고 사용 하는 코드 또는 데이터를 포함 하는 반면, 다른 데이터 섹션은 링커 및 라이브러리 관리자 (lib.exe)에 의해 생성 되 고 운영 체제에 중요 한 정보를 포함 합니다. 자세한 내용은 [PE 형식](/windows/win32/Debug/pe-format)을 참조 하세요.

콜론 (:)를 지정 합니다. 및 섹션 *이름* 입니다. *이름은* 대/소문자를 구분 합니다.

표준 이름과 충돌 하므로 다음 이름을 사용 하지 마십시오. 예를 들어. .sdata는 RISC 플랫폼에서 사용 됩니다.

- . 아치

- . bss

- . 데이터

- . edata

- . idata

- .pdata

- . .rdata

- . .reloc

- .srsrc

- . .sbss

- .sdata

- .slsa 데이터

- .text

- . .xdata

섹션에 대 한 특성을 하나 이상 지정 합니다. 아래에 나열 된 특성 문자는 대/소문자를 구분 하지 않습니다. 섹션에 포함할 모든 특성을 지정 해야 합니다. 생략 된 특성 문자로 인해 해당 특성 비트가 꺼집니다. R, W 또는 E를 지정 하지 않으면 기존 읽기, 쓰기 또는 실행 상태는 변경 되지 않은 상태로 유지 됩니다.

특성을 부정 하려면 해당 문자 앞에 느낌표 (!)를 사용 합니다. 이 표에는 특성 문자의 의미가 나와 있습니다.

|문자|attribute|의미|
|---------------|---------------|-------------|
|E|Execute|섹션이 실행 파일입니다.|
|R|읽기|데이터에 대 한 읽기 작업 허용|
|W|쓰기|데이터에 대 한 쓰기 작업 허용|
|S|공유|이미지를 로드 하는 모든 프로세스에서 섹션을 공유 합니다.|
|D|삭제 가능한|섹션을 삭제 가능한로 표시 합니다.|
|K|캐시 가능|섹션을 캐시할 수 없음으로 표시 합니다.|
|P|양|섹션을 페이징할 수 없는 것으로 표시 합니다.|

K와 P는 특이 한 의미에서 사용 되는 섹션 플래그를 사용 하는 경우를 의미 합니다. **/SECTION:. text, K** 옵션을 사용 하 여 텍스트 섹션에서이 중 하나를 지정 하는 경우 [/헤더](headers.md) 옵션을 사용 하 여 [DUMPBIN](dumpbin-options.md) 을 실행 하면 섹션 플래그에 차이가 없습니다. 섹션이 이미 암시적으로 캐시 되었습니다. 기본값을 제거 하려면 **/SECTION:. text,!를 지정 합니다. K** 를 대신 합니다. DUMPBIN은 "캐시 안 됨"을 포함 하 여 섹션 특징을 표시 합니다.

E, R 또는 W가 설정 되지 않은 PE 파일의 섹션은 유효 하지 않을 수 있습니다.

**ALIGN =**_number_ 인수를 사용 하면 특정 섹션에 대 한 맞춤 값을 지정할 수 있습니다. _Number_ 인수는 바이트 단위 이며 2의 거듭제곱 이어야 합니다. 자세한 내용은 [/align](align-section-alignment.md) 을 참조 하십시오.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **링커**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션** 상자에 옵션을 입력 합니다. **확인** 또는 **적용** 을 선택 하 여 변경 내용을 적용 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
