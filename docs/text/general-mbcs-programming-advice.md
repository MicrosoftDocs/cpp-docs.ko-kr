---
description: '자세한 정보: 일반 MBCS 프로그래밍 조언'
title: 일반적인 MBCS 프로그래밍 팁
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], dialog box fonts
- MS Shell Dlg
- MBCS [C++], programming
- dialog boxes [C++], fonts
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
ms.openlocfilehash: 9ed4fcd4909b643e2c233482a420e82d01125efa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187535"
---
# <a name="general-mbcs-programming-advice"></a>일반적인 MBCS 프로그래밍 팁

다음 팁을 사용 합니다.

- 유연성을 위해 가능한 경우 및와 같은 런타임 매크로를 사용 `_tcschr` `_tcscpy` 합니다. 자세한 내용은 [tchar.h의 제네릭 텍스트 매핑](../text/generic-text-mappings-in-tchar-h.md)을 참조 하세요.

- C 런타임 함수를 사용 `_getmbcp` 하 여 현재 코드 페이지에 대 한 정보를 가져옵니다.

- 문자열 리소스를 다시 사용 하지 마십시오. 대상 언어에 따라 지정 된 문자열이 번역 될 때 의미가 달라질 수 있습니다. 예를 들어 응용 프로그램의 주 메뉴에 있는 "파일"은 대화 상자의 "파일" 문자열과 다르게 변환 될 수 있습니다. 동일한 이름으로 둘 이상의 문자열을 사용 해야 하는 경우 각에 대해 서로 다른 문자열 Id를 사용 합니다.

- 응용 프로그램이 MBCS 사용 운영 체제에서 실행 되 고 있는지 여부를 확인 하는 것이 좋습니다. 이렇게 하려면 프로그램을 시작할 때 플래그를 설정 합니다. API 호출을 사용 하지 마십시오.

- 대화 상자를 디자인할 때 MBCS 번역을 위해 정적 텍스트 컨트롤의 끝에 약 30%의 추가 공간을 허용 합니다.

- 일부 글꼴은 일부 시스템에서 사용할 수 없기 때문에 응용 프로그램에 대 한 글꼴을 선택할 때 주의 해야 합니다.

- 대화 상자의 글꼴을 선택 하는 경우 MS Sans Serif 또는 Helvetica 대신 [Ms Shell Dlg](/windows/win32/Intl/using-ms-shell-dlg-and-ms-shell-dlg-2) 를 사용 합니다. MS Shell Dlg는 대화 상자를 만들기 전에 시스템에 의해 올바른 글꼴로 대체 됩니다. MS Shell Dlg를 사용 하면 운영 체제에서이 글꼴을 처리 하는 모든 변경 내용이 자동으로 제공 됩니다. (MFC는 ms shell dlg를 올바르게 처리 하지 않으므로 Windows 95, Windows 98 및 Windows NT 4에서 MS Shell Dlg를 DEFAULT_GUI_FONT 또는 시스템 글꼴로 바꿉니다.)

- 응용 프로그램을 디자인할 때 지역화할 수 있는 문자열을 결정 합니다. 확실 하지 않은 경우에는 지정 된 문자열이 지역화 될 것으로 가정 합니다. 따라서 지역화할 수 있는 문자열을 이외의 문자열로 혼합 하지 마십시오.

## <a name="see-also"></a>참고 항목

[MBCS 프로그래밍 팁](../text/mbcs-programming-tips.md)<br/>
[포인터 증가 및 감소](../text/incrementing-and-decrementing-pointers.md)
