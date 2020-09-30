---
title: 액셀러레이터 키 (c + +)
ms.date: 02/14/2019
helpviewer_keywords:
- accelerator keys
- keyboard shortcuts
- keyboard shortcuts [C++], predefined
- menus [C++], shortcut keys
- keyboard shortcuts [C++], menu association
ms.assetid: f234c5f2-4ec3-4c9e-834a-b5dd297625b9
ms.openlocfilehash: 4f838caa8ca9e4a996fa4cb8018d663c6c7aecea
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504292"
---
# <a name="accelerator-keys-c"></a>액셀러레이터 키 (c + +)

## <a name="predefined-accelerator-keys"></a>사전 정의된 액셀러레이터 키

Windows 애플리케이션 프로젝트에 포함될 수 있는 미리 정의된 많은 액셀러레이터 키가 있습니다. 이러한 가상 키 중 일부는 Windows 환경을 위한 것입니다. 다른 사용자는 브라우저나 유니코드 응용 프로그램을 지원 합니다. 모든 액셀러레이터에 이러한 키 중 하나를 사용할 수 있습니다.

|키|설명|
|---------|-----------------|
|VK_ACCEPT|(IME) 수락|
|VK_BROWSER_BACK|Windows 브라우저, **뒤로** 키|
|VK_BROWSER_FAVORITES|Windows 브라우저, **즐겨찾기** 키|
|VK_BROWSER_FORWARD|Windows 브라우저, **전방** 키|
|VK_BROWSER_HOME|Windows 브라우저, **시작** 및 **홈** 키|
|VK_BROWSER_REFRESH|Windows 브라우저, 키 **새로 고침**|
|VK_BROWSER_SEARCH|Windows 브라우저, **검색** 키|
|VK_BROWSER_STOP|Windows 브라우저, 키 **중지**|
|VK_CONVERT|(IME) 변환|
|VK_FINAL|(IME) 최종 모드|
|VK_HANGUEL|E 한글 모드 (호환성을 위해 유지, VK_HANGUL 사용)|
|VK_HANGUL|E 한글 모드|
|VK_HANJA|E 한자 모드|
|VK_JUNJA|E Ime 모드|
|VK_KANA|E 가 나 모드|
|VK_KANJI|E 간지 모드|
|VK_LAUNCH_APP1|Windows **응용 프로그램 1 키 시작**|
|VK_LAUNCH_APP2|Windows **응용 프로그램 2 시작** 키|
|VK_LAUNCH_MAIL|Windows **메일 키 시작**|
|VK_LAUNCH_MEDIA_SELECT|Windows **미디어 키 선택**|
|VK_LCONTROL|**왼쪽 Ctrl** 키|
|VK_LMENU|**왼쪽 메뉴** 키|
|VK_LSHIFT|**왼쪽 Shift** 키|
|VK_MEDIA_NEXT_TRACK|Windows **다음 트랙** 키|
|VK_MEDIA_PLAY_PAUSE|Windows **미디어 키 재생/일시 중지**|
|VK_MEDIA_PREV_TRACK|Windows **이전 추적** 키|
|VK_MEDIA_STOP|Windows **미디어 키 중지**|
|VK_MODECHANGE|(IME) 모드 변경 요청|
|VK_NONCONVERT|(IME) ime|
|VK_OEM_1|Windows 미국 표준 키보드의 경우 **;:** 키|
|VK_OEM_102|Windows RT 102-키 키보드의 꺾쇠 괄호 키 또는 백슬래시 키|
|VK_OEM_2|Windows 미국 표준 키보드의 경우 **/?** key|
|VK_OEM_3|Windows 미국 표준 키보드의 경우 **`~** 키|
|VK_OEM_4|Windows 미국 표준 키보드의 경우 **[{** key|
|VK_OEM_5|Windows 미국 표준 키보드의 경우 ** \\&#124;** 키|
|VK_OEM_6|Windows 미국 표준 키보드의 경우 **]}** 키|
|VK_OEM_7|Windows 미국 표준 키보드의 경우 ' 작은따옴표/큰따옴표 ' 키|
|VK_OEM_COMMA|Windows 모든 국가/지역의 경우 **,** 키|
|VK_OEM_MINUS|Windows 모든 국가/지역에 대해 **-** 키|
|VK_OEM_PERIOD|Windows 모든 국가/지역의 경우 **입니다.** key|
|VK_OEM_PLUS|Windows 모든 국가/지역에 대해 **+** 키|
|VK_PACKET|Windows 입력 하는 것 처럼 유니코드 문자를 전달 하는 데 사용 됩니다.|
|VK_RCONTROL|**오른쪽 Ctrl** 키|
|VK_RMENU|**오른쪽 메뉴** 키|
|VK_RSHIFT|**오른쪽 시프트** 키|
|VK_SLEEP|**컴퓨터 절전 모드** 키|
|VK_VOLUME_DOWN|Windows **볼륨 작게** 키|
|VK_VOLUME_MUTE|Windows **볼륨 음소거** 키|
|VK_VOLUME_UP|Windows **볼륨 위로** 키|
|VK_XBUTTON1|Windows **X1** 마우스 단추|
|VK_XBUTTON2|Windows **X2** 마우스 단추|

## <a name="accelerator-key-association"></a>액셀러레이터 키 연결

메뉴 항목과 키보드 조합에서 동일한 프로그램 명령을 여러 번 실행하도록 하려고 합니다. 이 작업은 메뉴 항목에 동일한 리소스 식별자 (ID)를 할당 하 고, 응용 프로그램의 액셀러레이터 테이블에 있는 항목에 할당 하 여 수행 합니다. 그런 다음 메뉴 항목의 캡션을 편집하여 액셀러레이터 키의 이름을 표시합니다. 메뉴 항목 및 액셀러레이터 키에 대 한 자세한 내용은 [메뉴 명령](./menu-command-properties.md)을 참조 하세요.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[액셀러레이터 키 편집기](../windows/accelerator-editor.md)<br/>
