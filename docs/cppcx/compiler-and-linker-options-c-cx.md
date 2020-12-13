---
description: '자세한 정보: 컴파일러 및 링커 옵션 (c + +/CX)'
title: 컴파일러 및 링커 옵션(C++/CX)
ms.date: 01/22/2017
ms.assetid: ecfadce8-3a3f-40cc-bb01-b4731f8d2fcb
ms.openlocfilehash: 66f3cf5a08d7ca0a07b5708495f76902c2286436
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340426"
---
# <a name="compiler-and-linker-options-ccx"></a>컴파일러 및 링커 옵션(C++/CX)

환경 변수, c + +/CX 컴파일러 옵션 및 링커 옵션은 Windows 런타임 앱 빌드를 지원 합니다.

## <a name="library-path"></a>라이브러리 경로

%LIBPATH% 환경 변수는 .winmd 파일을 검색할 기본 경로를 지정합니다.

## <a name="compiler-options"></a>컴파일러 옵션

|옵션|설명|
|------------|-----------------|
|[/ZW](../build/reference/zw-windows-runtime-compilation.md)<br /><br /> /ZW:nostdlib|Windows 런타임 언어 확장을 사용 하도록 설정 합니다.<br /><br /> `nostdlib` 매개 변수를 사용하면 컴파일러에서 미리 정의된 표준 검색 경로를 사용하여 어셈블리 및 .winmd 파일을 찾지 못합니다.<br /><br /> **/ZW** 컴파일러 옵션은 다음 컴파일러 옵션을 암시적으로 지정합니다.<br /><br />- **/FI** vccorlib.h - 컴파일러에 필요한 다양한 형식을 정의하는 vccorlib.h 헤더 파일을 강제로 포함합니다.<br />- [/Fu](../build/reference/fu-name-forced-hash-using-file.md) Windows winmd는 운영 체제에서 제공 하는 Windows winmd 메타 데이터 파일을 강제로 포함 하 고 Windows 런타임에서 다양 한 형식을 정의 합니다.<br />- **/FU** Platform.winmd - 네임스페이스의 Platform 패밀리에서 대부분 형식을 정의하고 컴파일러에서 제공되는 Platform.winmd 메타데이터 파일을 강제로 포함합니다.|
|[/AI](../build/reference/ai-specify-metadata-directories.md) *dir*|*dir* 매개 변수로 지정되는 디렉터리를 컴파일러에서 어셈블리 및 .winmd 파일을 찾는 데 사용하는 검색 경로에 추가합니다.|
|**/FU**  *파일*|지정된 모듈 또는 .winmd 파일을 강제로 포함합니다. 즉, 소스 코드에서 `#using`*file* 을 지정할 필요가 없습니다. 컴파일러에서는 고유한 Windows 메타데이터 파일, Platform.winmd를 자동으로 강제 포함합니다.|
|/D "WINAPI_FAMILY=2"|Windows 런타임과 호환 되는 Win32 SDK의 하위 집합을 사용할 수 있도록 하는 정의를 만듭니다.|

## <a name="linker-options"></a>링커 옵션

|옵션|설명|
|------------|-----------------|
|/APPCONTAINER[:NO]|실행 파일을 appcontainer에서(만) 실행 가능으로 표시합니다.|
|/WINS [: {NO&#124;ONLY}]|.winmd 파일 및 연결된 이진 파일을 내보냅니다. .winmd를 내보내려면 이 옵션을 링커에 전달해야 합니다.<br /><br /> **NO**—.winmd 파일을 내보내지 않지만 이진 파일을 내보냅니다.<br /><br /> **ONLY**—.winmd 파일을 내보내지만 이진 파일을 내보내지 않습니다.|
|/WINMDFILE:*filename*|기본 .winmd 파일 이름 대신 내보낼 .winmd 파일의 이름입니다. 명령줄에서 여러 파일 이름을 지정하면 마지막 이름이 사용됩니다.|
|/WINMDDELAYSIGN[:NO]|.winmd 파일에 부분적으로 서명하고 공개 키를 이진 파일에 삽입합니다.<br /><br /> **NO**—(기본값) .winmd 파일에 서명하지 않습니다.<br /><br /> /WINMDKEYFILE 또는 /WINMDKEYCONTAINER도 지정하지 않으면 /WINMDDELAYSIGN은 아무런 효과가 없습니다.|
|/WINMDKEYCONTAINER:*name*|어셈블리에 서명할 키 컨테이너를 지정합니다. *name* 매개 변수는 메타데이터 파일에 서명하는 데 사용되는 키 컨테이너에 해당합니다.|
|/WINMDKEYFILE:*filename*|어셈블리에 서명할 키 또는 키 쌍을 지정합니다. *filename* 매개 변수는 메타데이터 파일에 서명하는 데 사용되는 키에 해당합니다.|

### <a name="remarks"></a>설명

**/ZW** 를 사용하면 컴파일러는 CRT(C 런타임)의 DLL 버전에 자동으로 연결됩니다. 정적 라이브러리 버전에 연결 하는 것은 허용 되지 않으며 유니버설 Windows 플랫폼 앱에서 허용 되지 않는 CRT 함수를 사용 하면 컴파일 시간 오류가 발생 합니다.

## <a name="see-also"></a>참고 항목

[앱 및 라이브러리 빌드](../cppcx/building-apps-and-libraries-c-cx.md)
